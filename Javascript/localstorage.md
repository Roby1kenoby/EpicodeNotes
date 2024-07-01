se voglio passare al localstorage degli oggetti json, devo per forza trasformargli in stringa (e poi farne il parse quando li recupero)

```javascript
	let oggettoJson = {//cose
	}

	localStorage.setItem(chiave, JSON.stringify(oggettoJson))
	
	let itemRecuperato = json.parse(localStorage.getItem(chiave)))
```