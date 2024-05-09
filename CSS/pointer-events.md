Pointer event mi permette di definire se, quando il mouse passa su un oggetto,  sia "interagibile"
```css
.class{
	/*disabilita*/
	pointer-events: none;
	/*abilito e faccio comparire manina per indicare interazione*/
	pointer-events: auto;
	cursor: pointer;
}
```

Ci sono anche pointer-events specifici per gli svg (tipo fill, o stroke per prendere il focus quando il mouse entra sul bordo o nel contenuto)