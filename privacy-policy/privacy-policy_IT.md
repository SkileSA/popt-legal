# Informativa sulla privacy di Popt

*Questo documento è una traduzione della versione inglese. Solo la versione inglese è giuridicamente vincolante: [privacy-policy_EN.md](privacy-policy_EN.md).*

Ultimo aggiornamento: 2 novembre 2026

## Riepilogo

Popt è un’app che mette la privacy al primo posto. I contenuti che metti in Popt vengono crittografati sul tuo dispositivo prima di essere inviati ovunque, con chiavi che noi non abbiamo (vera crittografia end-to-end). Non possiamo leggere le tue attività, note, diario, foto, libreria, post o messaggi, e non può farlo nemmeno chi dovesse violare i nostri server. Quello che i nostri server vedono è la parte tecnica: quali account condividono contenuti, le date di creazione e modifica dei contenuti, e il tuo nome Popt e il tuo avatar, così che tu possa vedere chi è in un gruppo con te anche se non siete amici.

Non usiamo i tuoi dati per addestrare l’IA. Non li vendiamo a terzi. Non creiamo profili su di te e non ti mostriamo pubblicità di alcun tipo. L’app si connette ai nostri server per sincronizzare e fare il backup dei tuoi contenuti su tutti i tuoi dispositivi, e per far funzionare la condivisione, i messaggi e il nostro servizio di ricerca di contenuti multimediali da aggiungere alla tua libreria Popt. L’app comunica anche con servizi di terze parti che svolgono per noi funzioni essenziali:

* **Apple:** ricerca in Mappe, Luoghi e Musica, tutto coperto dalle solide politiche sulla privacy di Apple.
* **Google:** gestione degli account e autenticazione con Firebase. Hosting dei server e del database con Google Cloud.
* **PowerSync:** i tuoi dati passano dai server di PowerSync per raggiungere i tuoi dispositivi.
* **Cloudflare:** le tue foto e i tuoi file crittografati sono conservati in Cloudflare R2. L’app carica e scarica direttamente da R2.

Queste terze parti non hanno accesso ai tuoi contenuti, che in ogni caso sono completamente crittografati.

Puoi esportare tutto, eliminare tutto e verificare le nostre affermazioni con gli strumenti open source che pubblichiamo.

## Chi siamo

Popt è realizzato da Skile SA, una società con sede in Svizzera. Skile SA è il titolare del trattamento per Popt: decidiamo noi cosa raccoglie l’app e perché, e ne rispondiamo. La nostra giurisdizione è la Svizzera. Popt è usato in Europa, negli Stati Uniti e altrove, e ci impegniamo a rispettare le leggi sulla protezione dei dati più restrittive. Oggi è il Regolamento generale sulla protezione dei dati dell’UE (GDPR), quindi in qualunque paese tu sia, hai le tutele del GDPR.

Per qualsiasi cosa riguardi questa informativa puoi scriverci a support@popt.com. Il nostro indirizzo è Skile SA, Rue de Riant-Coteau 7, 1196 Gland, Svizzera.

