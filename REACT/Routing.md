È necessario installare un componente apposito per gestire il routing, tramite npm.

npm i react-router-dom

Il routing è principalmente comodo per rendere più facilmente condivisibili le pagine.

Dopo aver installato, andare in App.jsx e sostituire nel return quello che c'è con il router
```JSX
<BrowserRouter>
	<Header/>
	<Container>
		<Row>
			<Col>
				<Routes>
					<Route path="/percorso" element={<Home/>} />
					<Route path="/percorso2" element={<About/>} />
					<Route path="/percorso3" element={<Contacts/>} />
					
				</Routes>
			</Col>
			<Col>
				<Sidebar/>
			</Col>
		</Row>
	</Container>
	<Footer/>
</BrowserRouter>
```

Dentro ci andremo a mettere tutta l'applicazione.
Le parti fisse dell'applicazione (header, side, footer ecc) andranno direttamente lì dentro.

Nella cartella del progetto components ci metto le parti fisse.
Mi faccio poi una cartella "pages" dove andrò a mettere i componenti delle singole "pagine"

Per richiamare i singoli path, ho un componente che si chiama Routes, all'interno del quale metto le singole Route, alle quali passo con props il componente, specificando il path e l'elemento.
(*attenzione, devo aprire le graffe per poter richiamare il componente, e devo anche importarlo! Posso metterci dentro anche più di un componente, o addirittura strutture miste con html e componenti, ma conviene tenere pulita la struttura e limitarsi ad un solo componente per route*)
```JSX
<Route path="/percorso2" element={<About/>} />
```

Per puntare a una route tramite link, non uso i normali link a con href, ma uso un componente apposito (Link). Va importato anche questo. 
```JSX
<Link to="/percorso2">Home</Link>
```

Per puntare a una route dinamicamente (Es, /posts/numeroCheCambiaAdOgniPost) devo impostare un parametro che vari. Per indicare qual è, utilizzo i due punti.
```JSX
<Route path="/posts/:id/:author" element={<Post/>} />
```

All'interno del singolo componente generato tramite il route.
useParams è una funzione che ci restituisce tutti i parametri definiti nella Route (id e author, per esempio)
```JSX
import {useParams} from "react-router-dom"
	function Post(){
	const {id, author} = useParams();
	return{
		<div>Sono il posto con id {id} </div>
	}
}
```


Conviene sempre fare anche un route verso un componente NotFound.

Per farlo, il path è to='/\*'
