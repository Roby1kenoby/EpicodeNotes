**Selettore di discendenza**
Applica lo stile su tutti gli elementi 3, figli di elementi 2, figli di elementi 1
```css 
elem1 elem2 elem3 {
}
```
**Selettore di classe composto**
Applica lo stile a tutti gli elementi che hanno le classi elem1, elem2, elem3
```css 
elem1.elem2.elem3 {
}
```
Posso avere anche le seguenti combinazioni:
```css
- elemento.classe: /*Seleziona gli elementi con la classe specificata.*/
- elemento#id: /*Seleziona un elemento con l'ID specificato.*/
```
(per elemento si intende un tag standard, tipo h1 ecc.)
**ATTENZIONE**!
Se non metto spazi, sto ricercando un elemento (es: div) che ha quella specifica classe o id
```css
div.class
div#id
```
Se metto gli spazi, sto cercando un elemento che ha la classe class o l'id id, all'interno di un div
```css
div .class
div #id
```

Posso fare dichiarazioni multiple così:
```css
#elem1, #elem2 .ciao{

}
```

Posso fare anche riferimento ad attributi 
https://www.w3schools.com/css/css_attribute_selectors.asp
Cerco tutti gli oggetti che hanno tag input, ma che hanno value = Inserisci (è case sensitive)
``` css
	input[value=Inserisci]
	input[type=text]
	input[name=pippo]
```
