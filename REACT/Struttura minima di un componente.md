È buona prassi nominare come .jsx i file in cui scriverò in JSX.

È necessario ricordarsi di effettuare l'export della funzione affinché sia utilizzabile altrove
```javascript
function App() {
	// normalmente, cercherò di fare il più possibile con js prima del return le logiche, e nel return ci butto solo le parti html con un po' di jsx per riportare le variabili calcolate nel js
  return (
	  // parte html del componente con eventuali finestre {} sul js
  );
}
// default serve a indicare qual è l'export di default del componente.
// normalmente nei componenti c'è sempre un solo export, altre cose potrebbero averne più di uno
export default App;

// posso anche fare l'export così:

export default function app(){
	// cose
}

// posso anche definire il componenente così:
const counter = () => {
	// cose
}
```

È fondamentale che il nome del componente (della funzione) abbia iniziale Maiuscola, affinché sia richiamabile dall'applicazione principale.

Consiglio, se deve restituire più cose (un h1 e un pulsante, per es) è sempre meglio inserirle all'interno di un div (se necessario dello stile) o in un fragment (che è un tag vuoto che non viene neanche presentato nell'inspector quando esamino i componenti).

```
// esempio di fragment
<></>
```