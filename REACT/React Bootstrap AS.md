Mi permette di trasformare un componente in un altro componente solo a livello estetico.

Per esempio

```JSX
<Button
	as={Link}
	to={'/posts/${post.id}'}>
Leggi
</Button>
```

Importante quando voglio usare il [[Routing]], una navBar di Bootstrap ha i link standard, vanno trasformati con l'AS affinché funzionino.