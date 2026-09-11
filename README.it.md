<p align="center">
  <img src="assets/iris.gif" width="170" alt="IRIS" />
</p>

<h1 align="center">Mahes Omprakash</h1>

<p align="center">
  <strong>Sviluppatore di integrazione IA e automazione</strong><br/>
  <a href="https://suntsun.github.io">suntsun.github.io</a>
</p>

<p align="center">
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.md">Español</a> ·
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.en.md">English</a> ·
  <strong>Italiano</strong> ·
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.de.md">Deutsch</a>
</p>

---

Esperienza nello sviluppo di agenti IA integrati in sistemi già in produzione: ERP, API di terze parti, generazione di file ufficiali e automazione della pubblicazione sui social.

Gli agenti eseguono azioni reali sul database — creano record, fanno avanzare processi, generano documentazione — con permessi circoscritti, conferma umana implementata a livello di ORM e tracciabilità completa di ogni operazione.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## Di cosa mi occupo

Integro agenti IA e automazioni in sistemi reali, già in esercizio.
Lavoro principalmente con Python, Odoo, PostgreSQL, n8n e Linux.

---

## Progetti in evidenza

### 🏰 El Castillo — automazioni Linux con orchestratore conversazionale governato

Sistema di 26 automazioni controllate tramite linguaggio naturale. L'LLM non può eseguire comandi direttamente: si limita a proporre {binario, argomenti} e un livello indipendente convalida ogni richiesta rispetto a una lista chiusa di comandi consentiti.

L'esecuzione usa shell=False, rifiuta i metacaratteri, limita il numero di operazioni e registra ogni tentativo in un audit log JSONL.

Python — solo libreria standard · systemd · unittest
440 test nell'orchestratore · 1.179 test nell'intero ecosistema

Problema centrale: consentire a un modello linguistico di interagire con un sistema Linux reale senza aprire una via di escalation dei privilegi. La sicurezza è applicata a livello di processo e di permessi, non tramite istruzioni nel prompt.

[Vedi repository](https://github.com/Suntsun/el-castillo)

---

### 🤖 Agenti IA su ERP — caso di studio

Architettura di una flotta di agenti conversazionali integrati in Odoo che eseguono operazioni reali sull'ERP. Condividono uno schema comune: modelli di dati dedicati, capacità di dominio, utente di servizio con permessi espliciti e tracciabilità documentale.

Risultati misurati:

| Metrica | Valore |
| --- | --- |
| Estrazione di CV su golden set avversariale | 14 casi, 0 allucinazioni |
| Scritture verificate direttamente nell'ERP | 930, nessuna discrepanza |
| Latenza dopo la riprogettazione del flusso | 90–200 s → 8,3 s in media |
| Test per progetto | 625 · 511 · 300 · 94 |

Decisioni di progettazione rilevanti:

- **Conferma umana a livello di ORM.** La prima versione governava gli invii tramite istruzioni al modello. Dopo un audit interno, il controllo è stato spostato in guardie su `create()` e `write()`, dove l'agente non può aggirarlo.
- **Inversione del flusso di scrittura.** Il modello ha smesso di modificare direttamente l'ERP e restituisce invece un verdetto JSON. Il codice convalida quel risultato ed esegue la persistenza in modo sincrono, eliminando i fallimenti intermittenti e riducendo la latenza di un ordine di grandezza.

Il codice sorgente appartiene al cliente. Vengono documentati l'architettura, le decisioni tecniche e i risultati, ma non il codice.

---

### 🎬 IRIS — pipeline di contenuti automatizzata

Pipeline di pubblicazione che trasforma una richiesta in linguaggio naturale in un post reale su Instagram: generazione dello script, video con avatar e voce sintetica, sottotitolazione, inserimento di b-roll, approvazione umana e pubblicazione finale.

Odoo funge da nucleo del sistema, n8n da livello di integrazione con oltre 95 nodi, e un runner dedicato su VPS esegue la post-produzione in un ambiente isolato tramite bwrap.

Verificata end-to-end con pubblicazioni reali su Instagram.

Decisioni tecniche rilevanti:

- **Validazione nell'ambiente reale.** La sandbox è stata testata direttamente sul server di produzione, dove sono emersi due guasti non riproducibili in locale che potevano bloccare la pipeline senza un segnale chiaro.
- **Controllo dei contenuti generati.** Il sistema integra sette gate di validazione per impedire la pubblicazione di dati non verificati, inclusa una verifica OCR sul render finale.

[Vedi repository](https://github.com/Suntsun/iris-pipeline-contenido)

---

### ⚙️ Sistema Captain — orchestrazione multi-agente

Livello di comando che coordina più di 15 agenti specializzati a responsabilità singola: uno costruisce, uno collauda come utente reale, uno esegue un audit avversariale, uno revisiona il diff. Governato da una costituzione scritta e da una memoria persistente in Markdown su cui un solo agente è autorizzato a scrivere.

**Perché è rilevante:** lo schema di audit incrociato ha individuato ripetutamente difetti che una singola passata di sviluppo non avrebbe colto — gate di sicurezza implementati solo nel prompt, falsi successi riportati all'utente, timeout mal calibrati.

---

## Metodo di lavoro

- **Verifica sul database**, non sul report del sistema stesso: i numeri che pubblico sono contati, non stimati.
- **Test come parte del deliverable**, non come fase successiva. Ogni progetto include la propria suite.
- **Validazione nell'ambiente di destinazione.** I guasti che contano tendono a emergere sul server, non in locale.
- **Sicurezza applicata ai sistemi con IA**: permessi negati per impostazione predefinita, conferma umana nel codice, tracciabilità completa e revisione avversariale prima del rilascio.

---

## Stack

**Linguaggi** · Python · Java · SQL · Bash
**Piattaforme** · Odoo (modelli, ORM, QWeb, OWL) · PostgreSQL · n8n · systemd
**Integrazione** · XML-RPC · REST · SOAP · Webhook · Meta Graph API · file ufficiali a larghezza fissa
**IA applicata** · agenti basati su LLM · function calling e flussi JSON convalidati · RAG ed estrazione documentale · controllo delle allucinazioni con golden set
**Sistemi** · Linux (Arch/Hyprland) · Docker · sandboxing con bwrap · CI/CD

---

## Conservazione, scienza e tecnologia

Come iniziativa personale, collaboro come volontario a progetti non profit legati alla conservazione della natura, alla ricerca scientifica e alla divulgazione.

Posso contribuire con sviluppo backend, automazione dei processi, elaborazione e visualizzazione di dati, API, applicazioni web, mappe interattive e integrazione di strumenti.

Lo sviluppo è a titolo gratuito, purché il progetto abbia una finalità reale, non commerciale e una portata sostenibile. Ogni proposta viene valutata in base alle esigenze tecniche, all'utilità e alla mia disponibilità.

Se fai parte di un'associazione, di un gruppo scientifico o di un'iniziativa di conservazione e hai bisogno di supporto tecnologico, puoi contattarmi via email (nei contatti in fondo) o su Instagram (account dedicato ai progetti di biologia): @zurtopia_

---

## Contatti

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mahes-sunsun-es250206)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mrm.sunsun@gmail.com)

*Disponibile a opportunità in integrazione IA, automazione dei processi e sviluppo backend.*
