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

un evento può anche essere onscroll (per intercettare lo scroll della pagina)

se poi voglio sapere che distanza è stata percorsa in scroll, posso usare 
document.documentElement.scrolltop (dall'alto, ma ci sono anche left, bottom, to ecc).

Un evento importante è l'onload
```javascript
window.onload = function(){
	// questa roba verrà eseguita al caricamento della finestra
}
```

Eventi interessanti:
* DOMContentLoaded (fine del caricamento del DOM)