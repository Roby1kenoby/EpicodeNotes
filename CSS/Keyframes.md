I Keyframes sono strumenti per effettuare [[Animazioni]] in css.

Li definisco così:

```css
@keyframes NomeFunzione{
	...
}
```

Approcio from - to (molto simile alle transition standard)
```css
@keyframes NomeFunzione{
	from {opacity: 0}
	to {opacity: 1}
}
```

Approcio percentuale
```css
@keyframes NomeFunzione{
	0% {opacity: 0}
	50% {opacity: 0.5}
	100% {opacity: 1}
}
```

Per richiamare l'animazione, faccio così:
```css
.nomeclasse{
	animation: nomeAnimazione 2s ease-in-out;
}
```
Oltre alle proprietà identiche alla transition (vedi sopra) ci sono anche le proprietà 
```css
animation-iteration-count /* quante volte deve essere eseguita l'animazione*/
animation-fill-mode /* stile da applicare prima dopo o entrambe la fine dell'animazione */
animation-direction /* verso la fine o dalla fine verso l'inizio*/
```
Posso applicare ad un oggetto anche più animazioni.
```css
.classe{
	animation-name: caduta, ondeggia;
	animation-duration: 2s, 5s;
	animation-iteration-count: infinite, infinite;
	animation-timing-function: ease-in-out, linear;
}
```

Per usare i keyframes su browser diversi, è necessario specificare quanto segue:
```css
@-webkit-keyframes rotate{
	//edge\explorer
}
@-moz-keyframes rotate{
	/firefox
}

@keyframes rotate{
	// chrome
}
```