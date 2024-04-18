Disposizione degli elementi ottimale in base alla grandezza dello schermo.
Devo cercare di sviluppare un unico html e regole css che vadano bene a prescindere dal dispositivo.

Le media queries sono interrogazioni che vengono fatte al dispositivo per poi definire dei break-points (dimensioni alle quali cambiano le regole del css). Es: fino a 450px allora un set, da 450 a 1200 altre ecc.

```css
@media all{
	/*Tutte le regole scritte qua dentro, mi valgono per tutti i tipi di dispositivi e grandezze. Se non lo specifico, di default tutte le mie regole valgono per tutti i dispo.*/
}

@media screen{
	/*solo per visualizzazione su schermi. Se l'utente richiede una stampa del contenuto, è come se non avesse un foglio di stile*/
}

@media print{
	/*visualizzazione solo per i dispositivi di stampa*/
}

@media speech{
	/*per gli screen reader*/
}

@media screen and (min-width: 650px){
/*
	applico regole se siamo su uno schermo, e viewport largo almeno 650px
*/
}

@media screen and (min-width: 650px) and (max-width: 800){
	font-size: 1.3 rem
	/* quando passo a schermi più grossi, magari, aumento la dimensione del font*/
}

@media screen and (orientation: landscape){
/* orientamento dello schermo*/
}
```

In genere l'approccio è mobile first, si parte quindi da un dispositivo piccolo e poi si va a crescere. Questo perché la buona parte delle regole che vanno bene per un cell vanno bene anche per schermi più grossi.

Per abilitare sui dev tools di chrome la visualizzazione delle media queries
![[MediaQueries.png]]
