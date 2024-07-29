Se non ho idea di che parametri ci siano nell'url, posso fare così:

```javascript
response.send(request.query)
```

l'url può essere strutturato così:
https://localhost.5000/?name=pinco&age=30

il risultato tirato fuori da request.query è un oggetto json strutturato così:

{
	"name": "pinco",
	"age": 30
}

Usare questo tipo di estrazione dei dati dalla query string serve perché spesso lato client ho possibilità di far fare solo una get (per es un link è una get) ma voglio cmq poter permettere di passare parametri, e quindi lo posso fare nel query string.

Poiché nell'url ci possono essere valori di qualsiasi tipo, starà a me lato server fare dei controlli con quello che ho ricevuto.