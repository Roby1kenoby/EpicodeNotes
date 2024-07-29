IMPORTANTE: va creato nella root del progetto.
È possibile chiamarlo .env e basta, ma in quel caso inserirlo nel git ignore.
Buona pratica è poi inserire un file .env.example da pushare, con il modello dell'env da compilare (con i dati del singolo sviluppatore)

Le chiavi nell'env devono iniziare tutto per REAC_APP_NOMEMIAVARIABILE
```JSX
REACT_APP_KEY=valore
REACT_APP_KEY2=altroValore
REACT_APP_KEY3="valore con spazi"

```

per usare i file env in qualsiasi file:
```JSX

{process.env.REACT_APP_KEY}
```

Se modifico il file env, devo riavviare lo npm start per far ricaricare le variabili