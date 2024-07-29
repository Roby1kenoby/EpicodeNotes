Server a fare il cambiamento automatico di Route.

```JSX
const navigate = useNavigate()

// poi richiamo con 
if(error){
	navigate('/*')
}
```

Questo mi porta alla route desiderata.
In alternativa, posso utilizzare un componente [[Navigate]]