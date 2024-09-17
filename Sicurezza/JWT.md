Sono stringhe, leggibili (pertanto non metterci dati sensibili), composte da 3 pezzi (separati da .)

Il primo è l'header, poi c'è il payload e poi la firma.

L'header contiene info sull'algoritmo utilizzato.
Il payload son le info che ci servono (non fare mai jwt che NON scadono, dargli sempre una data di scadenza, possibilmente corta, tipo una settimana).
La firma è l'hash di tutto quello che precede, + un secret (memorizzato sul server). Questo è quello che rende sicuro il jwt.

Il server quando deve controllare la validità del token: 
1) aggiunge il secret al fondo della stringa
2) verifica che l'hash calcolato sia corrispondente a quello ricevuto.

Per creare token jwt installare nel backend la libreria apposita
npm i jsonwebtoken

Vedi [[Esempio di CRUD]] per l'utilizzo

