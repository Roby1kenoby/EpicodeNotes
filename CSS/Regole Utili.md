* Width: x% -> la percentuale è ==basata sull'elemento padre== (un div, container ecc). Quindi se questo cambia, cambierà anche l'elemento cui applico width in percentuale
* Posso importare font così:
```html
<style>
	@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
	body {font-family: 'Roboto', sans-serif;}
</style>
```
Andando su https://fonts.google.com/ posso cercare il font, selezionare i pesi desiderati e farmi costruire la riga di import
![[ImportFont.png]]
L'import conviene metterlo come prima cosa nell'attributo style
* max-width: 400px -> permette di avere un elemento che a pagina intera occupa cmq non tutta la pagina ma solo una parte, e poi si adatta in caso di riduzione della dimensione dello schermo
* margin-left: auto + margin-right: auto -> due tag separti, mi permettono di centrare un elemento al centro del proprio contenitore (posso ottenere lo stesso risultato con margin: 0 auto; 0 è per il sopra e sotto, auto per destra e sinistra)
* background-image: url("http:\\\\url.jpg") -> per mettere un'immagine come background di un div
* background: linear-gradient(direzione, colore1, colore2) -> per colorare da un colore all'altro. Posso avere degli stop point (dopo al colore) per indicare da dove a dove deve cambiare (rosso 25% blu 50% ecc)
* cheat-sheet: https://2019.wattenberger.com/blog/css-cascade
* In genere, la width conviene darla in misure relative (em,% vh) mentre la height non limitarla.
* Conviene sempre resettare il css come prima cosa (vedi [[Risorse Utili]]) Eventualmente si arriva ad avere un proprio modo di resettare le cose
