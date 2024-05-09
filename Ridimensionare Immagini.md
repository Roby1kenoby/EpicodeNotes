In genere, conviene dare una dimensione al contenitore, e poi dire all'immagine che la width = 100% del contenitore.
```css
main img{
    width: 100%;
    height: 300px;
    object-fit: cover;
    border-radius: 1em;
    box-shadow: 4px 6px 3px rgb(147, 146, 146);
}
```
Objecet-fit cover permette di non distorcere l'immagine.
Serve dare un'altezza per "tagliare" l'immagine.
Border-radius è per arrotondare gli spigoli delle immagini. È anche possibile modificare anche solo uno spigolo e non tutti.
Box-shadow è per dare un'ombra (i parametri sono offset orizzontale, offset verticale, blur, colore)