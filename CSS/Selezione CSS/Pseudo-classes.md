Elenco: https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes#user_action_pseudo-classes
Sono classi che si attivano in certi momenti per gli oggetti. Per es:
* active
* hover
```CSS
/*così sto specificando il comportamento quando si fa hover sul blocco*/
h1:hover{
	color: red;
}
```
* focus
* link (link non ancora visitati)
* visited (link già visitati)
* first-child
* last-child
* nth-child(n) (posso dargli anche odd o even, per selezionare elementi alternativamente)
* empty
* first-of-type
* last-of-type
* nth-of-type
* not (nega il contenuto)
* has (se le condizioni tra le parentesi sono verificate, allora formatto l'elemento)
Sono molto comode per modificare il comportamento specifico di un elemento, senza dover andare a toccare l'html