# Coordinamento delle quattro piattaforme
Versione proposta: 25 settembre 2026. Documento operativo in revisione, non un servizio di monitoraggio né un lock distribuito già installato.

## Priorità e autorità
Ordine: VinoVeritas, Copilot 247Agent, Splendoria, Sommelier Academy.
La regia controlla baseline, dipendenze, evidenze e integrazione. Le altre chat possono sviluppare contemporaneamente in branch isolati. Le istruzioni dell'utente e AGENTS.md del progetto continuano ad applicarsi.

Le chat non condividono automaticamente memoria o piani. Un agente può controllare solo il lavoro reso disponibile nei repository, negli ambienti e nei documenti accessibili. Questo protocollo deve essere letto e adottato dalle sessioni coinvolte; il file da solo non impone esclusione reciproca.

## Contratto di attività
Prima di una modifica, registrare nel luogo privato del progetto:
- task ID, progetto e responsabile della sessione;
- repository, branch e commit iniziale; file/funzioni autorizzati;
- ambiente, Worker, versione attiva e risorse dati previste;
- risultato osservabile, aree protette, effetti esterni consentiti;
- test richiesti, baseline precedente e rollback;
- attività concorrenti e risorse condivise;
- stato, ultima verifica, scadenza del coordinamento e collegamento alle evidenze.

Nessun dato cliente, credenziale o dettaglio di vulnerabilità non risolta in questo repository pubblico.

## Concorrenza
1. Letture indipendenti e sviluppo su branch distinti possono procedere insieme.
2. Se due attività cambiano lo stesso file, confrontare le funzioni effettivamente coinvolte; integrare e rieseguire i test sul commit combinato. Non sommare test verdi di commit diversi.
3. Un solo responsabile per deploy, migrazioni, cambi binding o dati di un ambiente. Gli altri attendono o usano un ambiente realmente isolato.
4. Un accordo scritto fra sessioni è un lock operativo, non un lock tecnico. Per un lock tecnico futuro serve un coordinatore atomico con lease, scadenza e fencing token controllato da tutti i deployer. Un semplice file o una issue senza CAS non impedisce le corse.
5. Rileggere commit remoto, deployment ID, insieme delle versioni e percentuali, binding pertinenti e schema prima e dopo ogni qualificazione e immediatamente prima della mutazione.
6. Se uno di questi cambia, marcare la prova INVALIDATA_DA_DRIFT. Conservare la prova originaria; identificare la modifica concorrente e ripetere sul nuovo candidato.
7. Non ripristinare uno staging cambiato da un'altra sessione senza sapere chi lo sta usando. Non eseguire force push o sovrascrivere una release congelata.
8. Anche una push può provocare preview/deploy automatici: verificare workflow e integrazioni del repository prima di pubblicare un branch.

## Stati ammessi
- IN_LETTURA
- IN_SVILUPPO_LOCALE
- PRONTA_PER_REVISIONE
- QUALIFICAZIONE_STAGING
- INVALIDATA_DA_DRIFT
- BLOCCATA_CON_MOTIVO
- PRONTA_PER_RILASCIO
- PUBBLICATA_VERIFICA_PARZIALE
- PUBBLICATA_E_VERIFICATA
- RIPRISTINATA

Ogni stato deve indicare evidenza e timestamp. PRONTA_PER_RILASCIO non concede da sola autorizzazione alla produzione. Un test locale non promuove il live e un HTTP 200 non qualifica tutti i percorsi.

## Obiettivo 3.000 clienti per piattaforma
Separare clienti paganti, tenant, utenti per cliente, utenti contemporanei, richieste API, inferenze AI e volume storico dei dati. Non dividere implicitamente i 3.000 fra le quattro piattaforme.

Prima della qualifica definitiva richiedere:
- isolamento e autorizzazioni A/B, proprietario e membro, revoca e credenziali scadute;
- paginazione completa, query e indici su dataset realistici, carico sbilanciato fra tenant;
- retry, idempotenza, scritture concorrenti, risposta persa dopo commit;
- lavori asincroni in lotti limitati, checkpoint, deduplicazione e ripresa dopo crash;
- quote e concorrenza AI per cliente e globali, timeout, budget e degradazione controllata;
- backup verificato e ripristino di dati sintetici, oltre al solo rollback del codice;
- percorso cliente completo e persistenza dopo logout/nuovo accesso;
- carico graduale e prolungato su staging isolato, versione e schema fissi, monitoraggio errori e costi.

Zero perdite di dati o accessi fra tenant è un gate funzionale. Prestazioni, disponibilità, RPO/RTO e costi sono obiettivi da misurare e concordare; non promesse ricavabili dal numero di test.

## Passaggio di consegne fra chat
Usare questo messaggio insieme al task concreto:

> Leggi il protocollo di coordinamento della regia e AGENTS.md del progetto. Prima di modificare, verifica commit, versione attiva, file coinvolti e attività concorrenti. Lavora su una baseline isolata; rendi disponibili diff, test e limiti della verifica. Coordina in anticipo ogni mutazione dello staging condiviso. Non promuovere test di un altro commit o una versione cambiata. Le autorizzazioni al rilascio restano quelle esplicite dell'utente.

## Limiti del presidio
La presenza di questo documento non attiva controlli periodici, notifiche o un agente permanente. Durante una sessione attiva la regia può rileggere gli strumenti condivisi; un presidio continuativo richiede automazione effettivamente configurata, destinatari autorizzati e gestione degli allarmi.
