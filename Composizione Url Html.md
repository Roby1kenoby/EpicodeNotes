Posso comporre url con variabili da js affinché nell'html ci siano cose (immagini per es).
```javascript
src="url" + param
```

Se url ha lo slash al fondo, il percorso è a partire dal dominio (https://pippo.com + /param)
Se invece non ha lo slash al fondo, il percorso è a partire dalla pagina corrente (https://pippo.com/paginaAttuale + /param)