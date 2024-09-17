- Add New Project
- Collegarsi a GitHub
- Scegliere il progetto (fa visualizzare solo i progetti pubblici) e fare import
- Dargli
	- Nome
	- framework preset - Create React App
	- Root Directory - selezionare la cartella col frontend
	- Build and Output Settings
		- Build Command - npm run build (o il comando presente nel package.json)
		- Output Directory - Lasciare quello che c'è
		- Install command - npm install
	- Environment variables
		- Metto il puntamento all'url del backend (REACT_APP_API_URL="url rilasciato dopo il deploy del backend")
		- ==Impostare anche CI false== (rimuove dei warning del progetto che non lo farebbero compilare correttamente da parte di Vercel)
- A questo punto fare Deploy
Se torno nella dash, ottengo l'url del frontend

