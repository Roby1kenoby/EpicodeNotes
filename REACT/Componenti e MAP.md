==È importante, quando si creano più componenti a partire dallo stesso scheletro, dare ad ognuno di essi una chiave univoca.==
Questo perché react usa questa chiave per capire qual è il componente tra i molti che è variato, e aggiorna solo quello.
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
Questa sopra è la sintassi "rapida", ho solo una roba che sta su una riga.
Se devo mettere più righe:

```jsx
function AllTheBooks() {
    return (
        <div className="row row-cols-4">
            {
                books.map(b => (
	                // cose da ciclare
                )
            }
        </div>    
    );
}
```