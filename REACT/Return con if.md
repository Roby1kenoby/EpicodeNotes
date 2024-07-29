In un componente react, posso avere più return, l'importante è che li gestisca con delle if.
Se il primo IF è vero, avviene il primo return e di conseguenza il secondo non viene considerato.

```JSX

if(caricamento)
	return(
		// cose
	)
return(
	// altre cose
)
```
Potrei avere n condizioni tutte nello stesso componente e gestirle così.