Prima fare un framewire con le macrosezioni e poi scendere nel dettaglio di ognuna di esse.
![[EsempioScomposizione.png]]

Per quanto riguarda il css, vedere quali sono gli aspetti più comuni e cercare di fare classi apposite.
Se possibile, minimizzare gli elementi html, e usare pseudo-classes per gestire le particolarità dei singoli elementi.

Se possibile, inizializzare sempre tutto quanto a margin 0 (body, h1, ecc)

Sistemare per prima cosa la struttura portante, e poi andare a lavorare sui dettagli

Progettare prima a livello mobile e poi scalare verso il desktop

In genere, conviene mettere al fondo della pagina html (below the fold) i componenti javascript che non sono essenziali per il rendering, mentre tutto quello che serve per la visualizzazione ed il caricamento iniziale sopra (above the fold).