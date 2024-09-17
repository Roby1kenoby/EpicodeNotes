Sono funzioni che "stanno in mezzo", hanno di solito una forma del tipo {req, res, next} => {}
Next è una funzione di callback.

I Middleware possono fare tante cose. Gestire le autenticazioni, gestire le rotte, validare dati ecc.

Posso definire i middelware a livello globale, o a livello di file specifico del singolo file in base alle esigenze.

Per utilizzare un middleware, devo utilizzare il termine "use"

```Javascript
// router 
app.use("/recipes", router)

// middleware mio
app.use((req,res, next) => {
	console.log("addio")
})
```

**Se il primo middleware risponde, tutto quello che segue (a livello di altri middleware) non viene più eseguito (viene interrotta la catena).**

Nell'esempio sopra, verrà chiamato il recipes, e il middleware con  console.log("addio") non verrà mai richiamato.

Se all'interno di un middleware chiamo la funzione "next", gli sto dicendo di andare avanti al successivo.

**Attenzione: sempre o andare a next, o rispondere in un middleware, altrimenti la richiesta rimane piantata**

Esempio di middleware di validazione.
```Javascript
app.use((req,res,next) => {
	if(req.headers.authorization == "Bearer token_vlaido") {
	// magari recupero i dati dell'utente e li aggiungo alla richiesta
	req.authUser
	// faccio proseguire la sequenza di middleware
	next();
	}
else{
	// altrimenti, interrompo la catena e restituisco errore.
	return res.status(401).send()
}
})
```

In genere conviene farsi una cartella middleware, e poi metterci dentro tutti i file dei middleware specifici.
Quindi, nel file in cui mi serve la richiamo semplicemente così:

```Javascript
// file a parte con la funzione di middleware
export default (req,res,next) => {
	// controlli sull'autenticazione, se ok next, altrimenti send della response con l'errore
}
```

```Javascript
import authentication from 'path'
app.use(authentication)
```

Se voglio aggiungere solo ad una specifica rotta un middleware:

```Javascript
router.get('/', 
		   // qui sto registrando il middelware. Se è tutto ok, allora passa next e esegue la funzione, altrimenti invia l'errore
		   authentication, (req,res) => {
	// attività vere e proprie definite dal router
})
```

Posso anche avere un middleware con 4 parametri: err, req, res, next.

Per richiamare un middleware di errore, devo fare next(err).

In genere si mettono alla fine dell'elenco di middleware

```Javascript
// file middleware errorHandler. Devo per forza scrivere next, anche se non lo uso, se no il costruttore non sa che è un middleware di gestione errori


export default (err, req, res, next) => {
	console.log('errore')
	return res.status(500).send('errore')
}
```

```Javascript
import errorHandler from 'path'

app.use('/', router);

app.use((req,res,next) => {
	//altro middleware
	// se passo un argomento al next, capisce che è un middleware di gestione errore, e va al primo middleware di gestione errori che segue
	next('errore')
	
})

app.use((req,res,next) => {
	// altro middleware che viene skippato in caso di errore.
})

app.use(errorHandler)

```

In genere, i middleware che gestiscono gli errori sono globali e vengono registrati sul file server.js, e vengono messi al fondo, dopo gli altri middleware.

Un middleware errorHandler può anche rimandare tramite next senza argomenti ad un middleware standard, o a un secondo errorHandler se next ha un argomento.

Un middleware errorHandler (posizionato dopo un mw normale) viene skippato se quello normale fa un next senza parametri (e dopo al mw errorHandler c'è un mw normale)