È un framework molto leggero per la creazione di backend in NodeJS
Mongoose è una libreria per interagire con MongoDB

Il client fa le richieste, expressJS analizza la richiesta e poi fa la relativa operazione CRUD sul DB.

Dovrò installare express con npm, e poi posso usarlo nei progetti

npm i express

*conviene installare anche i seguenti moduli: npm i express dotenv mongoose cors. Dopo di che, nodemon -D [[Integrazione progetto con Mongodb | per integrare il mongoDB]]*

Per inizializzare un progetto,
npm init -y 

(-y da si a tutte le domande successive).

questo crea il file package.json

aggiungere poi dentro "type": "module" per fare si che l'importazione delle librerie non si basi più sul require (metodo vecchio) ma con l'import (nei file js)

A questo punto, posso creare il file (tipo server.js). Sostituisco poi in package.json alla voce main quello che c'è col nome del file che ho appena creato

Conviene anche creare il git.ignore, e mettiamoci dentro node_modules e il file .env

A questo punto creo il file [[File server.js]]
