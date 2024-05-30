
```javascript
let cleanTracks = function(){
	// individuo l'elemento padre
    let tab = tracksModal.querySelector('tbody')
    // con un querySelector cerco l'elemento da eliminare. Se sono uguali tra di loro (per es stesso tag o classe) è più comodo
    let childDaEliminare = tab.querySelectorAll('tr')[0]
    // perchè poi, finché ci sono elementi dello stesso tipo, li rimuovo così
    while (childDaEliminare){
        tab.removeChild(childDaEliminare)
        childDaEliminare = tab.querySelectorAll('tr')[0]
    }
}
```