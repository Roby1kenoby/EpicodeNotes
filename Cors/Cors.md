Cors è una protezione del browser che impedisce le fetch tra un dominio e l'altro per sicurezza.
In pratica evitiamo che il nostro backend funzioni solo col nostro frontend.

Normalmente i miei domini (front e back) sono diversi (es: 3000 e 3001). Il browser blocca eventuali richieste dall'uno all'altro.

Cors (è un [[Middleware]]), va messo nel file sul backend [[ExpressJS]] e gli dice, se non specifico nulla nella funzione, di comunicare con chiunque.

https://expressjs.com/en/resources/middleware/cors.html

file Server.js
```Javascript
// in fase di test abbiamo scritto così, che è un'applicazione globale e permette tutte le richieste
app.use(cors())

// se vogliamo limitare le richieste, possiamo passargli un oggetto di configurazione. Vedi nel link sopra config con origini dinamiche

// questa è la lista degli url accettati
var allowlist = [process.env.FRONTEND_URL]
// quando arriva una richiesta, la intercetta, e verifica se c'è nell'elenco allowList.
var corsOptionsDelegate = function (req, callback) {
  var corsOptions;
  // se c'è, allora origin:true, altrimenti false
  // !origin permette di far funzionare le chiamate server-to-server tipo le autenticazioni oauth con priveder tipo google
  if (allowlist.indexOf(req.header('Origin')) !== -1 || !origin ) {
    corsOptions = { origin: true } // reflect (enable) the requested origin in the CORS response
  } else {
    corsOptions = { origin: false } // disable CORS for this request
  }
  // infine usa la funzione next per passare allo step successivo.
  callback(null, corsOptions) // callback expects two parameters: error and options
}

app.use(cors(corsOptionsDelegate))
```

