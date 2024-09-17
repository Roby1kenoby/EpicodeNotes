Per farmi rilasciare client e secret, devo andare su https://console.cloud.google.com/welcome poi creare un progetto.
Vado poi alla voce Credenziali, e seleziono crea credenziali id client oauth.

Configurare poi la schermata di consenso, per far si che quando l'utente si logga vengano fuori le informazioni di consenso (nome dell'app, tipo di info richieste ecc)

1) UserType: Esterno (mi permette di condividere l'app con chiunque)
2) Configurare le altre info che compariranno nella schermata (quelli obbligatori)
	1) Nome
	2) Info sviluppatore
3) Poi aggiungere gli ambiti, cioè i dati dell'utente che vengono presi da google (selezionare solo i sottostanti)
	1) Email
	2) Profile
4) Aggiungo poi utenti di prova, e saranno gli utenti che possono collegarsi all'applicazione

A questo punto posso tornare indietro e posso cliccare di nuovo su crea credenziali, poi Crea ID client OAuth.

Definisco quindi il tipo di applicazione (applicazione web nel nostro caso), Nome ecc.

Aggiungi Uri di reindirizzamento autorizzati, e ci metto l'url di reindirizzamento (http://localhost:porta/api/v1/auth/callback-google)

Faccio crea e finalmente ottengo l'id client e l'id secret da mettere nell'env




