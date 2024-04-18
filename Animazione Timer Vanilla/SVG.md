Svg sta per Scalable Vector Graphics. È una sintassi che permette di fare simboli\\grafica ecc in vettoriale, in modo che scali con la risoluzione dello schermo.

https://www.w3schools.com/html/html5_svg.asp

In genere si crea un tag svg e poi si disegna al suo interno.

``` html
<svg width="100" height="100">  
  <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />  
</svg>
```
Stroke è la proprietà che ti permette di evidenziare il bordo. Fill invece permette di definire il riempimento.

Ci sono vari tipi di figure prefabbricate in cui devi solo mettere le coordinate, e poi c'è il path.

Il path permette di fare qualsiasi tipo di figura. https://www.w3schools.com/graphics/svg_path.asp
Le lettere usate per fare il path se minuscole sono a posizione relativa, se sono maiuscole sono a posizione assoluta.
L'istruzione più complicata è la a, per fare archi.
https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths
```html
A rx ry x-axis-rotation large-arc-flag sweep-flag x y
a rx ry x-axis-rotation large-arc-flag sweep-flag dx dy
```
rx e ry sono la lunghezza del raggio sugli asse x e y, a partire dal centro della semi ellissi.
x e y (o dx e dy se usiamo coordinate relative), al fondo, sono il punto di arrivo dell'arco.
x-axis rotation è l'inclinazione sull'asse x.
![[RotazioneArcoSvg.png]]
large-arc-flag decide se l'arco deve essere meno (0) o più (1) di 180 gradi. Sweep flag decide se l'arco si muoverà su un angolo negativo (0) o positivo (1).
La combinazione dei due indica quale arco verrà utilizzato (per 2 punti possono passare fino a 4 archi distinti. la combinazione di questi due valori permette di scegliere quale usare.)
![[SvgArcFlags.png]]

Grazie al Path è possibile costruire percorsi che possono essere animati.