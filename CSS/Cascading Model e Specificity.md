![[Specificity.png | 500]]

Le regole del CSS sono applicate a cascata.
Se due selettori applicano regole allo stesso elemento (classe\\tag ecc) vince quello più in fondo.

Se però do ad un oggetto una classe, e poi applico del css a quella classe, anche se sta PRIMA delle regole applicate via tag, quella della classe ha una specificità maggiore e prevale.

Specificità Tag Base
![[SpecificitàTagBase.png]] 
Specificità Classe
![[SpecificitàClasse.png]]
La Specificità di una regola richiamata tramite id è ancora più forte della specificità di classe
![[SpecificitàId.png]]
Infine, le modifiche inline sono a specificità massima, prevaricano qualsiasi altra regola impostata

Come trucco (sconsigliato, perchè non è pulito) posso fare così:
```html
<head>
	<style>
		selettore { proprieta: valore;}
		// il cancelletto si usa per indicare che il selettore è un id
		#special-content {
			padding: 12px !important;
		}
	</style>
</head>
```
Il comando !important manda alle stelle la priorità di una regola, ma si ha il rischio di far sbroccare tutto

