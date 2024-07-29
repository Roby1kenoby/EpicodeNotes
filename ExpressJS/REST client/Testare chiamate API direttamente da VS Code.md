Fare una cartella requests, e dentro fare file del tipo users.http in cui vado ad inserire le singole richieste.

Dentro scrivo:
i tre hash servono per separare una richiesta dall'altra.

Se devo usare json devo impostare il content-type. Se ho bisogno di altra roba nell'header, la metto dopo l'url.
Quando ho finito con la roba dell'header, spazio per indicare che da lì inizia il body.


```
@baseUrl=http://localhost:5000

GET {{baseUrl}}

###
GET {{baseUrl}}/users/10

###
POST {{baseUrl}}/users
Content-Type: application/json

{
	"name": "pippo",
	"age": 15
}
```

Per avviare le richieste, nel file sopra ad ogni richiesta ci sarà Send Request. Se lo clicco viene eseguita la richiesta e nel terminal vedo la risposta.



