Tutte le classi per margin iniziano con m- e tutte quelle per il padding con p-.
Poi lato (t per top, b per bottom, s per start ed e per end) e size.

Attenzione, se aggiungo margini, questi non vengono considerati nel dimensionamento delle colonne. Se ho due colonne col-6, e ad una gli do ms-2, lo spazio effettivo occupato sarà il 50% del container + un tot del margine, e di conseguenza la seconda colonna mi va a capo.

Per risolvere questa cosa, si usano i gutter, che praticamente fanno da padding. 

**IMPORTANTE: in genere, conviene avere le classi di dimensionamento da sole, in modo da definire con esse la struttura, e poi inserire un div al loro interno per il contenuto (lì poi potrò applicare i miei margini e padding)**


