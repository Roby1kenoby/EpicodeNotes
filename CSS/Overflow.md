Questa proprietà permette di definire come viene gestito l'overflow degli elementi 
Se un contenitore che dentro ha un'immagine, se non metto overflow hidden e l'immagine è più grande del contenitore, (perchè per esempio applico la stondatura dei bordi), questa uscirà fuori ed andrà a coprire la stondatura del bordo (che quindi non verrà visualizzata)
Overflow: auto; mette in automatico la barra di scorrimento più adatta per il contenuto

Posso impostare white-space: nowrap; per evitare che il testo vada a capo quando trova ostacoli.
Posso impostare text-overflow: ellipsis; per far si che quando il testo viene troncato appaiano i 3 puntini.

Esempio:
```html
<section id="cardContainer">
            <div class="card">
                <img src="https://picsum.photos/300/200" alt="product">
                <div class="infoContainer">
                    <h3>Brugola 1</h3>
                    <p>Set di brugole</p>
                    <a href="#">link</a>
                    <div class="reviewWrapper">
                        <input type="text" placeholder="Lascia una recensione!">
                        <button>Invia!</button>
                    </div>
                </div>
            </div>
</section>
```

Il padre deve avere una width fissa, allora posso mettere nell'elemento che deve fare ellipsis le impostazioni 
```css
.card{
    border: 1px solid grey;
    display: flex;
    flex-direction: column;
    width: 25vw;
}

.infoContainer p{
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
```