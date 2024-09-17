Quando creo un context, posso decidere di definire molte cose all'interno del file stesso, in modo da tenere le cose più separate, e il codice dell'app più pulito.

```JSX
import { createContext, useState } from "react";
export const BookContext = createContext()

export function BookContextProvider({children}) {
    const [selectedBook, setSelectedBook] = useState(null)
    const value = [selectedBook, setSelectedBook]
    return (
        <BookContext.Provider value={value}>
            {children}
        </BookContext.Provider>
    );
}
```

In pratica oltre a creare il BookContext, creo letteralmente un altro componente (funzione BookContextProvider), che come props ha children.
Children è una variabile placeholder che conterrà tutti i figli che avrà al suo interno il contesto.
value sono le props che i figli potranno consultare.

Richiamo poi così il context:
```JSX
import { BookContextProvider } from './components/BookContextProvider';
function App() {
return (
<BrowserRouter>
      <BookContextProvider>
        <MyNav selectedGenre={selectedGenre} setSelectedGenre={setSelectedGenre}
                searchInput={searchInput} setSearchInput={setSearchInput}

        ></MyNav>
		// altri componenti
      </BookContextProvider>
</BrowserRouter>
)}
```
E non devo più passare qui i value.

I figli, continuano a potere usare il [[context]] normalmente