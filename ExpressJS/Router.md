Posso gestire meglio le varie rotte usando un Router

per farlo, nel mio file server: 

```Javascript
import userRouter from 'path'
// il primo parametro è un eventuale prefisso che posso applicare a tutte le rotte.
server.use('/users', userRouter)

```

in genere, si fa una cartella separata (routes), e dentro ci faccio un file per "argomento"

es user.router.js e dentro ci metto 

```Javascript
import express from 'express'
const router = express.Router()
	//chiamate varie
	router.get('/:id', (req,res) => {
	//cose
})

export default router
```


```Javascript
import express from 'express'
import userRouter from './routes/user.router.js'

// così richiamo le rotte definite in un altro file
server.use('/', userRouter)
```