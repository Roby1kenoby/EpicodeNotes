Informazioni che il componente padre passa al componente figlio.

Col fatto che i Componenti sono funzioni, posso passargli dei parametri.

```jsx
// props è un nome generico, posso usare un nome qualsiasi
function Slide(props){
	
	return <div>{props.titolo}</div>
}

export default Slide;
```

Gli attributi dell'html nel jsx sono proprietà di un oggetto, che viene poi passato come props al componente figlio. 
Posso passare come attributi anche numeri, oggetti, array e funzioni, l'importante è farlo aprendo le graffe (perchè ho bisogno di js)
```jsx
function Carousel(){
return{
	<div>
		<Slide titolo="Slide uno" buttonText="cliccami" par3={[1,2,3]}>
	</div>
	}
}
```


Se ho un oggetto complesso da passare come prop, posso anche fare così:
```jsx
function AllTheBooks() {
    return (  
        <div className="row row-cols-4">
            {
                books.map(b => <MyCard key={b.asin} book={b}></MyCard>)
            }
        </div>    
    );
}
```
In pratica book è un oggetto json complesso, e passo direttamente lui come prop.
L'oggetto che poi lo riceve:

```jsx
function MyCard({book}) {
    return (
        <Card>
            <Card.Img variant="top" src={book.img} />
            <Card.Body>
                <Card.Title>{book.title}</Card.Title>
                <Card.Text>
                    Price: {book.price} €
                </Card.Text>
            </Card.Body>
        </Card>
    );
}
```
Qui posso richiamare le proprietà dell'oggetto book direttamente dentro all'html.
==Importante: per poter usare book.img, book.title ecc, il nome del prop deve essere messo tra graffe, altrimenti non riesco ad accedere alle proprietà.==


Posso destrutturare la props ricevuta direttamente nominando tra le graffe i nomi delle chiavi.
È una tecnica rapida, che va bene quando ho pochi attributi, se son tanti diventa disordinato.

```jsx
// posso anche attribuire un valore di default con questo tipo di passagio dei props
function Slide({titolo='ciao', buttonText, par3}){
	
	return <div>{props.titolo}</div>
}

export default Slide;
```