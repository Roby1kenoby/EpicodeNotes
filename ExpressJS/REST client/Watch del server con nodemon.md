Installare la libreria nodemon

npm i nodemon

viene installato in node_modules.
In package.json, sotto scripts, aggiungo una stringa

```json
"scripts":{
	"dev": "nodemon server.js"
}
```

A questo punto, nel terminale posso scrivere 
npm run nomescript (dev) e questo parte.

Se il nome dello script è start, posso omettere run (npm start)

Per fare i test, vedi [[Testare chiamate API direttamente da VS Code]]