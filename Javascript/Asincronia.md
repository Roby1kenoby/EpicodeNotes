Lanciare una o più chiamate assieme, loro lavorano in background e poi ne elaboro i dati.
Possiamo gestire le chiamate asincrone in 3 modi:
- Callback: passaggio di una funzione come parametro ad un'altra funzione.
	Viene eseguita come prima cosa la funzione chiamante (che può essere per esempio una chiamata a dati esterni, oppure anche solo una funzione normale, tipo generare un array di numeri, non ha importanza). Dopo di che, si attiva la funzione di callback, che potrà utilizzare eventuali dati generati dalla prima funzione. 
	Diciamo che le callback vanno bene se ho poche cose da gestire, perché per ogni chiamata devo gestire sia il successo sia il fallimento. Se ne ho tante, devo indentare mille volte con degli if per gestire eventuali errori.
- Promise: Promessa di fare qualcosa che può restituire una Response che può contenere (vedi [[Promise-Resolve]])
	- pending
	- successo
	- fallimento
	Nel frattempo il resto del programma può fare altro.
	Quando una promise è risolta (a prescindere dal risultato) posso poi fare .then() e gestire le operazioni successive.
	Posso usare invece .catch() per gestire eventuali errori.
	Posso concatenare anche più then() per effettuare operazioni che dipendono l'una dall'altra. Infine posso anche usare .finally() per eseguire un'ultima istruzione al termine di qualsiasi cosa sia successa prima.
- Async/Await
	- Dichiaro una funzione come Async, e posso al suo interno usare la keyword Await per far si che i singoli passaggi attendano la conclusione del precedente.