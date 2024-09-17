Il contesto di solito arriva sempre dopo come tempistiche rispetto a un routing (fatto per es da un oauth)

Conviene pertanto rimandare come url di callback sulla login e poi impostare uno useEffect sul token, con redirect quando è stato valorizzato dal contesto.

```Javascript
const manageToken = function (){
        // recupero l'eventuale token dall'url (ricevuto da un login oauth)
        const objUrlParams = new URLSearchParams(window.location.search)
        const urlToken = objUrlParams.get('token')
        // verifico se è presente un token nel localstorage
        const storageToken = localStorage.getItem('token')
        // se c'è il token nell'url uso quello perchè è di sicuro il più recente
        if(urlToken){
            setToken(urlToken)
            localStorage.setItem('token', urlToken)
        }
        // se non c'è nell'url, ma c'è nello storage, allora considero quello
        if(!urlToken && storageToken){
            setToken(storageToken)
        }
    }
    useEffect(manageToken, [])
```