Per recuperare dati dal queryString
```Javascript

server.get('/users/:id', (request, resp) => {
	const id = request.params.id
	resp.send("Qui andranno i dati del post con id: ${id}")
	// modalità con destrutturazione
	const {id} = params.resp
}
```
Per recuperare dati dal body della richiesta

```Javascript

server.get('/users', (request, resp) => {
// così accedo al body
const userData = request.body
	resp.send(userData)
}
```

Per  testare le api direttamente da vcode, scaircare rest client