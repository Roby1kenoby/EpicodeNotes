```Javascript
import express from 'express'
// modalità di importazione moderna per il file env
import 'dotenv/config'
import mongoose from 'mongoose'

const server = express();
// dato preso dall'env, con dato di default
const port = process.env.PORT || 5000

server.listen(port, () => {
	console.log('server is on')
})

// passo come parametro la connection string, poi posso fare cose
mongoose.connect(process.env.MONGODB_CONNECTION_STRING).then(() => {
console.log('connessione al db ok')
}).catch((err) => {
console.log(err)
})
```

In genere posso anche creare un file apposito con la connessione al DB e poi importarla nel file server
```Javascript
import mongoose from "mongoose"
import 'dotenv/config'

const mongoDbConnection = async () => {

    // meglio qui la connectionString perchè così non diventa globale
    const connectionString = process.env.MONGODB_CONNECTION_STRING
    try {
        await mongoose.connect(connectionString)
        console.log('connessione al db ok')
    } catch (error) {
        console.log(error)
    }
}

export default mongoDbConnection

// file server.js

import mongoDbConnection from './db.js'

// collegamento al mongoDB se uso il file importato
mongoDbConnection()

```

