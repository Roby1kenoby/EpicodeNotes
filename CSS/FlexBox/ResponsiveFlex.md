Con la combinazione di [[Flex-Grow]], [[Flex-Shrink]] e [[Flex-Basis]] (assieme a flex-wrap) posso allineare in maniera responsive gli elementi.

Es:
```html
<div id="container">
	<div>
		<h2>Titolo 1</h2>
	</div>
	<div>
		<h2>Titolo 2</h2>
	</div>
	<div>
		<h2>Titolo 3</h2>
	</div>
	<div>
		<h2>Titolo 4</h2>
	</div>
</div>
```

```css
#container{
	display:flex;
	flex-wrap: wrap;
}

#container div{
	flex-grow: 2;
	flex-basis: 50%;
}
```

Il risultato sono 4 container che prendono il 50% dello spazio a disposizione, quindi verranno posizionati 2 su una riga, e poi per il wrap, 2 sulla riga successiva.