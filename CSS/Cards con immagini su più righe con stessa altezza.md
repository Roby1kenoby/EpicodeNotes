
Contenitore
```HTML
<div id="cardsContainer" class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 d-flex align-items-stretch">
	<!-- Qui ci metterò le cards. Uso align-items-stretch per far si che prendano tutto lo spazio in altezza -->
</div>
```

Card
```HTML
<div class="imgWrapper d-flex">
        <img src="${book.img}" class="album-img card-img-top" alt="${book.title}">
</div>
<div class="myCardBody">
	<div class="topInfo">
		<button class="btn btn-success" onClick="...">Buy</button>
	</div>
	<div class="bottomInfo">
		<a href="./dettagli.html?id=${book.asin}">
			<p class="title card-title">${book.title}</h5>
		</a>
		<p class="genreAndPrice"><span>${book.category}</span></p>
	</div>
</div>
```

CSS
```css
#cardsContainer{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: start;
}

.myCard {
    border: 1px solid black;
    border-radius: 0.5em;
    height: 100%;
    padding: 0;
    z-index: 0;
    /* questo mi serve per avere elementi sottostanti che possano avere position absolute*/
    position: relative;
}
/* questo è per far si che l'immagine occupi una larghezza fissa*/
.imgWrapper {
    width: 100%;
    height: 70%;
}

.myCard img{
    border-radius: 0.5em;
    /* questo fa si che l'immagine copra la superficie del div. Va bene se le imm non sono troppo diverse come dimensioni*/
    object-fit: cover;
    overflow: hidden;
    z-index: 0;
}
```