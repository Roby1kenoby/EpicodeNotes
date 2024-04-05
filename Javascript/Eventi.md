Un evento restituisce sempre un oggetto che da più informazioni
https://www.w3schools.com/jsref/dom_obj_event.asp

Se un elemento è già esistente nell'html, gli eventi sono i vari onClick, onHover ecc.
Se invece un elemento è creato tramite javascript, per assegnare degli event devo fare così:
``
```javascript
	// non devi mettere le parentesi dopo il nome funzione
	element.onClick = functionName
	element.addEventListener("click", functionName)
	// se metto dei parametri alla funzione, non funziona più l'evento (vengono presi subito e applicati)
```

Se ho bisogno di passare dei parametri alla funzione, devo usare una arrow function
```JavaScript
element.addEventListener("click", () => {functionName("ValorePar1", "ValorePar2")})

functionName = function(par1, par2){
	// funzione
}

```