```Javascript
import express from 'express'
// modalità di importazione moderna
import 'dotenv/config'
import mongoose from 'mongoose'

const server = express();
// dato preso dall'env, con dato di default
const port = process.env.PORT || 5000

server.listen(port, () => {
	console.log('server is on')
})

mongoose.connect(process.env.MONGODB_CONNECTION_STRING).then(() => {
console.log('connessione al db ok')
}).cath((err) => {
console.log(err)
})
```