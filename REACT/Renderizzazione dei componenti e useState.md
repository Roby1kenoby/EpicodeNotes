Per poter aggiornare visivamente i componenti che variano nel tempo, devo utilizzare stato e hook.

Lo stato è l'insieme delle variabili che, se  modificate, causano la nuova renderizzazione del componente.

Triggerare questa cosa, devo dichiarare le mie variabili tramite useState, che è l'hook.

```jsx
function Counter(){
	const [counter, setCounter] = useState(0)

	const increment = () => {
		// non posso utilizzare counter++ perchè andrei a modificare il valore della variabile direttamente, che però è un const, quindi andrebbe in errore.
		setCounter(counter + 1);
	};

	return (
		<>
			<div>{counter}</div>
			
		</>
	)

}
```

useState è una funzione di sistema che restituisce sempre un array che contiene
- il valore della variabile
- una funzione per cambiare il valore (un setter).
==useState gestisce una sola variabile di stato, non è possibile associarne più di una==

Ogni volta che lo stato cambia, i componenti di cui è cambiato lo stato vengono rirenderizzati.

==ATTENZIONE l'aggiornamento dello stato non è istantaneo. Quindi, in una funzione, non posso settare lo stato e poi leggere subito il nuovo valore. Quindi conviene o recuperare il valore dall'elemento che lo sta cambiando (Es: l'evento che ha scatenato il cambio di stato), oppure usare un'arrow function in cui prima cambio lo stato, e poi eseguo le operazioni che mi servono.==