Il frontend raccoglie user (o mail) e pass in chiaro.
Poi una rotta (differenziare la rotta del frontend da quella del backend) raccoglie queste info, e il backend deve farci cose.

1) Verificare user già usato
2) Registrare l'utente

I dati passati al DB non saranno identici, perchè la password deve essere convertita e anonimizzata (è necessario fare l'[[hash]] della password tramite una funzione (bcrypt.hash("pass inserita dall'utente", nrDiGiriDiHash)))

A questo punto, quando l'utente si logga, io devo fare il confronto tra la pass inserita criptata con bcrypt, con quello che ho salvato sul DB (bcrypt.compare("password inserita dall'utente","passwordhashata recuperata da mongo").

Spesso, l'algoritmo di hash aggiunge quello che viene chiamato "salt", che sono pezzi di stringa aggiuntivi, generati da lui e salvati comunque nel db, per rendere le password più sicure.


