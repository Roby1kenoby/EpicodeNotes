In genere conviene creare una cartella nel progetto per gli schema, denominata model.
Dentro ci metto i file Nomeschema.js, raggruppandoli per argomento (utenti, post, ecc)

```Javascript
import {Schema, model} from "mongoose"

// inizializzo lo schema tramite due oggetti. 
const userSchema = new Schema(
//Nel primo oggetto definisco i campi ed i vincoli dell'oggetto.
{
	name: {
		type: String,
		},
	email: {
		type: String,
		// campo univoco
		unique: true,
		// campo obbligatorio
		required: true
	},
	age: {
		type:Number,
		min: 0,
		max: 100
		}
	role: {
	type:String,
	// forzo appartenenza ad un certo tipo di valore
	enum['User','Admin'],
	default:'User'
	},
	approved: Boolean
},
	// nel secondo oggetto metto la collection, che per convenzione si mette al plurale
	{
	collection: 'users'
})
// Creo un model per poter aggiungere nuove istanzedi questo schema. Per convenzione si mette l'iniziale maiuscola ed al singolare
const User = model('User', userSchema)

// esporto il model che voglio usare nel resto del server
export default User
```

Nel file router poi posso richiamare questo modello quando mi sserve per archiviare cose.

```Javascript
// qui posso sempre decidere che nome dare all'importazione, perchè tanto l'export è di default
import User from 'pathPerLoSchema'

// devo dichiarare la funzione di callback come async perchè la chiamata al db è asincrona
userRouter.get('/', async (req,res) => {
	// uso await per attendere che il db mi restituisca cose
	const users = await User.find({})
	res.send(users)
})

userRouter.post('/', async (req,res) => {
	// recupero dal body l'oggetto che dovrebbe contenere i dati strutturati come da schema
	const userData = req.body
	// faccio un try catch per gestire le casistiche
	try{
		// istanzio il nuovo oggetto con lo schema User e gli passo i dati ricevuti
		const newUser = new User(userData)
		// tento il save
		const createdUser = await newUser.save()
		// se tutto ok, 201 (created)
		res.status(201).send(createdUser)
	}
	catch(err){
		// questo log l'utente non lo vede, lo leggo solo io nel backend
		console.log(error)
		res.status(400).send(error)
	}
})
```