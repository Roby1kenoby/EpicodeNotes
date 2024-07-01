Sono presenti due tecniche per gestire gli input dei form:
O un oggetto con più proprietà, o più stati.


```jsx
import {useState} from 'react';

// se metto in useState un valore, sarà il valore di default iniziale
const [title, setTitle] = useState('');
const [author, setAuthor] = useState('');
const [img, setImg] = useState('');
const [excerpt, setExcerpt] = useState('');

// campi nel form, manca il contenitore esterno
<Form.Control placeholder="title" 
onChange={(event) => setTitle(event.target.value)} value={title}/>

// affinché poi i componenti vengano renderizzati nuovamente, devo mettermi in ascolto dell'evento onchange

// quando qualcosa cambia, nella funzione onChange viene passato l'evento di cambio. Questo evento ha tante proprietà, tra cui il target (l'oggetto che è cambiato) e di conseguenza anche il suo valore.

<Form.Control placeholder="author" value={author}/>

<Form.Control placeholder="img" value={img}/>

<Form.Control placeholder="excerpt" value={excerpt}/>



```

In pratica, non è l'utente che scrive, che fa cambiare il testo nel box, ma è l'evento che si attiva, perchè sta cambiando qualcosa ed è React che renderizza il cambiamento.
Questo perchè gli ho detto che value = {nomeDelParametroDelloStato}

In pratica gli dico sii uguale a quella variabile, ma se poi non uso lo stato per aggiornare la variabile, questa non viene cambiata e il value rimane sempre lo stesso (cioè quello iniziale)

La modalità alternativa è questa.
```jsx
const [formData, setFormData] = useState({
	title: '',
	author: '',
	img: '',
	excerpt: ''
})

<Form.Control placeholder="title" onChange={(event) => setFormData({...formData, title: event.target.value})} value={formData.title}
```
l'operatore spread (...) esplode un oggetto (prende le singole chiavi e le restituisce. Funziona anche con gli array.)

Se lo metto tra un paio di graffe, in pratica sto creando una copia dell'oggetto iniziale (che è quello che vogliamo, perché noi NON possiamo modificare l'oggetto originale, ma dobbiamo passare il nuovo stato).
Dopo aver fatto questa operazione, posso con la virgola andare a modificare (o aggiungere, se la chiave non è ancora presente) valori all'interno del nuovo oggetto.
Questo sarà il mio nuovo stato.

Visto che l'operazione è un po' più lunga rispetto a quando ho un singolo stato, posso anche farmi una funzione esterna al return, alla quale passo la cosa che voglio modificare.
```jsx
const updateInput = (event) =>{
// event.target contiene sia l'oggetto che ha triggerato la modifica, sia il suo valore.
	const target = event.target;
	setFormData({...formData, 
	// target.name tra quadre è perché sto passando all'oggetto una chiave in maniera dinamica
	[targe.name]: target.value})
}

return{
	<Form.Control 
	placeholder="title" 
	// il name è importante perchè così in event.target ho sia il nome del campo sia il suo valore.
	name="title"  
	value={formData.Title}
	onChange={updateInput}
}
```

==ATTENZIONE onChange, se ci metto dentro una funzione, non devo metterla con le () ==
Le parentesi dopo il nome funzione, sono un operatore che esegue la funzione. Di conseguenza, se la associo ad un evento, gli sto dicendo di chiamarla immediatamente se metto le parentesi. Senza, sto dicendo all'evento "esegui queta funzione quando arriva il momento opportuno" (cioè quando parte l'evento)