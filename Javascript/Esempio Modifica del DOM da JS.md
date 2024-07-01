Per comodità, è possibile creare uno scheletro dell'oggetto che voglio replicare nel DOM, e poi clonarlo e modificarlo.

Es:
Questa è una card, che contiene una funzione onClick, un'immagine, un titolo e un paragraph che verranno modificati tramite js.
```html
<div class="album-card card d-none" data-bs-toggle="modal" data-bs-target="#tracksModal" onClick="getAlbum()">
  <img src="" class="album-img card-img-top" alt="missing">
  <div class="card-body">
	<h5 class="album-title card-title text-truncate"></h5>
	<p class="album-author card-text text-truncate"></p>
  </div>
</div>
```
Recupero l'elemento e lo clono, poi lo elimino dal dom.
```javascript
let cardHtml = ''
// funzione per recuperare l'html di una card già fatta, così è più semplice creare le altre. Poi la cancello

let findFirstCard = function(){
    firstCard = document.getElementsByClassName('album-card')[0]
    cardHtml = firstCard.cloneNode(true)
    firstCard.remove()
}
```
A questo punto posso usare questo scheletro per riempirlo e poi inserirlo dove mi serve.
```javascript
// funzione per creare la singola card di un album e la relativa sezione
let createAlbumCard = function(album){
	// tramite il querySelectorAll ricerco all'interno dell'elemento cardHtml
	// che alla fine dei conti è un pezzo del dom, quindi risponde a questo tipo
	// di query, e ne modifico le proprietà
    let cardImage = cardHtml.querySelectorAll('img')[0]
    // source dell'immagine
    cardImage.setAttribute('src', album.cover)
    
    let albumTitle = cardHtml.querySelectorAll('h5')[0]
    // contenuto dell'h5
    albumTitle.innerHTML = album.titolo
  
    let albumAuthor = cardHtml.querySelectorAll('p')[0]
    // contenuto del paragraph
    albumAuthor.innerHTML = album.artist

	// proprietà onClick
    cardHtml.setAttribute('onClick', `getAlbum("${album.tracklist}")`)
    // rimuovo la classe bootstrap che gestisce la visibilità
    cardHtml.classList.remove('d-none')

	// infine, ricerco la sezione in cui voglio inserirlo con un altro querySelector
	// e faccio append child (non so perchè ma è necessario fare appendchild, e dentro metterci il clone. Al contrario non ha funzionato)
    authorSection.querySelectorAll('div')[0].appendChild(cardHtml.cloneNode(true))
}
```

Un modo ancora più semplice è il seguente:
```javascript

let row = document.createElement('tr')
    row.innerHTML = `
    <th scope="row">${data.id}</th>
	    <td>${data.name}</td>
	    <td>${data.username}</td>
    <td>${data.email}</td>
    `
tableBody.appendChild(row)
```
Utilizzando i backtick, posso scrivere direttamente in html e usare variabili per inserire i valori parametrici.
Creato l'html posso poi appenderlo ad un corpo già presente nel DOM