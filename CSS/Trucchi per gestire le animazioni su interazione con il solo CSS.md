Usare [[pointer-events]] e [[Pseudo-classes]] focus-within (assegno ad un elemento che normalmente non è focussabile un pointer event, e poi con la pseudo class seleziono il suo padre (che è quello che poi animo\\controllo))

In alternativa, posso avere un campo di tipo checkbox messo subito prima dell'elemento che voglio controllare (es una nav), e lo posiziono al di fuori della pagina.
All'interno del label collegato (usare i campi id del checkbox e il for nel label), inserisco le cose che voglio controllare.

```css
#idCheckbox:checked ~ .elementoCheVoglioTargettare{
	/* cose da animare*/
}
```
Il primo metodo è molto più "pulito"
