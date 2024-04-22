Di base permette di creare interfacce nativamente responsive.
Documentazione
https://getbootstrap.com/docs/5.3/getting-started/introduction/

Per inserirlo nel nostro progetto o mi scarico i file e li inserisco nel progetto, oppure posso referenziare via link

```html
<!- Css ->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">

<!- Javascript  ->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz" crossorigin="anonymous"></script>
```

Ha i suoi breakpoint (vedi [[Media Querys - Sviluppo Responsive]])

Il javascript di bootstrap possiamo tranquillamente metterlo al fondo del body, come al solito. Tanto il javascript controlla le interazioni, e quelle arrivano dopo che la pagina si è caricata.