Non abbiamo partner pubblicitari, né data broker, né società di analisi dietro l’app. Le uniche altre parti coinvolte sono i fornitori di servizi elencati in [Servizi a cui si connette l’app](#servizi-a-cui-si-connette-lapp), e li nominiamo tutti.

## Come sono protetti i tuoi contenuti

Tutto ciò che scrivi, fotografi o salvi in Popt viene crittografato sul tuo dispositivo prima di uscirne, con chiavi che hai solo tu e le persone con cui condividi. I nostri server conservano e trasmettono quel contenuto crittografato. Usiamo crittografia standard di settore e niente di nostra invenzione: AES-256 per i tuoi contenuti e file, e chiavi a curva ellittica per condividerli. Il progetto completo è pubblicato e può essere verificato in modo indipendente (vedi [Verifica in prima persona](#verifica-in-prima-persona)).

**Le tue chiavi non lasciano mai il tuo dispositivo in forma leggibile.** Una copia bloccata è conservata sui nostri server perché si possa configurare un nuovo dispositivo, e l’unica cosa che può sbloccarla è il tuo **codice di recupero**, generato sul tuo dispositivo e mai visto da noi. Il codice di recupero è l’unico segreto che devi conservare. Se lo perdi e perdi anche tutti i dispositivi in cui hai effettuato l’accesso, non possiamo recuperare i tuoi contenuti per te.

**I contenuti condivisi** sono crittografati esattamente per le persone nella condivisione, e ognuna di loro ha la propria chiave. Quando qualcuno viene rimosso, ciò che viene condiviso da quel momento è crittografato con una nuova chiave che quella persona non ha.

**Foto e file** vengono crittografati sul tuo dispositivo prima del caricamento, e lo stesso vale per il loro nome, tipo e dimensioni. Ogni file ha la propria chiave, contenuta nell’elemento crittografato a cui appartiene, quindi una foto è leggibile solo da chi può leggere la nota, la lista o il post in cui si trova. Nello spazio di archiviazione un file è solo un nome casuale e un blocco di dati crittografati.

**Anche le notifiche push** sono crittografate. L’anteprima in una notifica (il nome di un elemento, le prime parole di un commento) è sigillata in modo che solo i dispositivi destinatari possano aprirla. Le notifiche passano da Firebase Cloud Messaging di Google e poi dal servizio push di Apple; entrambi, come il nostro server delle notifiche, vedono gli identificativi dell’account di origine e di destinazione e il tipo di evento (messaggio, post, nuova condivisione...), mai cosa dice.

### Cosa non è crittografato

Un server che conserva e consegna contenuti crittografati deve comunque sapere a quale account appartengono, con quali account sono condivisi, quale dispositivo li ha aggiornati per ultimo e quando sono stati creati o aggiornati. Questi sono i dati che i nostri server possono leggere, e il motivo per cui ognuno esiste:

- **Identificativi degli account.** Perché il server possa consegnare ogni elemento ai dispositivi giusti e a nessun altro.
- **Quando ogni elemento è stato creato, modificato o eliminato, e quali dispositivi lo hanno aggiornato per ultimi.** È così che si riconciliano due dispositivi che hanno modificato la stessa cosa mentre erano offline: senza questi dati il server non saprebbe quale modifica è la più recente, e le modifiche andrebbero perse. L’identificativo del dispositivo è l’identifier for vendor di Apple (IDFV): è specifico di Popt su quel dispositivo, non è l’identificativo pubblicitario e non può essere usato per riconoscerti in altre app. Si azzera quando Popt viene rimosso dal dispositivo.
- **Come sono raggruppati i contenuti.** A quale elemento di primo livello (una lista, una nota, un post, un progetto) appartiene ogni parte. Il server conserva, consegna e protegge i contenuti come elementi interi, quindi deve sapere dove finisce uno e dove inizia il successivo. La struttura interna di un elemento, quale riga sta sotto quale, è crittografata.
- **Il tuo nome Popt, la riga di stato e l’avatar.** Restano leggibili perché tutti in un post o in una lista condivisa possano vedere chi altro c’è, comprese le persone che non sono tue amiche, e perché chi inviti possa vedere chi lo sta invitando. L’app lo dice dove modifichi il tuo profilo.
- **Quali conversazioni hai silenziato, e la data in cui hai aperto ciascuna per l’ultima volta.** Il nostro server delle notifiche le legge per smettere di notificarti una conversazione che hai silenziato, e per evitare di avvisarti di qualcosa che hai già visto. Tiene traccia degli identificativi delle conversazioni, non dei contenuti.
- **Quanto spazio usi.** Cloudflare, dove sono conservati i file crittografati, vede la dimensione di ciascuno, come qualsiasi servizio di archiviazione. Noi sommiamo il totale per account per applicare il limite di spazio del tuo piano, e liberiamo un file quando non c’è più nulla che vi faccia riferimento.

## I dati che raccogliamo e perché

Raccogliamo il minimo necessario perché l’app funzioni, e niente per sapere qualcosa di te.

- **Il tuo indirizzo email.** Per farti accedere e per riconoscerti quando ci scrivi. Lo fornisci tu all’accesso, oppure arriva da Apple o Google quando accedi con loro (Accedi con Apple può nasconderlo dietro il relay di Apple). È conservato da Firebase Authentication; il nostro database ne tiene solo un hash.
- **Il tuo nome Popt, la riga di stato e l’avatar.** Perché gli amici ti riconoscano. Solo il nome è obbligatorio. Conservati in chiaro, come spiegato sopra.
- **I tuoi contenuti crittografati e i loro metadati.** Per sincronizzarli tra i tuoi dispositivi e con le persone con cui condividi.
- **Identificativi anonimi dei dispositivi.** Per notificare i tuoi dispositivi e distinguerli. Usa l’`identifierForVendor` di Apple, che tutela la privacy.
- **Le ricevute del tuo abbonamento.** Per sbloccare Popt Pro su tutti i tuoi dispositivi. Arrivano da Apple quando ti abboni; non vediamo mai i dati di pagamento.
- **Log delle richieste** (indirizzo IP, ora, percorso). Per mantenere il servizio in funzione e indagare sugli abusi, come qualsiasi server web.
- **Segnalazioni di abusi.** Per intervenire sui comportamenti dannosi. Arrivano dalle persone che le inviano.

**Cosa non raccogliamo:** la tua data di nascita, i tuoi contatti, la tua libreria fotografica, la tua posizione, statistiche su come usi l’app o un identificativo pubblicitario.

**Basi giuridiche.** Trattiamo i tuoi dati per fornire il servizio che hai richiesto (il contratto con te), perché hai scelto di condividere qualcosa o di concedere un’autorizzazione (consenso, che puoi revocare), per mantenere il servizio sicuro e rispondere alle segnalazioni di abusi (il nostro legittimo interesse, e in parte un obbligo di legge), e per adempiere agli obblighi contabili e fiscali (obbligo di legge).

**Non vendiamo mai dati, non li condividiamo mai a fini pubblicitari e non usiamo mai i tuoi contenuti per addestrare alcunché.**

## Servizi a cui si connette l’app

Questa è la lista completa. Se l’app comunica con qualcosa, è qui.

### Server Popt

Girano su Google Cloud negli Stati Uniti, e le foto e i file crittografati sono conservati presso Cloudflare, anch’essa negli Stati Uniti. Lo diciamo chiaramente perché il luogo conta, e perché qui conta pochissimo: su quei server ci sono contenuti che non possiamo leggere, più i metadati elencati sopra. I tuoi contenuti sono illeggibili in un data center negli Stati Uniti tanto quanto lo sarebbero in uno svizzero, e i metadati sono protetti dalle stesse regole ovunque si trovino.

Tutti si trovano sotto `*.popt.com`. Ecco cosa invia ogni funzione dell’app:

- **Sincronizzazione tra i tuoi dispositivi.** I tuoi contenuti crittografati, i metadati elencati sopra e la prova che hai effettuato l’accesso.
- **Amici e condivisione.** Gli identificativi degli account connessi come amici, gli identificativi degli account che fanno parte di ogni lista, progetto o post condiviso, e copie bloccate delle chiavi condivise.
- **Messaggi.** I tuoi messaggi crittografati e gli identificativi degli account delle due parti di una conversazione.
- **Notifiche.** L’indirizzo che Apple ci fornisce per raggiungere il tuo dispositivo, gli identificativi degli account di mittente e destinatari, e l’anteprima crittografata.
- **Popt Pro.** La ricevuta Apple del tuo abbonamento, perché Pro possa essere sbloccato su tutti i tuoi dispositivi.
- **Accesso via email.** Il tuo indirizzo email, per poterti inviare il codice monouso.
- **Aggiunta alla libreria.** La tua ricerca di un libro, film, serie, gioco o podcast, con la tua lingua e la tua fascia d’età. Le ricerche non vengono registrate.
- **Pubblicazione di un elemento della libreria come link.** L’elemento che hai scelto di pubblicare. L’elemento pubblicato non è collegato al tuo account.
- **Segnalazione di abusi.** La tua segnalazione, crittografata e leggibile solo dal nostro team di revisione.
- **Avatar.** Lo stile che hai scelto e un numero casuale da cui viene disegnato l’avatar. Niente su di te.

I nostri server conservano i log standard delle richieste per 30 giorni: quale indirizzo ha chiamato quale funzione, e quando.

### Servizi Google

A tutti questi si applica l’[informativa sulla privacy di Google](https://policies.google.com/privacy). Firebase e Google Cloud pubblicano ciascuno una pagina propria, linkata qui sotto.

- **Accesso ([Firebase Authentication](https://firebase.google.com/support/privacy)).** Conserva il tuo indirizzo email e il modo in cui accedi. Con Accedi con Google, anche il nome e la foto del tuo account Google.
- **Prova che l’app è autentica ([Firebase App Check](https://firebase.google.com/support/privacy)).** Prima che i nostri server rispondano, l’app dimostra di essere una copia autentica di Popt in esecuzione su un dispositivo reale. Google vede quella prova, non a cosa serve la richiesta.
- **Consegna delle push ([Firebase Cloud Messaging](https://firebase.google.com/support/privacy)).** Inoltra le nostre notifiche al servizio push di Apple. Conserva l’indirizzo che Apple ci fornisce per raggiungere il tuo dispositivo. La notifica che inoltra è crittografata.
- **Hosting ([Google Cloud](https://cloud.google.com/terms/cloud-privacy-notice)).** Fa girare i nostri server e il nostro database negli Stati Uniti, e quindi conserva tutto ciò che conservano i nostri server.
- **YouTube.** Quando salvi un link YouTube, il tuo dispositivo chiede a YouTube titolo e miniatura. Quando riproduci un trailer dentro l’app (dai 16 anni in su), l’app carica il player di YouTube, e YouTube ti vede come vedrebbe un visitatore del suo sito, cookie compresi. YouTube non ha un’informativa separata: vale quella di Google.

### Servizi Apple

A tutti questi si applica la [Politica sulla privacy di Apple](https://www.apple.com/legal/privacy/). Dove Apple pubblica una pagina per un singolo servizio, è linkata qui sotto.

- **[Accedi con Apple](https://www.apple.com/legal/privacy/data/en/sign-in-with-apple/).** Apple ci comunica il tuo indirizzo email, oppure l’indirizzo di relay privato che hai scelto per nasconderlo.
- **Notifiche (il servizio Apple Push Notification).** Consegna le nostre notifiche al tuo dispositivo. Apple trasporta la busta crittografata e non può leggerla.
- **Popt Pro (l’[App Store](https://www.apple.com/legal/privacy/data/en/app-store/)).** Il tuo abbonamento viene acquistato da Apple e fatturato da Apple. Un acquisto è legato al tuo account Popt da un token casuale, e la ricevuta di Apple è ciò che i nostri server verificano.
- **Luoghi ([Mappe di Apple](https://www.apple.com/legal/privacy/data/en/apple-maps/)).** Cercare un luogo, mostrare la mappa e trasformare le coordinate in un indirizzo: tutto va ad Apple dal tuo dispositivo. Le ricerche sono legate a un identificativo che cambia nel tempo, non al tuo ID Apple o al tuo account Popt.
- **Musica ([Apple Music](https://www.apple.com/legal/privacy/data/en/apple-music/) e [Shazam](https://www.apple.com/legal/privacy/data/en/music-recognition/)).** La ricerca di un album o di un artista va ad Apple Music. Il riconoscimento di un brano invia a Shazam una breve impronta audio, non la registrazione.
- **Fascia d’età.** Richiesta a iOS sul dispositivo, come descritto in [Minori ed età](#minori-ed-età). Deriva dall’età del tuo [Apple Account](https://www.apple.com/legal/privacy/data/en/apple-account/).


### PowerSync

Si applica l’[informativa sulla privacy di PowerSync](https://www.powersync.com/legal/privacy-policy).

PowerSync (JourneyApps) è il servizio che gestisce la sincronizzazione dal database Popt verso i tuoi dispositivi. I tuoi dispositivi si connettono direttamente a PowerSync, con un token dei nostri server, negli Stati Uniti.

### Cloudflare R2

Si applica l’[informativa sulla privacy di Cloudflare](https://www.cloudflare.com/privacypolicy/).

Le tue foto e i tuoi file crittografati sono conservati presso Cloudflare, negli Stati Uniti. L’app li carica e li scarica direttamente, a un indirizzo temporaneo fornito dai nostri server, quindi Cloudflare vede il tuo indirizzo IP, i byte crittografati e la loro dimensione, e una chiave di archiviazione che inizia con l’identificativo del tuo account. Mai un nome di file, mai il contenuto.

### Wikipedia e Wikidata

Si applica l’[informativa sulla privacy di Wikimedia](https://foundation.wikimedia.org/wiki/Policy:Privacy_policy).

Quando aggiungi un artista alla tua libreria, il tuo dispositivo chiede a Wikidata quale voce di Wikipedia corrisponde a quell’artista, poi chiede a Wikipedia il primo paragrafo. Vedono il tuo indirizzo IP e l’artista, niente sul tuo account.

### Altri

Alcune richieste vanno direttamente dal tuo dispositivo al sito a cui punta un link. Quel sito vede il tuo indirizzo IP, come quando lo visiti con qualsiasi browser. Non possiamo elencare quei siti, perché dipendono dai link che salvi.

- **Anteprime dei link.** Quando salvi o incolli un link, il tuo dispositivo scarica quella pagina per mostrare un titolo e un’immagine. I link TikTok usano l’endpoint di anteprima di TikTok. Le immagini nei risultati di ricerca e nelle anteprime dei link vengono caricate dai loro host originali. Se hai effettuato l’accesso a un sito nel browser di Popt, quelle richieste di anteprima portano con sé i cookie di quel sito.
- **Immagini delle notifiche.** Quando il post di un amico include un link, il tuo dispositivo scarica l’immagine del link per mostrarla nella notifica.
- **Il browser di Popt** è un normale browser web: i siti che visiti ti vedono come con qualsiasi browser. Cronologia e cookie restano sul tuo dispositivo, e un browser aperto dentro una cassaforte segreta non conserva niente.

## Servizi che usiamo dietro le quinte

Il tuo dispositivo non si connette mai a questi. Lo fanno i nostri server, dal nostro indirizzo, senza trasmettere alcuna identità, account o indirizzo IP.

### Twilio SendGrid

Si applica l’[informativa sulla privacy di Twilio](https://www.twilio.com/en-us/legal/privacy).

Invia l’email con il codice di accesso, e quindi riceve il tuo indirizzo email a ogni accesso.

### TMDB

Si applica l’[informativa sulla privacy di TMDB](https://www.themoviedb.org/privacy-policy).

Quando cerchi un film, una serie TV, un attore o un regista, il nostro server inoltra le parole che hai digitato e la tua lingua.

### Movie of the Night

Si applica l’[informativa sulla privacy di Movie of the Night](https://www.movieofthenight.com/privacy).

Dice all’app dove un film o una serie si può vedere in streaming. Il nostro server invia il numero di catalogo del film e il tuo paese.

## Solo sul tuo dispositivo

Diverse funzioni intelligenti di Popt girano interamente sul tuo telefono. Non ci viene inviato niente al riguardo.

- **Smistare ciò che scrivi.** Quando scrivi un appunto, un piccolo modello di apprendimento automatico incluso nell’app decide se sembra un’attività, un articolo della spesa, una voce di diario o una nota, e smista gli articoli della spesa per reparto. I modelli girano sul dispositivo. Il tuo testo non viene inviato da nessuna parte per questo. Per una lingua per cui non forniamo un modello, l’app chiede ad [Apple Intelligence](https://www.apple.com/legal/privacy/data/en/intelligence-engine/) sul dispositivo quando è disponibile, altrimenti non fa niente.
- **Ricerca.** L’indice di ricerca di Popt viene costruito sul tuo dispositivo a partire dai tuoi contenuti decifrati e non lo lascia mai. Se attivi Siri e Spotlight per Popt, l’indice di Apple sul dispositivo riceve le attività, le liste e le note che scegli. Quell’indice resta sul dispositivo ed è coperto dalla [politica di Apple su Siri](https://www.apple.com/legal/privacy/data/en/ask-siri-dictation/).
- **Controllo delle foto.** Sui dispositivi in cui sono attivi Avviso contenuti sensibili o Sicurezza nelle comunicazioni di Apple, Popt chiede a iOS di controllare sul dispositivo ogni foto che mostra, alla ricerca di nudità. Le foto segnalate vengono sfocate. Le foto non vengono inviate da nessuna parte per questo controllo, e noi non veniamo mai a conoscenza del risultato.
- **Fascia d’età.** Se usi una funzione soggetta a limiti di età, Popt chiede a iOS in quale fascia d’età rientri (meno di 13, da 13 a 15, da 16 a 17, o 18 e più). Popt non vede mai una data di nascita. La risposta è salvata con le tue impostazioni crittografate, quindi non possiamo leggerla nel nostro database. L’unico punto in cui viaggia in chiaro è la ricerca di Aggiungi alla libreria: la fascia approssimativa (meno di 13, da 13 a 15, da 16 a 17, 18 e più) accompagna la ricerca perché i risultati siano adatti all’età, senza il tuo account.
- **Posizione.** Allegare un luogo a una voce usa la posizione del tuo dispositivo solo quando lo scegli tu, e solo se lo hai consentito in iOS. Le coordinate sono crittografate come qualsiasi altro contenuto. Trasformare le coordinate in un indirizzo è una richiesta dal tuo dispositivo a Mappe di Apple, secondo le politiche di Apple su [Localizzazione](https://www.apple.com/legal/privacy/data/en/location-services/) e [Mappe](https://www.apple.com/legal/privacy/data/en/apple-maps/). Non passa mai dai nostri server.
- **Avvisi.** Gli avvisi per le attività con una data sono programmati localmente dall’app, non da un server.

## Funzioni social

Popt non ha un elenco pubblico di profili: nessuno può trovarti o vedere qualcosa di tuo senza un invito diretto. Tutto ciò che condividi resta crittografato end-to-end, e le persone con cui condividi possono leggere solo ciò che hai condiviso. I nostri server vedono gli identificativi degli account coinvolti, mai il contenuto.

### Inviti

Un invito è un link. Il messaggio facoltativo e l’elemento della libreria al suo interno sono crittografati sul tuo dispositivo con una chiave che viaggia nel link stesso, così che il contenuto dell’invito non sia conservato in chiaro sul nostro server ma l’invito resti visualizzabile in anteprima da chiunque abbia il link completo. Accettare un invito connette i due identificativi di account come amici e scambia le chiavi su cui si basa la condivisione successiva.

### Post

Un post è crittografato per gli amici che hai scelto quando lo hai pubblicato, e ogni commento è crittografato per le persone presenti nel post in quel momento.
- Solo chi ha pubblicato il post può aggiungere o rimuovere partecipanti
- I nuovi partecipanti non vedono i commenti precedenti
- I partecipanti rimossi non possono vedere i commenti successivi, ma conservano l’accesso al post e a tutti i commenti che potevano vedere al momento della rimozione

### Messaggi

Ogni parte di una conversazione possiede la propria metà: i tuoi messaggi sono crittografati con una chiave che avete solo voi due, e l’altra persona non può né modificarli né eliminarli. Eliminare un tuo messaggio lo rimuove per entrambi. I nostri server vedono che due identificativi di account si scambiano messaggi crittografati, e quando.

### Liste, progetti e note condivisi

I contenuti collaborativi sono crittografati con una chiave condivisa da tutti i partecipanti, e ogni membro può leggere o modificare secondo il ruolo che gli hai assegnato. Quando rimuovi qualcuno, il contenuto viene crittografato di nuovo con una nuova chiave e tolto dai suoi dispositivi alla sincronizzazione successiva. Ciò che ha scritto mentre era membro resta nella lista, di tua proprietà.

### Segnalare abusi

La segnalazione è l’unico caso in cui un contenuto ci arriva in forma leggibile. Quando segnali un profilo, un post o un messaggio, la segnalazione contiene il contenuto che stai segnalando, le sue foto e, per un messaggio, i pochi messaggi intorno per il contesto, più una nota facoltativa. Il contenuto segnalato ti viene mostrato prima dell’invio, così sai esattamente cosa stai inviando. La segnalazione viene poi crittografata sul tuo dispositivo prima di esserci inviata, così che solo il nostro team di revisione possa aprirla. L’account segnalato non viene informato della tua segnalazione, ma può essere sospeso o escluso del tutto dall’uso dei nostri servizi.

## Eliminazione e conservazione dei dati

**Eliminare i contenuti.** Tutto ciò che elimini va in Eliminati di recente per 30 giorni, dove puoi ripristinarlo o eliminarlo subito in modo definitivo. Dopo 30 giorni i nostri server lo cancellano definitivamente. Una foto o un file viene cancellato dallo spazio di archiviazione non appena sparisce l’ultimo elemento che vi fa riferimento. I contenuti condivisi con altri vivono anche sui loro dispositivi: eliminare la tua copia non elimina la loro.

**Eliminare il tuo account.** Apri Il mio account, scegli Elimina account e scrivi la frase di conferma. Entro 7 giorni eliminiamo il tuo accesso, il tuo profilo, le tue chiavi, i tuoi contenuti e file crittografati, i tuoi token push e le tue impostazioni delle notifiche. Liste, note e progetti condivisi di tua proprietà vengono eliminati per tutti i partecipanti, e lo stesso vale per i tuoi post con tutti i relativi commenti, i tuoi commenti sui post di altre persone e i tuoi messaggi. Ciò che hai aggiunto a liste, note e progetti dei tuoi amici resta lì. I tuoi amici vedranno poi “Account eliminato” al posto del tuo nome. Anche tutto ciò che aggiungi tra la richiesta e l’eliminazione viene eliminato, e dopo non è possibile recuperare nulla. Eliminare l’account non annulla un abbonamento a Popt Pro: annullalo nelle impostazioni degli abbonamenti del tuo Apple Account. Se non hai più nessun dispositivo in cui hai effettuato l’accesso, scrivi a support@popt.com dall’indirizzo usato alla registrazione ed elimineremo l’account per te.

Alcuni dati devono essere conservati più a lungo per adempiere ai nostri obblighi di legge:
- Le registrazioni degli abbonamenti che Apple ci chiede di conservare a fini contabili sono conservate per il tempo richiesto dalla legge.
- Le segnalazioni di abusi sono conservate finché ci servono per intervenire sulla segnalazione e per rispondere della nostra decisione, anche dopo che l’account segnalato non esiste più.

**Uscire** elimina i tuoi contenuti dal dispositivo: il database, le cache di foto e file, i cookie e gli accessi del browser, l’indice Spotlight e le tue impostazioni. Se hai attivato il Portachiavi iCloud sul dispositivo da cui hai effettuato l’accesso a Popt, il codice di recupero resta nel tuo portachiavi, così puoi accedere di nuovo a Popt facilmente, su qualsiasi dispositivo in cui hai effettuato l’accesso con lo stesso ID Apple.

**Tutto il resto ha vita breve.** Le registrazioni di consegna delle notifiche vengono eliminate dopo 31 giorni; i codici di accesso, i link di invito e i contatori dei limiti di richieste vengono eliminati quando scadono.

## I tuoi diritti

Ovunque tu viva, hai dei diritti sui tuoi dati, e noi riconosciamo a tutti l’insieme completo dei diritti del GDPR. La maggior parte puoi esercitarla direttamente nell’app, ed è così che preferiamo, perché non possiamo leggere i tuoi contenuti e non dovremmo doverlo fare.

- **Accesso e portabilità.** Esporta tutto da Il mio account. L’esportazione è una cartella di semplici file Markdown e delle tue foto, leggibile con qualsiasi editor di testo e con Obsidian. Comprende i tuoi contenuti e ciò che altri hanno condiviso con te. I contenuti in una cassaforte segreta si esportano spostandoli prima in Home dall’interno della cassaforte.
- **Rettifica.** Modifica qualsiasi cosa nell’app. Il nome del profilo, lo stato e l’avatar sono tuoi e puoi cambiarli in qualsiasi momento.
- **Cancellazione.** Elimina contenuti, o l’intero account, come descritto sopra.
- **Opposizione e limitazione.** Non facciamo profilazione, né pubblicità, né decisioni automatizzate su di te, quindi in questo senso non c’è nulla a cui opporsi. Se credi che conserviamo qualcosa che non dovremmo, scrivici.
- **Revoca del consenso.** Posizione, notifiche, accesso alle foto e fascia d’età sono autorizzazioni di iOS che puoi revocare in Impostazioni in qualsiasi momento. L’app continua a funzionare senza.
- **Reclamo.** Puoi presentare reclamo all’Incaricato federale svizzero della protezione dei dati e della trasparenza (IFPDT, edoeb.admin.ch) o all’autorità per la protezione dei dati del tuo paese. Preferiremmo che ci scrivessi prima, ma non è obbligatorio.

Per tutto ciò che non puoi fare nell’app, scrivici a **support@popt.com**. Poiché non possiamo vedere i tuoi contenuti, potremmo chiederti di dimostrare che controlli l’account, per esempio scrivendo dall’indirizzo email usato alla registrazione.

**Dove sono i tuoi dati.** I nostri server e il nostro spazio di archiviazione sono negli Stati Uniti, come descritto in [Servizi a cui si connette l’app](#servizi-a-cui-si-connette-lapp). I trasferimenti fuori dalla Svizzera e dall’UE sono coperti dalle clausole contrattuali standard dell’UE con ciascun fornitore, e dalla crittografia stessa: ciò che esce è contenuto che non possiamo leggere.

## Minori ed età

Popt è classificato 13+ sull’App Store, e i genitori possono approvarlo per un bambino più piccolo tramite Tempo di utilizzo. L’unico dato personale coinvolto è la **fascia d’età**, ed ecco come la gestiamo.

Non chiediamo mai una data di nascita. Quando qualcuno usa per la prima volta una funzione soggetta a limiti di età, Popt chiede a iOS in quale fascia d’età rientra (meno di 13, da 13 a 15, da 16 a 17, o 18 e più) tramite la Declared Age Range API di Apple, che i genitori configurano nelle impostazioni Famiglia. La risposta è salvata con le tue impostazioni crittografate, dove non possiamo leggerla. L’unico punto in cui la fascia viaggia in chiaro è la ricerca di Aggiungi alla libreria, perché i risultati siano adatti all’età, e non è collegata al tuo account.

Cosa sblocca ogni fascia d’età, come funziona l’approvazione dei nuovi amici da parte dei genitori e come vengono gestite le foto segnalate è spiegato nella nostra pagina sulla sicurezza dei contenuti: [popt.com/content-safety](https://popt.com/content-safety). Non raccogliamo nient’altro sui minori.

## Verifica in prima persona

Non dovresti doverci credere sulla parola per nulla di tutto questo. Pubblichiamo **veri-popt**, un insieme di strumenti e documentazione per verificare la crittografia di Popt: [github.com/SkileSA/veri-popt](https://github.com/SkileSA/veri-popt).

## Modifiche a questa informativa

Quando cambiamo cosa raccoglie l’app o con chi comunica, aggiorniamo prima questa informativa e poi l’app. La data in alto è la data dell’ultima modifica, e la cronologia completa delle versioni è pubblica nel nostro repository di documenti legali su GitHub, insieme ai nostri Termini di servizio: [github.com/SkileSA/popt-legal](https://github.com/SkileSA/popt-legal). Per una modifica che riduce la tua privacy, ti avviseremo via email prima che entri in vigore.
