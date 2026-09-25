# Registro operativo della regia
Aggiornamento: 25 settembre 2026. Registro documentale; non è un lock tecnico, un monitor o un'autorizzazione al rilascio.

## Come usare questo registro
Prima di iniziare, rileggere questo file dalla PR4 della regia e poi il task nel repository privato del prodotto. Lo stato qui è una fotografia: verificare sempre l'ultimo SHA e la consegna del responsabile. Non iniziare un ramo equivalente se un task è già in lavorazione.

Le date commerciali e le evidenze sensibili restano nel piano privato del proprietario. Nessun dettaglio di vulnerabilità o dato cliente va aggiunto qui.

## Priorità e incarichi
Ordine: VinoVeritas, Copilot 247Agent, Sommelier digitale, Splendoria, Sommelier Academy. Il Sommelier è una linea di rilascio distinta nello stesso progetto VinoVeritas.

| Task | Responsabilità effettiva osservata | Perimetro della regia in questo passaggio | Prossimo gate |
|---|---|---|---|
| VV-RELEASE-01 | Sessione regia: analisi della baseline e PR486 | Diagnosi causale e verifica locale; ambiente in sola lettura | Riconciliazione della baseline e qualifica del candidato |
| COP-RELEASE-01 | Sessioni di prodotto su PR577/578/582/583; #580 integrata; regia conserva #581 come tranche isolata | Dipendenze, composizione read-only, evidenze exact-SHA; staging non acquisito | Chiudere review #578/#582, integrare #583/#581 nel candidato unico e riqualificare exact-SHA |
| SOM-RELEASE-01 | Tranche RC5 coordinata, titolare dello staging secondo issue424 | Sola lettura e revisione delle consegne | Qualifica esatta del candidato RC5 corrente |
| SPL-RELEASE-01 | Sessioni di prodotto conservate; regia prepara un controllo locale | Preflight offline verificato; esclusione nativa del solo ramo regia applicata e riletta, senza push applicativo | Altre automazioni e ambiente isolato da verificare |
| ACA-CHRISTMAS-01 | Sessione Academy titolare del Master; regia supporta prerequisiti | Ricognizione accessi e dipendenze, nessun bootstrap parallelo | Sorgente riproducibile e target staging qualificabile |

Le sessioni di prodotto non sono sub-agenti controllabili da questo registro. Le assegnazioni della regia riguardano i propri sotto-incarichi; una nuova sessione deve confermare nel task privato l'adozione di un incarico senza sovrascrivere la titolarità esistente.

## Riferimenti di riconciliazione
- VinoVeritas: PR486, sorgente candidato `00b8a9e6ab0a1b31942df87f015d84f718d5fc4d`; non è una release produttiva.
- Copilot: `main ce3842e22d29409aa0a7217ff0b4484fa3af8422` include #580. PR583 head `7ad7150deb55e13f27a83a435ff7c1845f8204c1` ha qualification reale Workers AI/Kimi PASS e tutti i workflow PASS dopo rerun same-SHA del flake #572; resta review in corso. PR581 head `899a17c61a70b1226ea0618265a7222d87a6750a` mantiene evidenza valida solo per la tranche scheduler CAS ed è INVALIDATA_DA_DRIFT per la composizione finché non viene ricomposta sul candidato corrente.
- Sommelier: PR487 integrata nel branch `release/sommelier-intent-routing-424-rc5-20260925`, candidato osservato `4a5d09381056cee7257ef0a9dc3ba38d8b7023fd`. Le precedenti RC restano evidenze storiche.
- Splendoria: le patch locali non sono una release; consultare il pacchetto privato della regia e l'ultima baseline canonica.
- Academy: Master canonico v0.18; distinguere progettazione, baseline locale e qualifica runtime.

## Regole immediate contro le sovrapposizioni
1. Sommelier: rispettare la titolarità dello staging registrata in issue424. La sessione indipendente ha già ceduto la mutazione e opera in review. Non ripetere deploy o rollback mentre quella qualifica è aperta.
2. Copilot: #580 è integrata e la qualifica successiva è PR583. Non comporre la release finché PR578 non è review-clean o esplicitamente esclusa; PR582 sostituisce #574 ma ha finding di policy/ordine aperti, quindi PR577 resta dependency-blocked. Ricomporre infine la tranche scheduler di PR581 sul candidato corrente e ripetere tutte le prove sul nuovo exact SHA. Non trasferire evidenze da PR576/569 o da altri commit.
3. VinoVeritas: mantenere distinta PR486 dalla riconciliazione della baseline e dal rilascio Sommelier. Un controllo rosso va spiegato prima di cambiarlo.
4. Splendoria: il controllo locale non autorizza una push, un deploy o una migrazione. Verificare gli effetti automatici prima della consegna remota.
5. Academy: usare il Master e il handoff PostgreSQL esistenti; nessun database di altro progetto come sostituto.

## Consegna minima per ciascun task
- Base e candidato esatti, file e funzione interessati.
- Risultato richiesto e superfici preservate.
- Ambiente e responsabile di eventuali mutazioni.
- Test positivi e negativi sullo stesso candidato, con log e limiti.
- Dipendenze, prossimo gate, rollback e stato con timestamp.
- Link alla prova nel repository privato; nessun contenuto sensibile copiato qui.

## Criterio di chiusura
Preparato localmente, CI verde, qualificato in staging e pubblicato/verificato sono stati distinti. La chiusura richiede le prove appropriate al perimetro. Un conflitto risolto o una somma di test verdi non dimostrano che la release combinata funzioni.

Alla fine di ogni tranche il responsabile aggiorna il task privato. La regia riconcilia questo registro durante le sessioni attive; non è installata una sincronizzazione continua.
