Albums è un array di oggetti json, che contengono anche la proprietà titolo.
Some permette di prendere ognuno di essi e confrontare una loro proprietà con un altro valore che arriva da altrove. Torna true se lo trova, false altrimenti.
```javascript

!albums.some(element => element.titolo === album.titolo) ? albums.push(album) : null
```