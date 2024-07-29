È un [[hook]]. Vogliamo che avvengano cose al montaggio del componente (per esempio fare chiamate fetch al caricamento della pagina)

Anche questo si prende due parametri, il primo è una funzione (callback) il secondo è un array (detto array delle dipendenze)

La funzione di callback deve essere definita prima del momento in cui viene chiamata.
Volendo posso anche definirla direttamente nel useEffect tra graffe.

In pratica, quando il componente viene caricato, viene eseguita subito la funzione di callback.

- Se non metto l'array come secondo argomento, la funzione viene richiamata ad ogni rerendering del componente (non si fa quasi mai questa cosa, perché ci sono rischi di andare in loop infinito. La funzione aggiorna il componente, che si modifica e quindi riesegue la funzione.)
- Se invece ci metto l'array vuoto, viene eseguita solo la prima volta.
- Se nell'array ci metto variabili, la funzione verrà eseguita al cambiamento delle variabili nell'array.

```JSX
useEffect(nomeFunzione, [variabileCheTriggeraEsecuzione])
```

Per far piacere ad useEffect una funzione async, devo richiamarla con una funzione sincrona

```JSX
useEffect(() => {funzioneAsync()}, [parametri])
```
==Attenzione però, devo mettere le parentesi graffe, perchè così evito che la funzioneAsync restituisca cose alla useEffect, che non vuole niente di ritorno==

***Se l'array delle dipendenze è vuoto***, e ho un'istruzione di RETURN nella funzione, questa viene eseguita allo smontaggio del componente (questo perchè è la libreria REACT che ci da questa possibilità)

```JSX
useEffect(() => {
	// faccio cose
	return () => console.log('Questa istruz viene eseguita allo smontaggio del componente, solo se larray dopo è vuoto.')
}, [])

// oppure

useEffect(() => {
	// faccio cose
	// funzione che voglio venga eseguita allo smontaggio, solo se array vuoto dopo la callback
	function pippo = (){
		// fai cose
	}
	// no parentesi, se no viene eseguita subito
	return () => pippo
}, [])
```

==Attenzione: se devo richiamare funzioni che dipendono l'una dall'altra, è più comodo metterle in due useEffect distinti e far si che quella che dipende dall'altra si aggiorni al variare del parametro della prima==

```JSX
    useEffect(changeGenre, [selectedGenre])

    // spezzo lo useEffect in due (al posto che mettere le due funzioni nello stesso useEffect), perchè

    // una dipende dall'altra, e la latenza incasina le cose (cambio genere, ma la funzione filter books si

    // trova ancora lo stato "vecchio".)

    // devo però mettere anche come stato monitorato books, perchè la funzione filterbook dipende dallo

    // stato books

    useEffect(filterBooks, [books, searchInput])
```