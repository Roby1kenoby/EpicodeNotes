Bootstrap divide i colori in primary, secondary, tertiary ecc.
Sono semantici, quindi vuol dire che determinano anche la rilevanza.

Questi sono poi modificabili al fine di cambiare rapidamente in tutto il sito i colori.

Per farlo devo andare a sovrascrivere le variabili di bootstrap. Per farlo, creo un mio foglio di stile, in cui vado a impostare in root le variabili che sono già utilizzate da bootstrap.

```css
:root{
	bg-primary-rgb: 240, 240, 140
}
```

**ATTENZIONE: il mio file css deve essere referenziato DOPO il link di bootstrap, così va a sovrascrivere. Inoltre, devo rispettare i tipi che vengono utilizzati dal foglio di stile (es rgb, o esadecimale per il colore)**

Elenco Variabili
https://getbootstrap.com/docs/5.0/customize/css-variables/

