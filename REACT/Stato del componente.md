Se renderizzo un componente tramite una condizione booleana, quando sparisce dal dom, viene proprio distrutto (smontato) e tutto quello che conteneva viene perso (eventuali varaibili ecc).

```JSX
return{
	variabileBool && <Componente />
}
```

