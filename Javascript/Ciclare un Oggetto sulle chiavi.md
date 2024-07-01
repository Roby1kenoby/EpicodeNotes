
```javascript
    Object.keys(song).forEach(key => {
        let r = document.createElement('td')
        // song[key] è come accedo al valore
        r.innerHTML = song[key]
        row.appendChild(r)
    });
```

Se ho la chiave in una variabile, posso accedere così: 
```javascript
    let chiave = 'pippo'
    let obj = {
	    pippo: 1,
	    paperino: 'due'
    }
    console.log(obj[chiave])
```