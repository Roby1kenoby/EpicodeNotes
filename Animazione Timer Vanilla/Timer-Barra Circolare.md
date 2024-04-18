La logica è la seguente:
1) Creo uno cerchio svg come base (è quello che compare man mano che si "consuma" il path che gli sovrapporremo)
2) Ci disegno sopra un path che lo copra completamente
3) Animo questo path, usando la proprietà [[stroke-dasharray]], modificandone il valore tramite javascript.

Esempio:

cerchio di base grigio, coperto poi da un path.
Il path fa:
M -> mi muovo alle coordinate assolute 100 100 (il svg è 200x200, quindi sono al centro)
m -> dalle coordinate precedenti mi sposto a x = 0, y= -80 (lo 0,0 è in alto a sinistra)
a -> creo un arco, di raggio x e y = 40 (circolare), che arriva fino a 0, 160 (sono all'apice del cerchio, l'arco scende fino al punto più basso). Non ruoto niente, e il mio arco deve fare 180 o più gradi vedi [[SVG]]
a -> dal fondo del cerchio, rifaccio la stessa cosa, ma tornando al punto più alto del cerchio.
```html
<div class="base-timer">
        <svg width="200px" height="200px">
          <circle class="base" cx="100" cy="100" r="80" stroke="grey" fill="transparent" stroke-width="10"/>
          <path id="timeRemaining"
          d="
            M 100, 100
            m 0, -80
            a 40, 40, 0 1,0 0, 160
            a 40, 40, 0 1,0 0, -160
            "
          />
        </svg>
        <span id="time">
          30
        </span>
      </div>
```

Base-timer è un contenitore generico per contenere il resto.
```css
.base-timer {
    position: relative;
    height: 300px;
    width: 300px;
    border: solid 1px black;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
/* questo mi permette di avere il numero di secondi nel centro del cerchio*/
.base-timer span{
  position: absolute;
}
 
#timeRemaining{
/* colore della riga */
  stroke: aqua;
/* riempimento trasparente */
  fill:  transparent;
/* larghezza della riga */ 
  stroke-width: 10;
/* forma della fine della riga */
  stroke-linecap: round;
/* transizione. Ci metto un secondo (perchè la eseguirò ogni secondo con il js) e considero tutte le proprietà  */  
  transition: 1s linear all;
}
```

```javascript
// tempo massimo
const timer = 10
// tempo passato
let timePassed = 0
// var per il timerInterval
let timerInterval = null
// container del testo per i secondi
let timerContainer = document.getElementById("time")
// container del path
let timeRemainingContainer = document.getElementById("timeRemaining")


function startTimer(){
	// funzione che scatta ogni secondo
    timerInterval = setInterval(() =>{
        timePassed += 1
        timeLeft = timer - timePassed
        // aggiorno la stringa con i secondi attuali
        timerContainer.innerHTML = timeLeft
        //richiamo la funzione di animazione del path
        setCircleDashArray()
    },1000)
}

// funzione che calcola lo stroke-dasharray
function setCircleDashArray(){
	// percentuale del tempo passato (5/10 secondi)
    let timePercentage = timeLeft / timer
    // questa operazione serve perchè l'animazione, quando il timer arriva a 0, non è al fondo, perchè ci mette ancora 1 secondo a finire (mentre il timer è già a zero. Allora distribuisco questo secondo su tutti gli altri secondi)
    timePercentage = timePercentage - (1/timer) * (1-timePercentage)
    // ho bisogno di sapere quant'è la lungehzza totale del path
    let totalLength = timeRemainingContainer.getTotalLength().toFixed(0)
    // calcolo la lunghezza attuale
    let actualDash = (timePercentage * totalLength).toFixed(0)
    // costruisco la stringa con i due valori
    let sdaString = `${actualDash} ${totalLength}`
    // setto l'attributo stroke-dasharray sul path
    timeRemainingContainer.setAttribute("stroke-dasharray", sdaString)
}
startTimer()
```