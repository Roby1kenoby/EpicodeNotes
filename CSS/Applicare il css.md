Per applicare CSS posso usare l'attributo style direttamente nei tag (inline styling)
```html
<h1 style="proprietà: valore"></h1>
<h1 style="margin: 0"></h1>
```
Questo metodo ovviamente non è molto ideale a livello di manutenibilità
In alternativa, nel tag head, posso scrivere un tag style
```html
<head>
	<style>
		selettore { proprieta: valore;}
		// il selettore indica che tag verranno interessati dalla modifica
		// em sta per dimensione standard del font
		p {font-size: 1.2em;}
		// virgola tra tag per applicare stesse regole su più elementi
		h1, h4 {
			margin: 3em;
			background-color: black;
		}
	</style>
</head>
<body>
	<h1>Titolo</h1>
	<h2>Sottotitolo</h2>
</body>
```
Infine, posso referenziare un file .css nel progetto (o tramite url) direttamente nell'header
```html
<head>
	<link rel="stylesheet" href="nomefile.css"/>
</head>
```

Come selettore posso anche scegliere di usare una classe
```html
<head>
	<style>
		selettore { proprieta: valore;}
		// il punto dice "seleziona TUTTI gli elementi nella pag con quel nome"
		.content {
			padding: 12px;
		}
	</style>
</head>
<body>
	<h1>Titolo</h1>
	<div class="content">
		//contenuto
	</div>
</body>
```
Infine, posso scegliere di usare un id
```html
<head>
	<style>
		selettore { proprieta: valore;}
		// il cancelletto si usa per indicare che il selettore è un id
		#special-content {
			padding: 12px;
		}
	</style>
</head>
<body>
	<h1>Titolo</h1>
	// ATTENZIONE: Gli id devono essere univoci
	<div id="special-content">
		//contenuto
	</div>
</body>
```
Per i livelli di potenza, vedi [[Cascading Model e Specificity]]