Posso creare funzioni che restituiscano una Promise così:
``` javascript
	function blabla(){
		// posso anche omettere function, l'importante sono le due parentesi, tanto è una funzione anonima
		return new Promise(function(resolve, error) => {
			// operazioni varie
			resolve("quello che voglio")
			// se voglio gestire qua dentro l'error:
			if (/*cose*/){
				error()
			}
		})
	}
```
È assolutamente necessario che io nella funzione ad un certo punto gli dica resolve() (con o senza valori all'interno, dipende se mi serve gestire quello che restituisce la funzione), altrimenti rimarrà sempre in stato di attesa.

Nelle promise, in pratica, sono io che decido quando far uscire con ok o ko la response, grazie all'utilizzo di resolve ed error (che posso chiamare come voglio)