In genere ci sono tre tipi di rotte:
visibili a tutti (rotte dirette)
solo per utenti loggati (quelle che mostrano i contenuti)
solo per utenti guest (es rotte login)

```JSX
return {
<Routes>
	{/*rotte protette*/}
	<Route element={<ProtectedRoutes />}>
		<Route path="/" element={<Profile />} />
			{/* <Route path="/profile" element={<Profile />} /> */}
		<Route path="/profile/:userId" element={<Profile />} />
		<Route path="/edit-experience/:userId" element={<EditExperiencePage />} />
	</Route>
	{/*rotte per guest*/}
	<Route element={<GuestRoutes />}>
		<Route path="/login" element={<Login/>} />
	</Route>
	{/*rotte accessibili da chiunque*/}
	<Route path="*" element={<NotFound />} />
</Routes>
}

```

Per proteggerle, creo dei componenti appositi, che verificano se nel contesto è presente il token o meno, e in base a quello fanno vedere i propri outlet (componenti route figli) o effettuano un redirect.

```JSX
import { useContext} from "react";
import { LoginContext } from "../contexts/LoginContextProvider";
import { Outlet } from "react-router-dom";
import { Navigate } from "react-router-dom";

function ProtectedRoutes() {
    const {token} = useContext(LoginContext)
    console.log('Sono nel protected Routes ' + token)
    return (
        token ? <Outlet/> : <Navigate to='/login'/>
    );
}
export default ProtectedRoutes;
```

```JSX
import { useContext} from "react";
import { LoginContext } from "../contexts/LoginContextProvider";
import { Outlet } from "react-router-dom";
import { Navigate } from "react-router-dom";

function ProtectedRoutes() {
    const {token} = useContext(LoginContext)
    console.log('sono nel geust routes' + token)
    return (
        !token ? <Outlet/> : <Navigate to='/'/>
    );
}
export default ProtectedRoutes;
```

vedi [[Processo decente per il login]] per implementazione completa.