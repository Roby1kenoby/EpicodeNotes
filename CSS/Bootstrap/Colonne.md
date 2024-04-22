Di base, classe col è una classe display flex che cerca di occupare più spazio possibile dal proprio container.

Posso poi dare dimensioni alle colonne cambiandone la classe (es. col-6 è una colonna che prende il 50% della row). In questo caso, andranno a wrappare in caso di overflow rispetto ai 12 slot a disposizione.

*Conviene sempre completare i 12 spazi a disposizione, non lasciarne di vuoti*

Per rendere le colonne responsive (si muovono in base alla dimensione della viewport), devo invece usare il seguente formato:

```html
<div class="col-lg-6 col-xs-12">
	// content
</div>
```
In pratica, per dispositivi da large in su (in base ai break-point), la colonna deve occupare 6 slot, se invece da lo schermo è piccolo, fino a large, allora ne deve occupare 12.
