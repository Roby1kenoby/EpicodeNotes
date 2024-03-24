Se ho più pagine con gli stessi elementi (link\\titoli ecc) ma voglio cambiarne lo stile in ognuna di esse, mantenendo però certe proprietà base, posso fare così:

```html
<!-- H6 nella pagina principale -->
<h6>Luoghi correlati</h6>
<!-- H6 in un'altra pagina -->
<h6 class="pian-della-regina">Luoghi correlati</h6>
```

```css
/* css della pagina principale*/
h6 {
    padding: 22px;
    margin-bottom: 0px;
    margin-top: 56px;
    color: white;
    border-radius: 6px;
    background-image: linear-gradient(#004D81, #0A0B20);
}
/* stesso file css, ma punto all'elemento che ha una specifica classe*/
h6.pian-della-regina {
    background-image: linear-gradient(#4E786E, #76A639);
}
```
In questa maniera, nella pagina 1 ho tutte le impostazioni indicate nel css all'h6.
Nell'altra pagina, ho le stesse impostazioni, ma faccio un override della proprietà background image.

