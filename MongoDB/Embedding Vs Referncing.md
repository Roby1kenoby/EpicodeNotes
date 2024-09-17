Embedding vuol dire mettere tutto in un solo oggetto (es: Post di un blog, ci metto dentro anche l'array con i commenti).
- Comodo perchè ho tutto in un solo posto
- No join
- Aggiorno i dati con una sola operazione.
- Scomodo perchè ho documenti grandi, e ho un limite massimo di 16Mb per un singolo documento.
- Scomodo perché duplico i dati
Referncing vuol dire fare collection diverse (Una per i post, una per i commenti) e poi referenziare gli id dei commenti nel post.
- Scomodo per i Join, che sono lenti
- Pro, documenti più piccoli
- No duplicazione dati

Quale approccio scegliere dei due? Dipende dalle esigenze dell'app, dai carichi di lavoro e le relazioni tra le entità.

Il referencing è migliore se ho un oggetto con una proprietà che contiene un array che può crescere indefinitamente, oppure se so che devo accedere ad uno specifico elemento dell'array da solo.

Altrimenti, è quasi sempre preferibile l'embedding (mongo nasce un po' per quello).

Se devo fare referncing in uno [[Creazione Schema |Schema]]

```Javascript

import mongoose, {Schema} from "mongoose"
const userScherma = new Schema({
	name: {
		type: String
		required: true
	},
	// qui sto specificando che il tipo è un objectId
	cart: [{type: Schema.Types.ObjectId, ref:"product"}]
}, {collection: "users"}
)

// altro file schema
const productSchema = new Schema({
	prodName: {
		type: String,
		required: false
	},
	// altri campi
}, {collection: "sales"})

// questo "product" è quello che fa capire a mongoDb che la reference è di questo tipo qua, con questo schema.
export default model("product", productSchema)

// quando poi faccio la query nella rotta, posso chiedere a mongoDB di popolare l'eventuale array con gli oggetti referenziati, così:

userRoute.get("/me/cart", async (req,res)=>{
	const allUsers = await User.findOne({
		email: req.user.email
	})
	// populate dice a mongoDb, vai in cart dell'user, ti prendi gli id, te li cerchi nella collection corrispondente e mi popoli con i dettagli dei singoli product
	.populate("cart")
	res.send(allUsers.cart)
})

```


==Funzione specifica per l'embedding==
Se devo andare a ricercare (per eliminare o modificare) un valore embeddato, che ha una chiave, posso usare la funzione:

```Javascript
const recipe = await Recipe.findById(req.params.recipeId)
// id è la funzione specifica per trovare un elemento embeddato (ingredients è un array di oggetti all'i'nterno della ricetta)
const oldIngredient = recipe.ingredients.id(req.params.ingredientId)
oldIngredient.deleteOne()
```