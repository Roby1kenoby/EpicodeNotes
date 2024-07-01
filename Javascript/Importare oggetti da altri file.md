```javascript
// definisco un oggetto esportabile così:

export const books = [
	// array con oggetti
]

export const films = [
	// cose
]
```

Così posso importare in altri file (che posso anche rinominare)
```javascript
import {books, films as nuovoNome} from 'path'
```

Posso anche importare direttamente oggetti da file .json