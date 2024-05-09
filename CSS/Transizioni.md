Creano effetti di transizione degli elementi da uno stato a ad uno stato b.
Posso applicarla ad n aspetti (colori, ombre, posizione ecc).
Devo avere definito la situazione iniziale e poi quella di arrivo
(per es, ombra base e poi ombra su hover)
```css
/*a cosa applico, quanto deve durare, tipo di interpolazione, ritardo*/
transition: color 1s linear 0.2s

.card{
	overflow:hidden;
	transition: transform 1s linear;
}

.titolo{
	position: absolute;
}

.card:hover .titolo{
	transform: translateX(100%);
}
```
Nell'esempio sopra, applico la transizione (durata un secondo) alla proprietà transform.
Quando passo il mouse sull'oggetto, la proprietà transform è differente, quindi viene applicata (in questo caso trasla sull'asse x del 100% della propria lunghezza)

La posizione deve essere Absolute, per le transizioni.
La cosa che contiene il titolo deve avere overflow:hidden, per far si che quando il titolo esce, rimanga "invisibile"

L'attributo transition posso metterlo sia nell'elemento base, sia nell'elemento trasformato.
La differenza è che se metto nell'elemento base, la transizione avviene sia in una direzione sia nell'altra.
Se la metto invece nell'elemento con la trasformazione (l'hover, per esempio) allora avviene solo verso di lui, ma viceversa no (ritorna allo stato di partenza di botto)

Posso anche fare transition all per fare "animare" tutte le proprietà che cambiano da uno stato all'altro, oppure lasciare vuoto e mettere solo il tempo (è la stessa cosa)