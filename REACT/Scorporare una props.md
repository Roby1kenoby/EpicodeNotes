Quando creo un componente, se non metto le graffe, l'oggetto che arriva come argomento della funzione contiene eventuali proprietà, che dovrò poi scomporre manualmente
```JSX
function Display(props){
	let counter = props.counter
}
```

Se invece utilizzo le graffe, posso richiamare direttamente le proprietà che mi servono
```JSX
function Display({counter}){
	// qua dentro posso usare counter per farci cose
}
```