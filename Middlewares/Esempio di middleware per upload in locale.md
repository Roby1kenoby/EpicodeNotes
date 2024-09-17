
File middleware che gestirà gli upload
``` Javascript
import multer from 'multer'
// pacchetto di node per gestire i percorsi e le estensioni. node: specifica che vogliamo il pacchetto path specifico di node
import path from 'node:path'

// per recuperare l'estensione del file ricevuto
const storage = multer.diskStorage({
destination: 'uploads'
filename: (req, file, callback) => {
	callback(null, Date.now() + path.extName(file.originalname))
}
})

// come minimo devo indicare il percorso in cui salvare i file in locale. La cartella deve essere nella root del progetto
// const uploadLocal = multer({dest: 'uploads'})

// qui sto dicendo a multer di usare le impostazioni di storage indicate sopra, che specificano comunque una destinazione fisica sul server, ma poi gli speifico come costruire il filename. Se non lo faccio, i file vengono salvati senza estensione.
// storage è praticamente la configurazione di salvataggio

const uploadLocal = multer({ storage})

export default uploadLocal
```

File router
``` Javascript
import express from 'express'
import * as receipeController from 'path'
import uploadLocal from 'path'

const router = express.Router()

// single è una proprietà dell'oggetto di multer che ci permette di recuperare un singolo file. Cover è la chiave nel frontend nel form, da cui multer recupererà il file (Nell'oggetto FormData)
router.post('/', uploadLocal.single('cover'), receipeController.createOne)
```

File con il middleware createOne
```Javascript
export const createOne = (req, res) => {
// restituisco il req.file, che è l'oggetto che multer restituisce, contenente i dati del file archiviato. 
	return res.send(req.file)
// oppure posso far restituire il solo indirizzo dell'immagine, in modo che poi possa essere usato dal frontend (dopo essere stato salvato nel db)

return  res.send({
	imgUrl: `${process.env.HOST}:${process.env.PORT}/uploads/${req.file.originalname}`
	,eventualiAltriParametr: 'valore'
	// posso prendere il body della richiesta, che sarà probabilmente il resto del form oltre all'immagine, e li restituisco come risposta
	, ...req.body
})
}
```

Per testare questo tipo di cosa è necessario utilizzare postman.

I file vengono salvati in un percorso locale del tipo localhost:5000/uploads/nomefile.estensione

Per vederli tramite browser posso usare un altro middleware che si chiama static, di default presente con express.

su Sever.js
``` Javascript
import express from 'express'

// questo permette di far si che se raggiungo una risorsa tramite url, questa viene visualizzata 
app.use('/uploads', express.static('./uploads'))
```