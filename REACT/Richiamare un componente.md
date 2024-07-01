
Componente
```javascript
// css specifico per questo componente

import './App.css';
function App() {

  return (
		// cose
  );
}
```

```javascript
import React from 'react';
import ReactDOM from 'react-dom/client';
// file css che agisce sull'applicazione
import './index.css';
// importazione del componente App, che è posizionato nella cartella components, ed è un file che si chiama App.js (l'estensione è trascurabile)
// se un componente ha più export e non ho messo un default, devo mettere il nome del
// componente tra graffe (import {ComponenteTest} from ...)
import App from './components/App';
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
	// tag vero e proprio
    <App />
);
```