Posso tirare fuori tutte le chiavi di un oggetto, così, e usarle contestualmente per stampare il relativo valore
```javascript
Object.keys(oggetto).forEach(key => {
	console.log(key)
	console.log(oggetto[key])
})
```


