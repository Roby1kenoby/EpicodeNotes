Libreria che ci permette di fare autenticazione con tanti provider diversi

Installo con npm i passport, e poi le "strategie" che mi servono (es, quella di google)

npm i passport passport-google-oauth20

Ci serve aver dei router specifici per gestire la richiesta di autorizzazione ed il redirect

Passport va configurato con i dati del provider (es: [[google cloud console]]).
Creare una cartella config, in cui vado a inserire tutti i miei file di configurazione

Creo un file passport.config.js
``` javascript
// recuper la libreria
import GoogleStrategy from 'passport-google-oauth20'
// istanzio la strategy
const googleStrategy = new 
//oggetto con le configurazioni
GoogleStrategy({
	clientID: process.env.GOOGLE_CLIENT_ID,
	clientSecret: process.env.GOOGLE_CLIENT_SECRET,
	callbackURL: `${process.env.HOST}:${process.env.PORT}/${process.env.GOOGLE_CALLBACK}`
},
// funzione che viene chiamata quando google ci risponde. (cb sta per callback, ed è tipo il next del router, ma di passport)
	async function  (accessToken, refreshToken, profile, cb){
	// qui andiamo nel db e cerchiamo di capire se c'è già l'utente o dobbiamo crearlo. In genere, i dati che restituisce google sono strutturati così:
	/*profile: {
		_json: {
			given_name: "Pinco",
			family_name: "Pallino",
			email: "pinco@pallin.it",
			sub: "1231efd09iaf" // id di google
		}
	}
	*/
	// spread operator, smonto l'oggetto e con i duepunti rinomino le variabili 
	const {given_name: name, family_name: surname, email, sub: googleId} = profile._json

	// cerco l'utente tramite il google id. Se non c'è lo creo altrim lo loggo.
	// uso LET perchè voglio riusare la variabili user per la creazione del jwt, sia che mi debba registrare sia che sia già registrato
	let user = await User.findOne({googleId: googleId})

	if(!user){
		// creo l'utente
		const newUser = new User({
			googleId, name, surname, email	
		})
		// salvo l'utente
		user = await newUser.save()
	}
	// creiamo il jwt per l'utente (NON con l'id google, ma quello del nostro db)
	jwt.sign({
	userId: user.id
	},
	process.env.JWT_SECRET,{expiresIn: '1h'}, 
	(err, jwtToken) => {
		if(err) return res.status(500).send('error')
		// la callback di passport sa che se gli passi qualcosa è un token, e lo mette in automatico in req.user.token. Il primo parametro (null) è l'eventuale errore
		
		// poi chiamiamo il prossimo middleware (quello che fa il redirect) alla mia rotta post autenticazione

		return cb(null, {jwtToken})
	})
	}
)

export default googleStrategy
```
Ovviamente i client secret ecc vanno nel file env
```env
GOOGLE_CLIENT_ID=alksjdhkljsad
GOOGLE_CLIENT_SECRET=hboiajsfdoajs
GOOGLE_CALLBACK=http:/api/v1/callback-google
```

una volta configurata la strategia, vado sul server e la uso

Server.js
```javascript
import passport from 'passport'
import googleStrategy from 'path'
// questo use non è use di un middleware, ma è di passport e gli dico che strategia usare (il nome è libero)
passport.use('google', googleStrategy)
// metterlo prima del router

```

auth router
``` javascript
import passport from 'passport'
//rotte per richiedere a google l'autenticazione.
// quando l'utente arriva sulla rotta, il router richiama il metodo auth di passport, che ha come scope i dati registrati in google cloud console. Dopo di che c'è il redirect sull'auth di google
authRouter.get('/login-google', passport.authenticate('google',{
	scope: ['profile','email']
}))

//rotta che ci chiama google passandoci i dati dell'utente autenticato
// stesso metodo di passport, ma con info diverse. Gli dico che non voglio usare le sessioni
authRouter.get('/callback-google', passport.authenticate('google',{
	session:false
}), callbackGoogle)

```

controller
```Javascript

export const callbackGoogle = (req,res) => {
	// qui faremo il redirect al frontend. Passport ci crea nella richiesta un oggetto user, che contiene il token, che devo passare in chiaro perchè devo fare un redirect e posso farlo solo con una get
	const token = req.user
	res.redirect(`urlPostLogin?token=${token}`)
}

```

Per il frontend, nel contesto, verifico se c'è un token nei searchParams e poi agisco di conseguenza
```Javascript

useffect(() => {
	// recupero i dati dall'url
	const objUrlParams =	new URLSearchParams(windows.location.search)
	// recupero il token
	const token = objUrlParams.get('token')
	if(token){
		localStorage.setItem('token', token)
		//aggiungo l'utente nel context
		// redirect verso un'altra pagina
		navigate('/home')
	}
	// altrimenti proseguo con la renderizzazione della pagina, mostrando il login ecc.
	
}, [])
```