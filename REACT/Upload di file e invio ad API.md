
Esempio di Fetch nel frontend.
authorData mi arriva da un form, idem file
```Javascript
export const NewAuthor = async (authorData, file) => {
    try {
        // formData è un tipo di dati che permette il passaggio di file
        const formData = new FormData()
        // per ogni elemento dell'oggetto, devo fare append al formData creato, compreso il file
        // potrei fare un automatismo, ma rischio poi di permettere l'inserimento di valori in più
        // sul db da attori malevoli, rispetto a quelli che mi aspetto io
        formData.append('email', authorData.email)
        formData.append('password', authorData.password)
        formData.append('name', authorData.name)
        formData.append('surname', authorData.surname)
        formData.append('birthDate', authorData.birthDate)
        formData.append('avatar', file)
        const resp = await fetch(URI,{

            // non è necessario specificare il content-type perchè se non indico io json in automatico è
            // multipart/formdata
            // headers:{
            //     "Content-type": "application/json"
            // },
            method: 'POST',
            body: formData
        })
        const data = await resp.json()
        console.log(data)

        if(!resp.ok) throw new Error(resp)
        return data
    } catch (error) {
        console.log(error)
    }

}
```

Frontend, quando premo il button di conferma del form, richiama questa funzione
```Javascript
// stato per il file
    const [registerFormAvatar, setRegisterFormAvatar] = useState()

	// funzione per gestire la variazione del file
    const handleAvatarChange = (event) => {
        setRegisterFormAvatar(event.target.files[0])
    }
// funzione per creare il nuovo utente, richiama la fetch vista sopra
	const createNewAuthor = async function(){
	const createdAuthor = await NewAuthor(registerFormData, registerFormAvatar)
	createdAuthor._id ? showLoginForm() : alert('Errore nella creazione dell\'utente')
}
```