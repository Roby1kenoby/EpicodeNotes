
dotenv è per gestire l'environment lato server

npm i express mongoose dotenv

-D serve per installare nella liberia dev
npm i nodemon -D

poi creo file env con dentro
```env
PORT=5000
MONGODB_CONNECTION_STRING="mongodb+srv://Roby1kenoby:<password>@roby1kenobycluster.gobvtzr.mongodb.net/?retryWrites=true&w=majority&appName=Roby1kenobyCluster"
```

Preso dal mongodb Atlas, devo mettere la password in chiaro. Ricordarsi poi di mettere in git.ignore il file env.