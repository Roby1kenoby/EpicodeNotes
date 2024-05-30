
```javascript
    Object.keys(song).forEach(key => {
        let r = document.createElement('td')
        // song[key] è come accedo al valore
        r.innerHTML = song[key]
        row.appendChild(r)
    });
```