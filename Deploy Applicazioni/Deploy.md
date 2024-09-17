https://render.com/ per il backend (vedi [[Render]])
https://vercel.com/  e https://www.netlify.com/ per il frontend. (vedi [[Vercel]])

C'è anche gitHub pages, che però prevede che la repo sia pubblica

Sul backend è necessario gestire il [[CORS]]

È importante prima di tutto cercare nel file del backend eventuali riferimenti al localhost, in modo da andare a trovare dove sono e ==sostituirli con riferimenti al file env==.

Stessa cosa per il frontend, ricercare gli indirizzi statici e sostituirli con variabili prese da .env.local (messo nella root del progetto)!
Con Vercel, non è necessario avere il file env.production, perchè tanto i dati li metteremo nell'interfaccia di Vercel.
Per gli url, prendere la parte base (se ho /api/v1, non prendere questa parte perchè domani le api potrebbero essere v2)

Info utili Deploy:

- Non usare indirizzi statici
Backend
- Check di non avere link al localhost, ma sostituirli con variabili dell'env
- Aggiungere nel file .env e .env.example la chiave FRONTEND_URL
- Durante il deploy sistemare i valori delle chiavi nei fil .env e inserirli nell'interfaccia del deploy (HOST, PORT, FRONTEND_URL)
Frontend
- Check di non avere link al localhost, ma sostituirli con variabili dell'env
- Non è necessario importare 'dotenv/process' nel frontend
- Aggiungere nel file .env.local e .env.example la chiave ===REACT_APP_API_URL (è l'url del backend, attenzione, è necessario proprio chiamarla così per obbligo da parte di create react app=== 
- Le chiavi, in generale, devono tutte avere REACT_APP_ come prefisso
- Durante il deploy sistemare i valori delle chiavi nei fil .env e inserirli nell'interfaccia del deploy (REACT_APP_API_URL e CI:false)
- Per eventuali logon provider (google ecc), ricordarsi di aggiungere l'url del backend come autorizzato.