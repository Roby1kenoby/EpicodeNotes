Per gestire le autorizzazioni tramite token, mi creo un middleware apposito
```Javascript
import jwt from 'jsonwebtoken'
	export default (req,res,next) => {
		// verificare se c'è l'header Authorization e se è di tipo bearer
		if(!req.headers.authorization) return res.status(401).send('not authorized')
		// splitto la dicitura berarer token e controllo che sia strutturato correttamente
		const parts = req.headers.authorization.split(' ')
		if ((parts.length) != 2) return res.status(401).send('not authorized')
		if (parts[0] != 'Bearer') return res.status(401).send('not authorized')
	// se ho passato i controlli, allora a posto
	const jwtToken = parts[1]
	// verify controlla anche la durata del token
	jwt.verify(jwtToken, process.env.JWT_SECRET, async (err, payload) => {
		if(err) return res.status(401).send('not authorized')
		// se invece ok, recupero dal db i dati dell'utente loggato
		const user = await User.findById(payload.userId)
		if(!user) return res.status(401).send('not authorized')
		
		// aggiungo una chiave all'oggetto req le informazioni dell'utente loggato appena recuperate
		req.user = user;
		// faccio passare il middleware alla prossima operazione
		next()
	})
	
		// verificare la firma del token
	}
 
```

Questo middleware posso usarlo per proteggere le rotte che mi servono.

```Javascript
import authorization from '/path del middleware.js'
// se metto in cima questo, tutti gli altri router successivi saranno automaticamente interessati dal middleware.

// route non protetta 
router.get(/*rotta non protetta*/)
rotuer.use(authorization)
router.get(/*rotta protetta*/)

// in alternativa posso registrarlo dentro alle singole rotte che mi servono
rotuer.get('/percorso', authorization, funzioneDaEseguire)
```