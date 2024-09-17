Su login, il backend verifica la presenza dell'utente sul db, verifica la correttezza (tramite hash) della password, e quindi genera un token identificativo per l'utente.

Gli accessi alle rotte vengono poi gestiti tramite questo token, che viene salvato nel local storage, e non tramite la password dell'utente.

In [[JWT]] (Json Web Token) i token si fanno scadere. Con le sessioni invece si eliminano quando necessario dalla tabella sul DB che li contiene.
