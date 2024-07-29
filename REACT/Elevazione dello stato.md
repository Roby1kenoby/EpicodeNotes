Non è possibile far passare dati da un figlio ad un altro figlio, o da un figlio ad un padre.
Allora, "elevo" lo stato del componente al primo componente comune a tutti quelli che devono condividere quello specifico stato.

Non posso neanche saltare dei passaggi di componenti, purtroppo, devo proprio partire dall'alto e passare lo stato scendendo fino al componente più in basso che deve poter modificare lo stato

![[Pasted image 20240708193256.png]]

Eventualmente posso anche fare funzioni nel componente padre, e poi passarle ai figli come props.
*Una funzione può anche richiedere parametri. Al componente nel componente padre, passo solo il nome della funzione. Nel componente figlio, poi, quando richiamo la funzione, gli passerò il parametro*
Se la funzione non richiede parametri, quando è richiamata nel figlio la scrivo senza arrow function (perchè sto passando una definizione).
Se richiede parametri, invece, arrow function per poter passare anche i parametri