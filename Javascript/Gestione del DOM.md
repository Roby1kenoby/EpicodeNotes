Per selezionare oggetti dal dom posso fare così:
```javascript
document.getElementById("idPippo") //l'id deve essere univoco
document.getElementByClassName("classPippo") //restituisce tutti gli oggetti della classe specificata (array)
document.getElementByTagName("div") //restituisce i nodi del tipo specifico (tag) (array)
// IN GENERALE, QUELLI SOPRA SONO PIù PERFORMANTI, QUELLI SOTTO MENO, MA PIù COMODI
node.children //restituisce i figli di un nodo specifico
document.querySelector("body li") //restituisce il primo nodo che corrisponde al selettore CSS specifico. Con query posso proprio usare le modalità di selezione di css
document.querySelector(".classe.li")
document.querySelector("#idClasse")
document.querySelectorAll("div") //restituisce tutti gli oggetti che hanno uno specifico selettore CSS
```
Una volta ottenuti, posso farci cose (leggere\\modificare proprietà, richiamarne metodi ecc)

Per richiamare funzioni dal DOM
```html
<input type="button" value="Click me!" onclick="myFunction()" />

<button onclick="myFunction('parametri')">Click me!</button>
```

Per aggiungere elementi al DOM, prima li creo [[Esempio Modifica del DOM da JS]]
```javascript
let newDiv = document.createElement("div")

newDiv.innerText = "Ciao"
newDiv.style.color = "red"
newDiv.id = "new-div"
```
Poi li piazzo
```javascript
let body = document.querySelector("body")
// questo mette newDiv come ultimo discendente dell'elemento selezionato dal query selector
body.appendChild(newDiv)
//in alternativa, containerNode è il padre, newNode viene inserito subito prima di subsequentNode
containerNode.insertBefore(newNode, subsequentNode)
```

```javascript
newDiv.innerHtml //prende il contenuto html del tag
newDiv.innerText //prende solo il testo visibile
newDiv.textContent //prende il testo senza formattazioni
```

