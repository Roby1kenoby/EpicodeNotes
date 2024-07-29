https://testing-library.com/docs/react-testing-library/cheatsheet

Necessario avere un file che si chiama setupTests.js con all'interno import '@testing-library/jest-dom';

- Unit Testing -> testo un singolo componente
- Integration Testing -> verifico che i gruppi di componenti funzionino tra di loro.
- End to end testing -> simulo una vera e propria interazione umana

Per testare, usiamo react-testing-library (già integrata in create-react-app).

Per creare i test, conviene ragionare come un utente, pertanto cercare cose del tipo il testo sui pulsanti ecc, al posto che fare verifiche su stati o context.

Gli script di test di solito sono strutturati così:
- Arrange (vengono montati i componenti per ottenere l'html del DOM, ma nel virtual DOM)
- Selection (Selezione dei componenti con cui voglio interagire)
- Act (interazione coi componenti selezionati - la libreria di test  simula le interazione)
- Assert (valutazione di ciò che è stato montato e se ha risposto correttamente ad eventuali interazioni)
[[Metodi di Selection per i Test]]

*Attenzione: gli alert non sono un componente della pagina, ma del browser, quindi non sono testabili!*

I file che vengono testati sono quelli che hanno .test nel nome.
Se voglio testare un componente, devo importarlo nel file .test.

La funzione test si aspetta due argomenti: una descrizione, per capire cosa è andato storto, ed una funzione di callback (nella quale faccio i passi indicati sopra)

==Importante! Se devo testare un componente a livello di integration, potrebbe aspettarsi un context, o delle props. È pertanto necessario importare come minimo il livello di applicazione in cui vengono generate le props, o in cui viene definito il contesto.==

```JSX
import {NomeComponente} from 'percorso'
import {render, screen} from '@testing-library/react'

// ottengo lo stesso effetto di test con it(), è più bello se scrivi in inglese i test
test('descrizione del test', () => {
	// rendering
	render(<NomeComponente />)
	
	// selezione
	const nomeVar =	screen.getByText(/testoDaTrovareConRegex/i)
	const elementoInteragibile = screen.getByText(/testoSpecifico/)
	
	// la i al fondo è per impostare case insensitivie. Il testo tra / è proprio per usare regex al posto che stringhe dirette

	// interazione, se serve
	fireEvent.click(elementoInteragibile)
	
	// verifica. Expect ha tanti metodi per verificare varie cose
	expect(nomeVar).toBeInTheDocument()

	expect(nomeVar).toHaveTextContent(/valoreAtteso/)
});

	// questo va bene se lo style è inline. 
	expect(nomeVar).toHaveStyle('background-color: red')

// Se voglio invece quello applicato tramite file css, devo usare altri expect

test('test2', () => {
	// nello stesso file posso mettere quanti test voglio
})
```

Per vedere gli output dei test automatici, apro un terminale e npm test o npm t. Lui macina un po' e poi ci indica quali e quanti son passati.

*Con questo comando i test sono in modalità watch, cioè si accorgono se cambia qualcosa e rieseguono il test.*

Nel terminale vengono restituiti anche il testo in html compilato e gli eventuali errori.

*In genere, si cerca di fare un file di test per componente, se possibile, ma dipende dal tipo di applicazione da testare.*

vedi [[Import per Test]]

