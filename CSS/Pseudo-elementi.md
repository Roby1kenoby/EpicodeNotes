Usati per selezionare parti specifiche di elementi.
Si referenziano tramite ::
Come specifictà hanno stesso valore dei tag
* firstline
* after - permette di iniettare dopo ad un elemento roba che non è prevista 
```css
/*così aggiungo a tutti i link all'interno del tag nav un punto esclamativo al fondo. L'elemento non è interagibile dall'utente*/
nav a::after{
	/*il content è limitato a testo\caratteri ascii*/
	content: "!";
	/*
	Se a un elemento con position absolute metto top bottom left right: 0, è come dirgli width e height 100%
	*/
	position:absolute;
	top: 0;
	bottom: 0;
	left: 0;
	right:0;
}
/* posso anche attivare lo pseudo elemento assieme ad una pseudo classe*/
nav a:hover::before{
	content: "*!"
}
```
* before - come sopra, ma prima dell'elmento (questi elementi vengono usati per fare dei "trucchetti")
* marker
* selection - quando l'utente seleziona
