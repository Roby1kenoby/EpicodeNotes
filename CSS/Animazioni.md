Vedi [[Timer-Barra Circolare]]
l'animation linear è lineare, ma ci sono anche altre tipologie di animazione (ease in, out ecc)
```css
circle{
	/* inizializzo il cenrchio, soprattutto per le proprietà dashoffset e dasharray
	*/
	fill: transparent;
	stroke: pink;
	stroke-width:16;
	stroke-dashoffset:500;
	stroke-dasharray:0;
	animation: 30s countdown linear
}

/* imposto dei keyframes, dicendogli alla percentuale x dove deve essere come stroke dasharray */
@keyframes countdown{
	0%{
		stroke-dasharray:500 0;
	}
	100%{
		stroke-dasharray:0 500;
	}
}
```
Posso anche dire from{} to {} se ho solo un inizio e fine e non devo passare per punti intermedi

In genere, per le animazioni con i gradienti ed i colori, conviene sempre avere un div che dia la forma, e all'interno di quello metterci invece i colori.

