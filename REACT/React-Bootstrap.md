È necessario comunque installare [[bootstrap]] normale.

Documentazione: https://react-bootstrap.netlify.app/

Poi npm i bootstrap react-bootstrap (così installo sia bs sia react-bs)

Forse è possibile installarlo con -g per evitare di doverlo scaricare tutte le volte, tanto poi devo cmq fare la build del progetto.
Da Testare.

A questo punto devo andare nell'index.js e ci incollo 
import 'bootstrap/dist/css/bootstrap.min.css';

Per usare i componenti, non devo più usare le classi, ma è sufficiente richiamare i componenti

Al componente passo un prop con i parametri.
```jsx
import Button from 'react-bootstrap/Button';

<Button variant="primary">Primary</Button>{''}
```

L'oggetto dopo il button è ???

==Attenzione: quando importo i componenti di Bootstrap è necessario importarli dalla liberria. Inoltre, l'intellisense prende quello sbagliato, quindi è necessario importare a mano l'import indicato sul sito.==

Questa libreria ha comunque delle limitazioni, quindi a volte  è conviene magari usare bootstrap normale.