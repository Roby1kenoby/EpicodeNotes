I combinatori combinano gli elementi del css, in modo da permettere l'accesso a qualsiasi elemento.

**Spazio**
seleziona gli elementi figli del primo elemento (.hero)
```css
.hero img{}
```

**No Sapzio**
sto concatenando i selettori, cerco un elemento che abbia TUTTI quegli elementi (in questo caso le due classi hero e bigger)
```css
.hero.bigger{}
```

**\>**
seleziono i figli DIRETTI dell'elemento
```css
.hero > p {}
```

**,**
concateno la selezione di più elementi (==attenzione, se ne canni uno, non funzionano tutti==)
```css
h1,h2,h3 {}
```

**+**
seleziono l'elemento del tipo indicato, direttamente attaccato all'elemento indicato SULLO STESSO LIVELLO
```css
.hero h2 + p{}
```
viene selezionato solo Subtitle, 2 e 3 no
```html
<div class="hero bigger">
	<h2>Section title </h2>
	<p>Subtitle</p>
	<p>Subtitle2</p>
	<p>Subtitle3</p>
</div>
```

**~**
seleziono gli elementi che si trovano SULLO STESSO LIVELLO, ma DOPO quello indicato
```css
.hero span ~ p{}
```
vengono selezionati solo Subtitle2, 3 e 4, perchè sono i p che stanno sullo stesso livello di span, dopo di lui.
```html
<div class="hero bigger">
	<h2>Section title </h2>
	<p>Subtitle</p>
	<span>Divider</span>
	<p>Subtitle2</p>
	<p>Subtitle3</p>
	<div>pippo</div>
	<p>Subtitle4</p>
</div>
```

