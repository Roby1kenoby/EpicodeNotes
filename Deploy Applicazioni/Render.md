- Deploy a web service
- Colleghiamo la repo di github
- Scegliamo il progetto, poi clicchiamo connect
- A questo punto gli diamo un 
	- nome, 
	- linguaggio Node, 
	- Branch (potenzialmente sarà sempre il main), 
	- Region meglio europa, 
	- Root directory vuota
	- Build Command: comando per installare le librerie -> cd backend && npm install
	- Start Command: prendiamo il comando di avvio presente in package json (in genere sarà "start": "node server.js") ->cd backend && npm start (in base al progetto, mi sposto nella cartella dove ho la root del progetto), poi collego il comando successivo con &&, che è quello che fa partire il server
	- Instance type: Free (se il server non è attivo per un po', lo spegne, quindi al primo avvio sarà lento).
	- Environment Variables (posso importare un file ENV, conviene farsene uno che si chiami .env.prod. con i dati di produzione. ==Ricordarsi di metterlo in git ignore==)
		- Nella configurazione dell'env su Render dovrò sistemare i valori di 
			- HOST: indirizzo del backend pubblicato
			- PORT: 80 o 443 in base al tipo di http
			- FRONTEND_URL: indirizzo del frontend pubblicato
	- Faccio quindi Deploy.
	- In environment dovrò poi modificare i parametri indicati sopra.

Lui macina, installa cose ecc, e alla fine restituisce in alto a sx l'indirizzo a cui risponderà il server.

Se ho fatto una modifica del codice sul server, e poi committo la modifica su git, quando faccio push in automatico si rideploya.