In genere conviene creare una cartella nel progetto per gli schema, denominata model.
Dentro ci metto i file Nomeschema.js, raggruppandoli per argomento (utenti, post, ecc)

```Javascript
import {Schema, model} from "mongoose"

// inizializzo lo schema tramite due oggetti. 
const userSchema = new Schema(
//Nel primo oggetto definisco i campi ed i vincoli dell'oggetto.
{
	googleId: String,
	name: {
		type: String,
		},
	email: {
		type: String,
		// campo univoco
		unique: true,
		// campo obbligatorio
		required: true,
		// porto a lowercase, comodo per i confronti in un secondo momento
		lowercase: true,
		// elimino eventuali spazi
		trim: true
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
	password: {
		type: String,
		required: true
	},
	// se devo referenziare un altro oggetto nel db, posso usare il suo id così.
	// se me ne serve un array, basta racchiudere tutto tra quadre
	referenceToOtherId:[{
		type:Schema.Types.ObjectId,
		// questo è il nome dello schema di cui l'id finirà qua dentro. (sotto il nome dello schema è User)
		ref: "Post"
	}],
	approved: Boolean,
	// potenzialmente utile per la verifica della mail
	verifiedAt: Date,
	// codice nell'email di verifica (o nell'url)
	verificationCode: String,
	// per far scadere eventualmente la richiesta di verifica
	createdAt: Date
},
	// nel secondo oggetto metto la collection, che per convenzione si mette al plurale
	{
	collection: 'users',
	// ci sono poi una serie di parametri che posso mettere (tipo la creazione o meno dell'id, l'applicazione dei timestamp ecc)
	timestamp: true
})
// Creo un model per poter aggiungere nuove istanzedi questo schema. Per convenzione si mette l'iniziale maiuscola ed al singolare
const User = model('User', userSchema)

// esporto il model che voglio usare nel resto del server
export default User
```

*una proprietà dell'oggetto può anche fare riferimento ad un altro schema*
``` Javascript
import authorSchema from 'path'

const post = new Schema({
	author: {
		type: authorSchema
	},
	title: String
})
```
==ATTENZIONE: authorSchema non deve però essere una collection, ma solo uno schema! Altrimenti va in errore il server. ==

Nel file router poi posso richiamare questo modello quando mi serve per archiviare cose.

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

