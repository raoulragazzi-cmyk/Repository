# SKILL — Multi-Project Control Room / Anti-Confusion Gate

## Scopo
Gestire piu piattaforme software dalla stessa cabina di regia senza confondere repository, Worker, database, domini, ambienti, dati o procedure di deploy.

Questa skill e obbligatoria prima di qualunque modifica, migrazione, pubblicazione, hotfix o intervento infrastrutturale.

---

## 1. Project Identity Gate — obbligatorio prima di agire

Prima di ogni azione di scrittura, dichiarare internamente una **Project Context Card** con almeno:

- `PROJECT_NAME`
- `REPOSITORY`
- `TARGET_BRANCH`
- `CLOUDFLARE_ACCOUNT`
- `PRODUCTION_WORKER`
- `FRONTEND/ASSET_WORKER_OR_PAGES`
- `PRODUCTION_D1_NAME + ID`
- `STAGING_D1_NAME + ID`, se esiste
- `R2_BUCKET`, se esiste
- `PRODUCTION_DOMAINS`
- `HEALTH_ENDPOINT`
- `PROTECTED_AREAS`
- `LAST_KNOWN_GOOD` commit/version
- `DEPLOYMENT_METHOD`

### Regola di consenso
Una modifica puo procedere solo se coincidono almeno **quattro fingerprint indipendenti** tra:
1. repository;
2. Worker/app Cloudflare;
3. dominio;
4. D1 name/ID;
5. branch/ref;
6. R2/AI Search/altro binding critico.

Per operazioni su database o production sono obbligatori repository + Worker + dominio + D1 ID.

Se i fingerprint sono mancanti, ambigui o discordanti: **STOP. Solo lettura e verifica. Nessun deploy.**

---

## 2. Never Cross the Streams

- Non copiare un Worker, `wrangler` o configurazione da un progetto all'altro senza una nuova verifica completa del Project Identity Gate.
- Non inferire il progetto dal solo design, screenshot, nome di una funzione o argomento della conversazione.
- Uno screenshot deve essere associato al progetto tramite segnali visibili (dominio, repo, nome Worker, UI) oppure tramite il contesto esplicito dell'utente.
- Non riutilizzare un ID D1, bucket R2, AI Search binding, secret name o dominio solo perche sembra simile.
- Dopo ogni cambio di progetto nella conversazione, azzerare mentalmente il contesto operativo precedente e ricostruire la Project Context Card.

---

## 3. Modalita standard di intervento

### Fase A — Discovery read-only
1. identificare progetto;
2. leggere repository e branch;
3. leggere Worker/bindings/versioni Cloudflare;
4. leggere solo metadata D1/R2 necessari;
5. verificare domini e health endpoint;
6. confrontare con `PROJECT_REGISTRY.md`.

### Fase B — Baseline
1. registrare commit/source live;
2. registrare ultima versione Cloudflare;
3. registrare binding critici senza valori dei secret;
4. creare/aggiornare rollback target;
5. per modifiche rischiose, acquisire backup D1/Time Travel bookmark prima della scrittura.

### Fase C — Sviluppo
1. Issue;
2. branch dedicato;
3. modifica minima e focalizzata;
4. test automatici;
5. PR;
6. CI verde.

### Fase D — Staging
1. ambiente e database separati;
2. niente dati cliente reali salvo decisione esplicita;
3. test end-to-end con dati sintetici;
4. nessun binding production riutilizzato accidentalmente.

### Fase E — Production
1. Project Identity Gate ripetuto immediatamente prima del deploy;
2. backup/rollback disponibili;
3. deploy;
4. health check;
5. test funzionali critici;
6. registrazione nuova `LAST_KNOWN_GOOD`.

---

## 4. Incident / Hotfix Mode

Quando production e bloccata:

1. identificare il progetto con fingerprint prima di intervenire;
2. isolare il difetto minimo;
3. evitare refactoring, redesign o migrazioni non necessarie;
4. non toccare moduli protetti non coinvolti;
5. applicare la correzione piu piccola compatibile con i dati esistenti;
6. verificare il percorso utente che era bloccato;
7. subito dopo l'incidente, trasformare il bug in regression test automatico;
8. documentare causa, fix e prevenzione.

Un hotfix non deve diventare un'occasione per cambiare architettura.

---

## 5. Aree protette per progetto

Le aree protette sono specifiche del progetto e devono essere lette dalla scheda fingerprint locale.

Esempi correnti:
- VinoVeritas: e-label normativa e separazione compliance/marketing;
- Splendoria: auth, ownership libri/contenuti, Muse, PDF, dati utenti;
- 247Agent/Copilot Hotel: tenant isolation, KPI, dati hotel, AI source provenance.

Un'area protetta richiede autorizzazione esplicita o una richiesta che la coinvolga chiaramente, piu test di regressione dedicati.

---

## 6. Regole database

- Production D1 non si usa come staging.
- Migrazioni schema solo versionate.
- Nessuna query distruttiva senza backup/recovery path.
- Rollback applicativo e rollback database sono due decisioni separate.
- Non copiare dati personali/cliente in staging per comodita.
- ID del database deve essere verificato prima di ogni migrazione production.

---

## 7. Regole deploy

Un deploy e vietato quando:
- progetto non identificato con fingerprint sufficienti;
- CI e rossa;
- staging richiesto ma non validato;
- rollback target ignoto;
- sorgente GitHub non corrisponde alla baseline live;
- binding production/staging risultano ambigui;
- Cloudflare non e accessibile in modo affidabile e il deploy richiede verifiche live.

Mai pubblicare semplicemente perche un file si chiama `final`, `latest`, `index(7)` o simili.

---

## 8. New Project Onboarding

Ogni nuovo progetto gestito dalla cabina di regia deve ricevere, prima dello sviluppo ordinario:

1. repository GitHub canonico, preferibilmente privato se contiene IP proprietaria;
2. branch `main` normalizzato;
3. `PROJECT_FINGERPRINT.md`;
4. `AGENTS.md`;
5. `GOVERNANCE.md`;
6. `RELEASE_CHECKLIST.md`;
7. CI / quality gate;
8. staging isolato;
9. backup e rollback;
10. health endpoint;
11. security policy;
12. registrazione nel `PROJECT_REGISTRY.md` centrale.

Finche questi elementi non esistono, il progetto e in stato `BOOTSTRAP`, non `MANAGED PRODUCTION`.

---

## 9. Comunicazione con il proprietario del prodotto

All'inizio di un intervento importante indicare chiaramente il progetto, ad esempio:

`Sto lavorando su VINOVERITAS — repo X — Worker Y — D1 Z.`

Non costringere il proprietario a conoscere Git, Wrangler o DevOps. Il proprietario decide prodotto, mercato e rischio; la cabina di regia traduce queste decisioni in workflow tecnico controllato.

Quando serve un gesto manuale, chiedere **una sola azione precisa**, spiegando perche e quale progetto riguarda.

---

## 10. Completion Gate

Un intervento non e concluso finche non sono veri tutti i punti applicabili:

- progetto identificato correttamente;
- modifica tracciata;
- test verdi;
- staging validato quando necessario;
- deploy effettuato sul target corretto;
- health check positivo;
- percorso utente interessato verificato;
- rollback identificato;
- registry/fingerprint aggiornati se l'infrastruttura e cambiata.

**Principio finale: meglio fermare un deploy corretto per eccesso di verifica che pubblicare una modifica corretta sul progetto sbagliato.**
