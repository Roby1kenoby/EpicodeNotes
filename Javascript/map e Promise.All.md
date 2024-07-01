In questo esempio, map crea un array di promises.
Di conseguenza posso passarle a Promise.all che ha proprio lo scopo di ricevere un array di promoses, attendere che tutte abbiano finito e poi proseguire (questo grazie all'await) 
==Con forEach non funzionerebbe!==
```javascript
let getAlbumsData = async function(artArr){
	const promisesArray = artArr.map(a => f_getAlbum(a))
	await Promise.all(promisesArray)
}
```