Sono i parametri passati nell'url, per passare da una pagina all'altra delle informazioni (in genere per passare da una pagina di origine ad una di dettaglio)

```javascript
// per passare parametri, l'url deve essere composto così:
'https:\\blablabla.html?nomePar1=valorePar1&nomePar2=valorePar2'

// questo mi permette di tirare fuori tutto quello che c'è dopo il punto interrogativo (i parametri)
const params = new URLSearchParams(window.location.search)
// così per recuperare il singolo parametro
let primoPar = params.get("nomePar1")
```
