### Filter
Se al filtro passo una condizione che mi restituisce un valore booleano, allora l'array di ritorno è filtrato.
```javascript
// versione ridotta
array.filter(x => x<5)

array.filter(function(x, i){
	// faccio cose con x
	// se voglio che l'array venga filtrato tramite una funzione, devo però usare un'istruzione di return.
	// se inserisco un secondo parametro, in genere è l'indice
})
```

### forEach
Prende ogni singolo elemento dell'array e ci posso fare cose tramite funzione. ***Non restituisce niente.***
```javascript
array.forEach(elemento, i) => {
	//elemento è il singolo oggetto nell'array, i è l'indice che viene auto incrementato (e non è necessario avercelo, ma se serve l'indice è quello)
}
array.forEach(elemento => {
	// così è senza indice
})
```
==ATTENZIONE: il forEach crea problemi con le funzioni asincrone!==
Se ne sbatte delle promise e appena ha finito il ciclo esce!
Se hai bisogno di fare tante chiamate async in parallelo, usare [[map e Promise.All]]
### Map
 A differenza del forEach, questo restituisce un array, che è quello originale, modificato con le istruzioni applicate ad ogni singolo elemento.
```javascript
// così sto dicendo ad Array, di trasformarsi in un array in cui ogni singolo elemento è stato modificato con la struttura di objTemp
array = array.map(x => {
	const objTmp = {
		par1: x.primoValore,
		par2: x.secondoValore,
		//ecc
	}
	return objTmp
})
```

### Reduce
aggrega gli elementi dell'array e restituisce un valore unico
```javascript
myArray = [1,3,5,9,2]
let sum myArray.reduce((curr, temp) => curr+temp, 0)
// result: 20
```

### Join
```javascript
// concatena gli elementi all'interno di un array, e posso inserire un separatore.
// se non lo metto no problem, in ogni caso il risultato è una stringa
myArray.join(',')
```

### Find\\FindIndex
Deriva da [[ES6 (Ecma Script 6)]]
```javascript
const numbers = [24,41,12,654,87]
numbers.find(n => n>30)
// restituisce 41. Se non c'è, -1
numbers.findIndex(n => n>30)
// restituisce 1 (la prima istanza). Se non c'è, -1
```

### Includes
Deriva da [[ES6 (Ecma Script 6)]]
```javascript
const numbers = [24,41,12,654,87]
numbers.includes(24)
// restituisce true
numbers.findIndex(n => n>30)
// restituisce false
```

