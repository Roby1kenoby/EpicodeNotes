```Javascript
//aggiungere elementi

const newUser = {
	"name": "Jhon",
	"surname": "Rambo"
}

const newDocument = new userModel(newUser)
await newDocument.save()

// get
// exists restituisce l'id se c'è qualcosa che corrisponde nel db
const authorExists = await Author.exists({email: data.email})
// find restituisce collezioni di oggetti o oggetti interi
const users = await userModel.find({})
const users = await userModel.findById(id)
const users = await userModel.findOne({})


// update
// il primo parametro è la ricerca, il secondo l'update
await userModel.findOneAndUpdate({name:"Jhon"}, {surname: "Rambo"})

await userModel.findByIdAndUpdate("id", {surname: "Rambo"})


// delete
await userModel.findOneAndDelete({name: "Jhon"})
userModel.findByIdAndDelete("id")
```
