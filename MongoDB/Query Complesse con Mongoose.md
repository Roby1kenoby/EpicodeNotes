==ATTENZIONE==
Le query con mongoose sul db sono particolari.
L'await è un po' come dirgli "ok, esegui la query sul db".
Spesso è sufficiente, usare direttamente l'await, ma quando ho query complesse devo fare come segue:

```Javascript
// da qui sto iniziando a costruire una query che al suo interno ha una promise.
// se ci metto subito await davanti, lui esegue la query, quindi i passaggi successivi dedicati alla paginazione non funzioneranno perchè il risultato della query è un Array, e il primo step successivo è il sort, che però viene interpretato come sort di Javascript (si aspetta di avere nei parametri una funzione di comparazione, non un oggetto), e non come sort di mongoose (che avviene sul DB, e che come parametri ha i campi sui quali fare l'ordinamento)
	const authorsListQuery = Author.find({})
		// qui sto ancora editando la query che farò sul DB, facendo un sort
        authorsListQuery.sort({surname:1, name:1})
        // qui continuo l'edit della query per la paginazione ecc.
        authorsListQuery.skip((page-1)*authorsPerPage)
        authorsListQuery.limit(authorsPerPage)
// a questo punto, grazie all'await effettuo la query complessiva, e mi restituisce l'array con i risultati.
	const authorsList = await authorsListQuery

// metodo alternativo per effettuare query su una sola "riga", l'await all'inizio la fa partire subito, ed i punti concatenano le sucessive parti della query
const authorsList = await Author.find()
	.sort({surname:1, name:1})
    .skip((page-1)*authorsPerPage)
    .limit(authorsPerPage)
// essendo su una sola riga, non posso fare cose tipo if o altre cose simili
```