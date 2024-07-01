Se il nome di una chiave di un oggetto è uguale al nome della variabile con cui voglio valorizzarla, posso fare semplicemente così:

```javascript
const title = 'pippo'
const author = 'mario'

obj ={
	title: '',
	author: ''
}

obj = {
	title,
	author
}
```