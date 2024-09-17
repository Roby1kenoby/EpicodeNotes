In pratica non gestiamo noi le password, ma Google, Facebook ecc.

![[Pasted image 20240902190845.png]]Dobbiamo prima registrarci con il provider oauth, che ci consegna una stringa secret.

Su login, il provider ci restituisce un id (che dobbiamo salvare nel db) ed altri dati (salvabili opzionalmente). Usare l'id come chiave, non la mail.

A questo punto possiamo creare il jwt, ma con il nostro ID (quello sul mongo). 

La fregatura è che il login così fa vari redirect, passo dal mio frontend al backend, che rimanda a google, che torna al mio backend. 

Per tornare al mio frontend, devo fare un redirect, ma l'unico modo che ho per farlo è usare una get, quindi il token jwt finisce nell'url e dovrò recuperarlo da lì.

Esiste una libreria che si chiama [[Passport]], (passportjs.org), che dovrebbe semplificare un po' le integrazioni con i vari provider.

