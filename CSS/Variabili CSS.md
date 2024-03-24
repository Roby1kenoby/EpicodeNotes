Esiste una pseudo classe chiamata :root in cui posso inserire delle variabili.


```css
:root {
	/* per convenzione le variabili si chiamano così --nomevar*/
	--primary-color: #ff6384;
	--secondary-color: #36a2eb;
}
```
Posso poi usare tale variabile come valore così:
```css
.square{
	background-color: var(--primary-color);
}
```
Posso usare qualsiasi contenuto per una variabile.