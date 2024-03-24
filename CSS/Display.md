None nasconde gli elementi, e NON riserva loro dello spazio (al contrario di visibility:hidden)
```css
display:none 
```

Con inline, width e height non hanno effetto. Margini e padding applicati al blocco vengono interpretati male dagli elementi circostanti
```css
display:inline 
```

Permette di applicare width, height, margini e padding
```css
display:inline-block
```

Inline-block può essere utile per elementi li, messi in orizzontale, ma permettendo di inserire margini e padding tra di loro.