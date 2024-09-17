In genere, il logout si fa sempre con la POST, in modo che non sia possibile creare un link malevolo (GET) che ti effettua il logout non intenzionalmente.

devo installare via node bcrypt

npm i bcrypt

Router
```Javascript
import express from 'express'
import * as authController from 'path'
const authRouter = express.router()

authRouter.post('/register', authController.registerNewUser)
authRouter.post('/login', authController.loginUser)
authRouter.post('/logout', authController.logoutUser)
authRouter.get('/me', authController.getUserData)

export default authRouter
```

Controller
```Javascript
// ho lo schema che ha email e password
import User from "path/usersSchema.js"
import bcrypt from 'bcrypt'
import jwt from 'jsonwebtoken'

export const registerNewUser = async (req,res) => {
	// vedo se esiste già l'utente
	const user = await User.findOne({email: req.body.email})
if (user) return res.status(500).send('Mail già in uso')

// per essere più "sicuri", conviene inserire i dati manualmente e non direttamente l'oggetto (mongo accetta anche elementi in più di quelli presenti nella struttura)
const newUser = new User({
	name: req.body.name,
	email: req.body.email,
	// c'è anche un metodo sincrono, ma meglio di solito async. Il nr di giri di hash di default è 10, potrei non metterlo
	password: await bcrypt.hash(req.body.password, 10),
	createdAt: new Date
})

// in alternativa per la creazione senza fare un elemento per l'altro, posso fare 
/*const newUser = new User({...req.body, password: await bcrypt.hash(req.body.password, 10)})*/
	const createdUser = await newUser.save()
	res.send(createdUser)
}

export const login() = async (req,res) => {
	const user = await User.findOne({email: req.body.email})

	// se non c'è l'utente, errore
	if (!user) return res.status(401).send("not authorized")
	// se non è verificata la pass
	if(!(await bcrypt.compare(req.body.password, user.password)){
		return res.status(401).send('credenziali errate')
	}
	
	// se la password è corretta, allora genero il token. La prima parte è il payload, la seconda il secret
	jwt.sign({userId: user.id}, process.env.JWT_SECRET, {
		// questo è l'oggetto delle opzioni, vedi documentazione ufficiale per vedere quali ci sono
		expiresIn: '1h'
	}, 
	// quando l'operazione di firma finisce, viene chiamata la callback (non posso usare await)
	(err, jwtToken) => {
		if(err) return res.status(500).send("server error")
		res.send({
			token: jwtToken
		})
	})
})

// il logout con i jwt non si fa lato server, ma lato frontend, pulendo il local storage.

```

file env
```env
JWT_SECRET=secret_key
```