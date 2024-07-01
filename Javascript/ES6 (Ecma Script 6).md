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
Funziona solo sugli array e sugli oggetti, li cicla ed esplode gli elementi
```javascript
obj1 = [45, 46]
obj2 = [{key: value}]
obj3 = [1, 2]
obj4 = [...obj1, ...obj2, 'pippo', obj3 ]
// l'output sarà un array con tutti gli elementi ESPLOSI
console.log(obj4) // 45, 46, key: value, 'pippo', [1, 2]

// sugli oggetti, lui cicla le chiavi al loro interno e crea un oggetto unico con tutte le chiavi.
// ATTENZIONE: se due chiavi sono uguali, prenderà l'ultima in ordine cronologico
obj1 = {name: rambo, age: 12}
obj2 = {name: jhon, sex: m}

oo = {...obj1, ...obj2}
console.log(oo) // {name: jhon, age: 12, sex: m}
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

### Settare rapidamente attributi di oggetti html
```javascript
	var nuovoDiv = Document.createElement("div")
	// così sto letteralmente dicendo al div "il tuo id è varId".
	// c'è un parametro per ogni attributo (tipo className, style ecc)
	nuovoDiv.id = varId
	// questo modo di assegnare una funzione su click non la fa comparire nel DOM.
	// nuovoDiv è letteralmente l'oggetto, quindi come parametro della funzione sto passando l'intero div.
	nuovoDiv.onClick = () => {nomeFunzione(nuovoDiv)}
```

### Variabili negli elementi del DOM
Utilizzando la notazione data-nomeVariabile posso inserire nei miei oggetti sul dom dei valori extra che magari mi servono dopo, e mi risparmiano una fetch successiva (per esempio).
*Attenzione, l'oggetto che viene restituito, ha poi nomi variabili non in camel o snake case (appiattisce tutto)*
```html
	<div id="pippo" data-nomeVariabile="miovalore" data-nomeVariabileDue="miovalore2"></div>
```
```javascript
	let d = Document.getElementById('pippo')
	// dataset è proprio il termine per tirare fuori i valori che ho messo nei data-NomeVariabile
	console.log(d.dataset)
```