Per applicare il layout model Flex, devo costruire un contenitore così: 
```html
<div style="display: flex">
</div>
```
Tutti i ==figli diretti== di questo contenitore saranno flex-item

Gli elementi in un flex-container si spalmano su un asse chiamato main axis. Quando raggiungono il fondo, si espandono sull'altro (cross axis).

È possibile specificare la flex-direction come proprietà nel foglio css.

Il default è row (quindi mi sviluppo prima orizzontalmente e poi verticalmente)

**Justify-content: permette di allineare gli elementi in base all'asse principale (ci sono varie opzioni)**

**align-items: permette di allineare gli elementi, *su una singola riga*, in base al cross axis (anche qui varie opzioni)** 
	- flex-start parte dall'alto (o sx) del main axis a disporre le cose. I singoli item si estendono in base ai loro contenuti
	- Baseline allinea i blocchi in base al testo che hanno all'interno

align-content: permette di allineare gli elementi sul cross axis, *nel caso ci siano più righe di item, e ci sia flex-wrap*

flex-wrap: fa andare a capo gli elementi alla riga successiva. Se non c'è, cerca di mettere più elementi possibile sulla stessa riga

align-self: da mettere su un flex-item, per cambiare solo la sua proprietà align-item
order: da -n a -n da mettere su un flex-item, indica in che ordine devono essere posizionati nella direzione del main-axis. Stesso numero, l'ordinamento è quello dell'html

Cheat sheet
https://css-tricks.com/snippets/css/a-guide-to-flexbox/

Training
https://flexboxfroggy.com/#it
https://flukeout.github.io/
https://mystery.knightlab.com/