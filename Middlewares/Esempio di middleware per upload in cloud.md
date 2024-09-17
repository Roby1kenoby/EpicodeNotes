Mettere nel file env i cloud name, api key e api secret presi da Cloudinary.

Necessario installare poi tramite npm le seguenti librerie, cloudinary per poter interagire, l'altra per far parlare più facilmente multer e cloudinary. Se no, posso usare le istruzioni presenti su cloudinary (non uso il secondo middleware)

npm i cloudinary multer-storage-cloudinary

```Javascript
import 'dotenv/config'
import multer from 'multer'
import { v2 as cloudinary } from 'cloudinary'
import { CloudinaryStorage} from 'multer-storage-cloudinary'

const uploadCloudinary = multer({
	// config di multer, dove registro?
	// CloudinaryStorage è dalla libreria di collegamento
	storage: new CloudinaryStorage({
		// config di cloudinary
		cloudinary,
		params:{
			// cartella che verrà createa su cloudinary
			folder: 'epicode',
			cloud_name: process.env.CLOUDINARY_CLOUD_NAME,
			api_key: process.env.CLOUDINARY_API_KEY,
			api_secret: process.env.CLOUDINARY_API_SECRET
		}
	})
})

export default uploadCloudinary
```

A questo punto posso usare questo middleware come nell'[[Esempio di middleware per upload in locale]]

File router
``` Javascript
import express from 'express'
import * as receipeController from 'path'
import uploadLocal from 'path'

const router = express.Router()

// single è una proprietà dell'oggetto di multer che ci permette di recuperare un singolo file. Cover è la chiave nel frontend nel form, da cui multer recupererà il file.
router.post('/', uploadCloudinary.single('cover'), receipeController.createOne)
```

CreateOne poi dovrà occuparsi di salvare sul db, e restituire al frontend quello che serve per renderizzare i componenti

```Javascript
export const createOne = async (req, res) => {
    // creo un nuovo oggetto Recipe da inserire sul db, che prende i dati dal body.
    // Author lo devo parsare come JSON perchè è un oggetto JSON, ma arriva sotto formato di stringa.
    // Nella request, Cloudinary mi restituisce delle proprietà file.path che sono il percorso all'immagine salvata dal middleware sopra.
    const newRecipe = new Recipe({
        ...req.body,
        author: JSON.parse(req.body.author),
        cover: req.file.path,
    });

	// a questo punto salvo la nuova ricetta sul DB
    const createRecipe = await newRecipe.save().catch((err) => {
        console.log('Errore: ', err);
        return res.status(500).send(err);
    });

    return res.send(createRecipe);
};
```
