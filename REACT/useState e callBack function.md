Quando voglio settare lo stato di un componente, di base basta inserire il nuovo valore nella funzione di set

```JSX
setMiaVaraibile(nuovoValore)
```

A volte però, potrei dover richiamare il set in una funzione annidata, o voler chiamare il cambio stato più di una volta.
In questi casi, fare così non va bene, perchè avviene la prima esecuzione e il valore si "fissa"

```JSX
const [counter, setCounter] = useEffect(0)

useEffect(() => {
	setInterval(() => {
		setCounter(counter+1)
	}, 1000)
}, [])
```
useEffect con le quadre al fondo viene eseguito solo al primo rendering del componente.
setCounter all'interno di setInterval, viene eseguito una sola volta (per via di useEffect con le quadre).
React arriva lì, e dice quant'è counter? 0+1 = 1.
Poi setInterval torna dopo 1 secondo, e dice "ok, faccio setCounter(1)"
Di conseguenza, il counter a schermo rimane sempre a 1.

Devo allora modificare il codice così:
```JSX
const [counter, setCounter] = useEffect(0)

useEffect(() => {
	setInterval(() => {
		setCounter((oldCounter) => oldCounter+1)
	}, 1000)
}, [])
```
le funzioni di set permettono sempre di inserire come valore una funzione di callBack, che come parametro al suo interno ha il valore dello stato nel momento in cui viene eseguita.
Di conseguenza, quando React arriva lì, trova la callBack che richiede di leggere in tempo reale lo stato e aggiorna il valore correttamente.