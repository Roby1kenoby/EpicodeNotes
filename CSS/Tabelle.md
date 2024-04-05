Posso impostare per le tabelle dei gruppi di colonne, per facilitarne il dimensionamento
```html
<table>
	<colgroup>
		<col class="thirty">
		<col class="seventy">
	</colgroup>
	<thead>
		<th>Location</th>
		<th>Job Description</th>
	</thead>
	<tbody>
	</tbody>
	<tfoot>
	</tfoot>
</table>
```
Così la colonna thirty avrà larghezza 30% della tabella
```css
table{
    /* table-layout: fixed; */
    width: 100%;
}
td{
    border: 1px solid black;
    padding: 0.5em 1em 0.5em;
    min-width: 10em;
}
.thirty{
    width: 30%;
}
.seventy{
    width: 70%;
}
```