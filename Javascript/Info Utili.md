Document.write("ciao") scrive letteralmente ciao nel dom

Concatenamento Variabili in stringhe:
```javascript
console.log(`Il risultato della converisone di ${nomeVariabile} miglia è ${nomeVariabile2}`);
```

Carattere escape:
```javascript
	console.log('il carattere escape è l\')
	console.log("in alternativa posso usare i doppi apici per usare l'apice in una stringa")
```

Prompt (fa apparire una richiesta di input singolo come se fosse un alert)
```javascript
variabile = prompt("Dimmi il tuo nome")
```

=== e !== confrontano i valori E i tipi

Break si usa per terminare i loop
Continue si usa per terminare l'iterazione corrente

Negli switch, mettere sempre un break alla fine di ogni case, altrimenti vengono analizzati anche i successivi.
Inoltre, posso raggruppare vari case per un singolo output
```javascript
switch(Numero){
 case "uno": alert("hai inserito uno")
	 break
 case "due":
 case "tre":
 case "quattro": alert("hai inserito un numero tra uno, due e tre")
	 break
}
```

```javascript
let i = 10
console.log(i++) // stampa 10 e poi fa + 1
console.log(++i) // fa +1 e quindi stampa 11
// stessa cosa con i -
```

Gli array possono contenere tipi diversi