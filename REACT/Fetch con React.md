Esattamente come in JS posso usare async-await o promise.then

Per inizializzare uno stato che deve ricevere dati da fetch, posso o inizializzarlo con un array\\oggetto vuoto, oppure  posso cercare di distinguere tra non sono ancora arrivati i dati, oppure non ci sono dati nella risposta.
Posso quindi impostare a NULL lo stato iniziale, oppure gestire un altro stato booleano che inizia a true, e poi modificarlo a false quando ho ricevuto i dati.

