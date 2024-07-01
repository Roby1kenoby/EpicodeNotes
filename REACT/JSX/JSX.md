Sintassi specifica di React per estendere Javascript (Javascript XML).
In pratica andremo a creare dei componenti (che sono tag creati da noi) che poi verranno visualizzati nel DOM.

==IMPORTANTE==
Se chiamo tag con la minuscola, sono tag nativi HTML.
Se li metto con la maiuscola, invece sono tag che creo io. Devo pertanto mettere l'iniziale maiuscola se voglio che funzionino.

Inoltre, è sempre fondamentale chiudere i tag aperti 

```javascript
const Example = function(){
	return (
		// questo è html diretto, non una stringa!
		<h1>Hello World!</h1>
	)
}
```

Nel DOM, richiamo il mio tag così
```HTML
<Example />
```

Il jsx è praticamente HTML in cui posso richiamare javascript, aprendo graffe nell'html
Nelle graffe posso scrivere js.

```jsx
const myApp = function(){
	const mioValore = 'pippo'
	return {
		<h1>{mioValore}</h1>
	}
}
export default myApp

```

Attenzione, nel JSX (all'interno del return) posso mettere soltanto expressions (sintassi che restituiscono qualcosa, tipo map), non statements (sintassi che non restituiscono, tipo if, forEach ecc).

