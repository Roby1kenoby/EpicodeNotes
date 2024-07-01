Il "." è il percorso del progetto (punto è cartella corrente del terminale)
```terminal
npx create-react-app .
```

Se non è ancora stato installato il framework una prima volta sulla macchina, è necessario installarlo con
```terminal
npm i -g create-react-app
```
(vedi comandi [[NODE]])

Fatto lo scaffolding, vengono create una serie di cartelle e file nel progetto. 
- NodeModules sono le librerie necessarie scaricate.
- package.json contiene tutte le indicazioni per npm affinché scarichi tutte le librerie che ci servono.
- La lista completa è in package-lock.json
- Public è la cartella che contiene contenuto statico dell'applicazione 
	- robots.txt per es indica come devono comportarsi i crawler sul sito
	- index.html (non andremo praticamente mai a modificarlo. In pratica, quando faccio la build dell'app, ci verranno piazzati dentro i rif ai file css e js, ma il resto rimane vuoto, popolato poi dal Js.
	- In genere ci andrò anche a mettere eventuali elementi che hanno bisogno di un indirizzo fisso (es immagini ecc)
- src è la cartella in cui lavoreremo.
		- index.js è il punto di partenza dell'applicazione.
			- ==Da questo file, eliminare il tag React.StrictMode per evitare problemi in fase di test (duplica le chiamate)==

Fare sempre una cartella components in cui andremo ad inserire i file dei nostri componenti.
*NON fare una sottocartella per componente, (farsi rispiegare perchè no)*

**I nomi dei file js dei componenti devono essere con l'iniziale maiuscola, e il nome (per convenzione) deve essere uguale al nome del componente.**

Se ho bisogno di reinstallare i NodeModuls, è sufficiente fare nel terminale npm install e npm si occupa di riscaricare tutto quello che serve a partire dai file json indicati sopra.



