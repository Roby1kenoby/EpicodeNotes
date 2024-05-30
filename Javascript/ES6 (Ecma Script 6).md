Insieme di regole da cui deriva javascript.
Permette di utilizzare delle keyword specifiche e altre funzionalità varie.
### This
L'operatore this viene usato per richiamare il contesto di esecuzione di una funzione o di un oggetto specifico. Bisogna fare attenzione ad utilizzarlo, però, perché se uso arrow notation fa riferimento al contesto generale (la window), senza arrow notation invece funziona correttamente e mi restituisce il contesto dell'oggetto da cui viene richiamato
```javascript
let obj1{
	name: 'Lidia'
	desc: 'blabla'
	getCapitalName: () => {
		console.log(this.name.toUpperCase()) // questo this fa riferimento alla window. Non lo userò mai, così.
	}
}

let obj2{
	name: 'Pippo'
	desc: 'blabla'
	getCapitalName: function() {
		console.log(this.name.toUpperCase()) // questo this fa riferimento all'oggetto stesso (obj2), e quindi this.name è effettivamente la proprietà name, cioè Pippo.
	}
}


```
This può essere comodo per quando ho da istanziare n oggetti proceduralmente, e voglio assegnargli una funzione che agisca su uno specifico selezionato\\hoverato ecc.
```javascript
	btn = Document.createElement("button")
	btn.addProperty('onClikc', `nomeFunzione(${this})`)

```
### Spreading
```javascript
obj1 = [{cose}]
obj2 = [{cos2}]
obj3 = [...obj1, ...obj2, 'pippo' ]

// l'output sarà un array con tutti gli elementi
```


### Creazione rapida variabili da oggetti
```javascript
let ob1 = {
	nome: 'roberto',
	cognome: 'allocco'
}

let {nome, cognome} = ob1
// se chiamo le mie variabili come le chiavi dell'oggetto, non devo dichiararle con let bla bla bla, ma vengono generate in automatico
```

### Settare attributi di oggetti
```javascript
	var nuovoDiv = Document.createElement("div")
	nuovoDiv.id = varId
	// questo modo di assegnare una funzione su click non la fa comparire nel DOM.
	// nuovoDiv è letteralmente l'oggetto, quindi come parametro della funzione sto passando l'intero div.
	nuovoDiv.onClick = () => {nomeFunzione(nuovoDiv)}
```