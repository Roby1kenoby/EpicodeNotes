Posso impostare un valore di default per un parametro di una funzione, direttamente in fase di definizione
```javascript
function saluta(param1, param2 = 'Boh'){
	console.log(param1 + ' ' + param2)
}
```

HOISTING: le funzioni hanno priorità di elaborazione. Il browser legge tutto lo script, trova le funzioni e le memorizza, e poi passa all'esecuzione. Quindi, di per se, posso mettere anche le funzioni tutte al fondo.

Funzione anonima: non è riutilizzabile, e l'hoisting non funziona (cioè essendo che è anonima, vale solo nel momento in cui è dichiarata). Si usa di solito quando ti serve solo per una cosa specifica in un certo momento
```javascript

console.log(prodotto(3,5)) // questo va in errore, perchè qui non esiste ancora la funzione

let prodotto = function(fatt1, fatt2){
	return fatt1 * fatt2
}

console.log(prodotto(3,5)) // qui invece funziona
```

**SE non metto let davanti ad una variabile, la sto dichiarando come GLOBALE**

```javascript
	// permette di valutare il contenuto che gli passo come se fosse un'operazione matematica
	eval()
```