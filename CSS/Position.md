Di base, tutti gli oggetti hanno posizione static (renderizzati dall'alto verso il basso, non risente delle proprietà left,right,top,bottom ecc)
Esistono poi
* Relative - l'oggetto è spostato in base alla sua posizione predefinita (top bottom left right sono distanze che posso applicare, tipo top: 30px vuol dire posizionati a 30 pixel dall'alto)
* Absolute - l'oggetto è spostato in base alla finestra (uso top bottom ecc come sopra)
* Sticky - ha una posizione specifica, ma si fissa raggiunta una determinata posizione
* Fixed - l'oggetto è spostato in base al viewport (parte visibile della finestra del browser) L'elemento rimane fisso anche se i contenuti scrollano altrove (buono per header\\sidebar\\navbar fissi)

se metto in un oggetto relative, un oggetto absolute, l'absolute sarà posizionato in base alle dimensioni e posizioni dell'oggetto relative, non alla pagina intera.

Per es relative\\absolute:
```css
.container {
position: relative;
width: 500px;
height: 300px;
}
.child {
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%)
}
```
nel child, gli dico di posizionarsi al 50 dall'alto e al 50 da sinistra. Però lui come riferimento ha l'angolo in alto a destra, quindi applico una trasformata con una traslazione del 50% sull'asse x e y dell'oggetto stesso
![[CentraturaConPosition.png]]
es. sticky.
quando l'elemento, scrollando la pagina, arriva alle coordinate top= 0px, si blocca lì e diventa fixed 
```css
position: sticky
top: 0px
```
**ATTENZIONE**
Se imposto un oggetto come sticky, e quell'elemento finisce fuori dallo schermo (es: imposto l'header sticky, e scrollo giù), anche l'elemento impostato come sticky sparisce.