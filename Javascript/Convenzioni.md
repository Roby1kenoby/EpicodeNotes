Dichiaro variabili con let
Dichiaro costanti con const (variabile che non cambierà durante l'esecuzione del programma)
Usare camelCase.
Valore nullo è null
Java può essere richiamato 
* inline (usando eventi tipo onclick e poi scrivendo cosa fare)
* tra tag script come per il css 
* richiamandolo da altro file (**conviene metterlo al fondo del body**, perchè così la pagina viene caricata tutta, e poi vengono letti gli script che fanno cose sulla pagina)
``` html 
/*defer server se metto lo script nell'header, per far si che l'interpretazione avvenga in un momento più opportuno (cioè al caricamento completo della pagina)*/
<script defer src="percorsoalfile.js"></script>
// in alternativa, conviene piazzare i tag script al fondo della pagina, per far si che vengano letti dopo il caricamento di tutto il resto.
```

Tutto il codice che deve essere eseguito al termine del caricamento della pagina dovrebbe essere inserito in una funzione windows.onload.
Il rimanente, in altre funzioni che vengono richiamate tramite altri eventi.
```JavaScript
window.onload = function() {
	// tutte le mie funzioni che devono partire al termine del caricamento della pagina
}

//oppure ancora
window.addEventListener('load', function () {
	// scrivo qua dentro tutte le mie funzioni
})
```
