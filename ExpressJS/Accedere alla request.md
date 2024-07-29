Per recuperare dati dal queryString
```Javascript

server.get('/users/:id', (req, res) => {
	const id = request.params.id
	resp.send("Qui andranno i dati del post con id: ${id}")
	// modalità con destrutturazione
	const {id} = params.resp
}
```
Per recuperare dati dal body della richiesta

```Javascript

server.get('/users', (req, res) => {
	// così accedo al body
	resp.send(request.body)
}
```

Per  testare le api direttamente da vcode, scaircare rest client