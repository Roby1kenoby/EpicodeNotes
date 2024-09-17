Useremo un middleware nominato multer per gestire questo tipo di richieste di salvataggio (in locale o in cloud).

Possiamo poi appoggiarci a servizi come Cloudinary per fare l'hosting delle immagini in cloud.

*Pacchetti da installare*
npm i multer cors helmet morgan

Helmet è un pacchetto che aggiusta gli header affinché il server sia più sicuro (rimuovendo dei dati dagli header).
Morgan è un logger che ci aiuta a visualizzare l'attività sul server

poi scrivo su server.js, 

import morgan from 'morgan'
// ecc altri import

app.use(morgan('dev'))
app.use(helmet())
app.use(cors())

Multer invece lo useremo nelle rotte specifiche che devono gestire file.

[[Esempio di middleware per upload in locale]]

[[Esempio di middleware per upload in cloud]]

