Questa proprietà degli [[SVG]] permette di tratteggiare una qualsiasi figura o path.
```css
stroke-dasharray: 250 500;
```
come valore prende un array. In base al numero di valori, alternerà tra tratteggio e spazio.
Se ci son due valori, il primo è un tratteggio da 250, il secondo uno spazio da 500 e così via all'infinito.
Se ci fosse un terzo valore (100), avremmo tratto 250, spazio 500, tratto 100, spazio 250, tratto 500 ecc.

Quando ho un path che si chiude (per esempio un cerchio), posso usare questa proprietà, assieme alle [[Transizioni]] per fare un effetto di "linea che si disegna da sola" (vedi [[Timer-Barra Circolare]]).

In pratica, nell'array avrò due valori (il primo, ricordiamo, è la lunghezza del tratto, il secondo del gap.)
Se so la lunghezza totale, posso partire da 0 tratto e 100 gap, e incrementare il tratto ogni tot tempo per far si che il path compaia andando avanti nel tempo (spiegazione con esempi https://css-tricks.com/svg-line-animation-works/).
