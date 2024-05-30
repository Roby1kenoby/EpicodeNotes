Per effettuare chiamate rest
```javascript
fetch('url').then((response) => {
	// cose con la response
}).catch((err) => {
	console.log(err)
});
```

Esempio reale
```javascript
const albumUrl = 'https://striveschool-api.herokuapp.com/api/deezer/search?q=metallica'

// la funzione è async perchè voglio usare await prima del fetch, in modo che gli step successivi avvengano solo alla conclusione del fetch
let findAlbums = async function(url, authorId){
    const resp =  await fetch(url)
    // è necessario trasformare in json affinché la risposta sia gestibile
    let data = await resp.json()
    let albums = []
    //mappo la response
    data.data.map((a) => {
        let album = {
            titolo: a.album.title,
            tracklist: a.album.id,
            cover: a.album.cover_big,
            artist: a.artist.name
        }
        // controllo che l'album non ci sia già nell'array
        !albums.some(element => element.titolo === album.titolo) ? albums.push(album) : null
    });
    return [albums, authorId]
}
```