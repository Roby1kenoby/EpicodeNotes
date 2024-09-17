Come prima cosa:
npm i nodemailer

Nodemailer è una libreria di interfacciamento per node, verso qualsiasi servizio di invio mail hostato.

Abbiamo poi bisogno di configurare l'env con le info del servizio che voglio usare (host, port, user e password).

Conviene creare nel progetto una cartella services, dove inserisco poi i file che vengono usati dal resto dell'applicazione (es: mail.service.js)

```Javascript
import nodemailer from 'nodemailer'

// funzione di configurazione del mailer
const transport = nodemailer.createTransport({
	host: process.env.EMAIL_HOST,
	port: process.env.EMAIL_PORT,
	auth: {
		user: process.env.EMAIL_USER,
		pass: process.env.EMAIL_PASSWORD,
	}
})
// esporto la funzione che invierà l'email
export default transport
```

A questo punto, posso effettuare l'invio di una mail da qualsiasi punto della mia app

``` Javascript
// file router
router.post('send-mail', recipeController.sendMailMiddleware())
```


``` Javascript
// file controller
import transport from '../services/nomeFileConIlServizio'

export const sendMailMiddleware = async (req, res) => {


	// sendMail è la funzione per effettuare l'invio tramite il transport, che è l'oggetto per interfacciarsi col server di invio posta
	await transport.sendMail({
		from: "mittente",
		to: "destinatarii",
		// se voglio, posso recuperare dati per l'email dal body della richiesta
		to: req.body.email,
		subject: "oggetto",
		text: "contenuto in plain text, se non c'è il supporto html del lettore",
		html: "testo in html"
	})
	// il transport accetta anche una funzione di callback per la gestione degli errori. Nel caso in cui la usi, l'await non serve più.
	//,(err) => {console.log(err)}
}
```

