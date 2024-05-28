MILESTONE 1
Dopo aver creato il progetto ragionate sui componenti e cercate di ricalcare quanto visto nei live coding di oggi e venerdì.
Come dati utilizzate l'array in allegato. Potete incollarlo nel vostro data, oppure importare il file come visto oggi.
Avrete un componente padre (es. CardsList) che dichiara l'array nel data e vi cicla per passare il singolo dato al figlio (es. SingleCard) tramite le sue props.

MILESTONE 2
Spostate i dati in questione in uno store.js, all'interno di un array che chiamerete ad esempio carte.
Il componente padre (es. CardsList) richiama store.carte e vi cicla per passare il singolo dato al figlio (es. SingleCard).
Vi chiederete cosa cambia rispetto a prima? Cosa ci guadagno? Nulla! Ma ci tornerà utile per bonus con axios

MILESTONE 3
Aggiungete una select in pagina per scegliere l'archetipo.
La select dovrà essere direttamente in App.vue e non in un componente. :avviso:
Le options della select verranno popolate dinamicamente, grazie a un array contenente tutti gli archetipi.
Dove prendo gli archetipi? Con un'altra chiamata, sempre al caricamento di App.vue ma a questo endpoint. I dati vanno sempre nello store.

MILESTONE 4
Quando l'utente seleziona un valore dalla lista, dovrete aggiornare la lista di cards che avete in store.
Vuol dire che effettuerete una chiamata alle API (simile a quella iniziale) ma con l'archetipo selezionato.