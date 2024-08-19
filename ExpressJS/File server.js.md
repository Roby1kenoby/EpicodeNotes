```Javascript
import express from "express"

const server = express()
// questa stringa mi serve per poter gestire json quando arrivano
server.use(express.json())
// in genere meglio prendere la porta dal file env, e mettere un default process.env.PORT || portaDefault
const port = 3001

server.listen(port, () => {
	console.log("Server is running on port: ", port)
})
```

Per avviare il server, nel terminale, scrivo node e poi il nome del file di ingresso (se non abbiamo l'utility di watch [[Watch del server con nodemon |nodemon]])

```terminal
node server.js
```

Nel caso facessi modifiche ai file, devo riavviare il server ogni volta affinché vengano caricate

A questo punto posso creare le singole rotte (che si occuperanno poi di rispondere alle chiamate)

```Javascript
// esempio di rotta:
// esempio di indirizzo che risponde a un get
server.get('/', (req, res) => {
	// tra le parentesi tonde del send metto il body della risposta.
	res.send('ciao a tutti')
	res.send({"saluto": "ciao a tutti"})
})
```

Il primo argomento è una stringa con la parte dell'indirizzo a cui voglio far rispondere.
Il secondo è una callback che fa cose.
Gli argomenti della callback son sempre due (tre, ma in genere due). Il primo è la richiesta, il secondo la response.

Il request contiene l'eventuale body o gli eventuali parametri presenti nel query string, oltre agli header e tutto quello che concerne la richiesta.

La response è l'oggetto che verrà restituito, io lo preparo e poi faccio il send della response.

==Attenzione: send, di default manda uno status code 200 (response ok)==

Se voglio inviare uno status diverso:

```Javascript
response.status(404).send(cose)
// posso anche solo inviare lo status così.

response.sendStatus(300)
// questo crea un piccolo body
// oppure
resposne.status(404).send()
// questo non da un body
```

