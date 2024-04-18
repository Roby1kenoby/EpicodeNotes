Aumenta la dimensione di un elemento, ma SOLO SE NECESSARIO (i contenuti richiedono spazio)
Il valore di default degli elementi è 0.

Se ho elementi piccoli, e gli do a tutti un grow identico, cercheranno di prendere più spazio disponibile possibile, equiripartito, ma cmq sempre in base anche al contenuto (se uno ne ha un po' di più, allora ne prenderà leggermente di più)

In combinazione con [[Flex-Basis]] posso invece renderli identici a livello di dimensione (ma il contenuto comunque la fa da padrone).

Notazione rapida: flex: 0 1 auto (Grow, Shrink, Basis)