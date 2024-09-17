Metto cose dentro al Context, e quelle cose sono recuperabili da tutti i figli ed i figli dei figli ecc.

Mi permette quindi di evitare la catena delle props ( props - drilling: passare la prop a un componente anche se non gli serve, solo perché serve al suo figlio)

==Evitare di mettere il context troppo in alto, ma metterlo dove avremmo messo lo stato elevato. Questo perchè, se lo metto al padre principale, ogni cambiamento renderizza nuovamente tutti i componenti che accedono al context, e quindi rirenderizzerei tutta l'app==

==Il context deve sempre stare ad un livello superiore rispetto a dove devo utilizzarlo. Se devo usarlo in App, lo metto in index==
Il provider fornisce il contesto. I consumer sono quelli che lo utilizzano.

Conviene crearsi il provider in un file a parte (es Context.jsx)
e al suo interno possiamo creare più contesti, affinché vengano usati solo nei componenti in cui servono.
```JSX
import {createContext} from "react";

export const CounterContext = createContext()

export const UserContext = createContext()

```
Il contesto si usa come un componente.

```JSX
function App(){
	const [counter, setCounter] = useState(0);
	return{
		<div>
			<CounterContext.Provider value={[counter, setCounter]}>
				// altri componenti che hanno bisogno di questo contesto. I figli di questi componenti avranno anche loro accesso a questo contesto
			</CounterContext.Provider>
		</div>
	}
}
```
*Posso anche mettere più context annidati l'uno dentro l'altro, se i componenti all'interno del primo hanno anche bisogno del secondo*

Nel value del contesto, passo tutto quello che voglio che sia accessibile ai componenti figli.
Posso passare qualsiasi cosa, array, oggetti, variabili ecc. *Se devo passare più di una cosa, devo racchiuderle in array o oggetti.*

```JSX
import {useContext} from "react";
function Display(){
	// recupero dall'array che mi restituisce useContext il primo valore e lo metto in una variabile che si chiama counter
	const [counter] = useContext(CounterContext)
}
```
vedi [[CheatSheet JS Moderno]] per dettagli sul modo in cui viene recuperata la variabile counter.

*In genere, cercare di mettere una sola variabile in un singolo contesto. Cercare anche di non passare variabili di nature diverse in un solo contesto, perchè così riduco la riusabilità del contesto*

[[Context in un file separato]]