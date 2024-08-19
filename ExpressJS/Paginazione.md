Sono disponibili un po' di metodi del mongoDB che vengono esposti tramite mongoose.

- Sort permette di ordinare i risultati restituiti. 
	Gli passo le categorie e gli dico con che ordinamento: sort({title:1, category:-1})
	- 1 è crescente, -1 decrescente
- Skip - salta un tot di valori. skip(50)
- Limit - restituisci un massimo di x valori. limit(25)

```javascript
// endpoint che fa la get
// in genere conviene dare dei default per far si che non si spacchi l'app se manca quel param
const page = req.query.page || 1

const perPage = req.query.perPage || 5

const users = await User.find({})
// ordino
users.sort({name:1, age:-1})
// page è la pagina a cui sono.
// perPage è il numero di elementi che voglio visualizzare per pagina.
users.skip((page-1)*perPage)
users.limit(perPage)

const totalResults = await User.countDocuments()

const totalPages = Math.ceil(totalResults / perPage)

// in genere, conviene restituire un oggetto più composto rispetto al solo risultato della query sul db
res.send({
	data: users,
	// posso non mettere la chiave, e il risultato è che l'oggetto avrà una proprietà con quel nome e quel valore
	totalPages,
	totalResults,
	page
})
```

