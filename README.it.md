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

Esperienza in soluzioni di Intelligenza Artificiale applicate ad aziende già operative: sistemi **Agentic AI**, integrazione e orchestrazione di **LLM**, architetture **RAG**, automazione dei processi, sviluppo di **API**, personalizzazione di **ERP** e automazione per i **social media**.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![SQL](https://img.shields.io/badge/SQL-003B57?style=flat-square&logo=databricks&logoColor=white) ![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white) ![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?style=flat-square&logo=claude&logoColor=white) ![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square&logo=groq&logoColor=white) ![Llama](https://img.shields.io/badge/Llama-0866FF?style=flat-square&logo=meta&logoColor=white) ![Qwen](https://img.shields.io/badge/Qwen-615CED?style=flat-square&logo=alibabacloud&logoColor=white) ![Mistral](https://img.shields.io/badge/Mistral-FA520F?style=flat-square&logo=mistralai&logoColor=white) ![Obsidian](https://img.shields.io/badge/Obsidian-7C3AED?style=flat-square&logo=obsidian&logoColor=white)

---
## Progetti in evidenza

### 🏰 El Castillo — assistente di sistema con permessi blindati

Un assistente con cui parlo in linguaggio naturale per gestire 26 automazioni sulla mia macchina Linux.

La parte interessante è ciò che **non** può fare. Il modello non esegue mai nulla di propria iniziativa: si limita a proporre ciò che vorrebbe lanciare, e un livello indipendente — scritto a mano, senza IA — verifica quella proposta rispetto a un elenco chiuso di operazioni consentite. Ciò che non è nell'elenco viene rifiutato. Ogni tentativo, accolto o negato, viene registrato.

Il problema di fondo è lasciare che un modello tocchi un sistema operativo reale senza regalargli il controllo della macchina. La soluzione è stata separare per livelli ciò che ciascuna parte può fare, riservare le operazioni delicate a un circuito a parte e marcare automaticamente tutto ciò che vi transita. La sicurezza risiede nei permessi del sistema, non in un'istruzione dentro il prompt: un prompt si può convincere, un permesso negato no.

Lo schema non dipende da Linux: qui è applicato alla mia macchina, ma funziona per qualsiasi sistema. Permette di porre limiti e confini d'azione a modelli più estesi o complessi, come Claude o Codex.

Python con sola libreria standard · 440 test nell'orchestratore · 1.179 nell'intero ecosistema

[Vedi repository](https://github.com/Suntsun/el-castillo)

---

### 🤖 Flotta di agenti IA su ERP — caso di studio

Sette agenti conversazionali che vivono dentro Odoo:

- **Sara — Risorse Umane.** Raccoglie le candidature via email, WhatsApp e modulo web, estrae i dati dal CV, effettua la selezione in base ai requisiti della posizione e fissa i colloqui.
- **Emilio — Amministrazione del personale.** Aperture e chiusure di posizione previdenziale, generazione dei file ufficiali di affiliazione e comunicazione dei contratti all'ente pubblico per l'impiego.
- **Lara — Business intelligence.** Sorveglia bollettini ufficiali e stampa — registro delle imprese, appalti pubblici, contributi — e segnala ciò che incide sull'attività. Si configura in base al settore dell'azienda.
- **Smith — Gare d'appalto.** Monitora gli appalti pubblici, scarta ciò che non rientra secondo criteri oggettivi e prepara la documentazione dell'offerta.
- **Lia — Logistica.** Giacenze, rotte di consegna, vettori, indicatori di servizio del magazzino e monitoraggio in tempo reale su una mappa con la flotta in circolazione.
- **Samy — Commerciale.** Pipeline CRM, prioritizzazione delle opportunità, avviso su quelle che si raffreddano e monitoraggio degli incassi.
- **Marina — Manutenzione tecnica.** Impianti di trattamento acque: rapportini di lavoro sul campo e servizio di assistenza tecnica.

Due decisioni che hanno cambiato il progetto:

- **La conferma umana risiede nel codice, non nel prompt.** All'inizio chiedevo semplicemente al modello di non inviare nulla senza permesso. Un audit interno ha reso evidente che non basta: ora il controllo si trova nel punto in cui l'ERP scrive i dati, e l'agente non può aggirarlo per quanto glielo si chieda.
- **L'agente propone, il codice decide.** Ho smesso di permettere al modello di scrivere direttamente nell'ERP. Ora restituisce la sua conclusione, il codice la convalida ed è il codice a salvare. I guasti intermittenti sono spariti e il processo è passato da minuti a secondi.

Il codice appartiene al cliente. Documento l'architettura, le decisioni tecniche e i risultati, ma non il codice sorgente.

---

### 🎬 IRIS — agente di creazione contenuti dalla chat

Un agente integrato in Odoo con cui si parla in chat. Gli chiedi una pubblicazione e pensa lui al resto: scrive il copione, genera il video con avatar e voce sintetica, lo sottotitola, aggiunge il b-roll, te lo sottopone per l'approvazione e lo pubblica su Instagram.

Odoo è il nucleo, n8n il livello di integrazione con oltre 95 nodi, e un server dedicato esegue la post-produzione in un ambiente isolato.

Verificato dall'inizio alla fine con pubblicazioni reali.

**Controllo di ciò che viene pubblicato.** Sette verifiche impediscono che esca un dato non verificato, inclusa una lettura OCR del video già montato.

[Vedi repository](https://github.com/Suntsun/iris-pipeline-contenido)

---

### 🌤️ Sunny — un assistente che usa il computer senza controllarlo

Gli scrivi quello che vuoi fare —spostare dei file, cercare documenti vuoti, aprire un programma— e lo fa. Tutto sulla macchina stessa, senza che esca nessun dato.

È l'idea di El Castillo portata sulla scrivania. Il modello capisce il comando e pianifica, ma non tocca niente: restituisce un piano in JSON che viene validato contro un elenco chiuso di azioni, e solo allora si esegue. Se un'azione cancella o sovrascrive, chiede prima.

Per leggere lo schermo usa OCR vero, non un modello di visione. Un modello di visione può descriverti testo che nell'immagine non c'è, e quell'invenzione diventerebbe un'azione reale sui tuoi file. Preferisco perdere flessibilità piuttosto che cancellare il file sbagliato.

Cinque fornitori di modello dietro una sola interfaccia (Ollama in locale, Groq, Cerebras, Anthropic, Gemini), con una catena di riserva che distingue il guasto passeggero da quello definitivo.

Python · 786 test su Windows, la sua piattaforma nativa · 622 in verde riproducendo la suite su Linux, dove i 15 fallimenti restanti sono chiamate proprie di Windows

[Vedi il codice](https://github.com/Suntsun/sunny) · [Caso di studio](https://github.com/Suntsun/sunny-rpa-local)

---

### ⚙️ Sistema Captain — orchestrazione multi-agente

Un livello di comando che coordina più di 15 agenti specializzati, ciascuno con una sola responsabilità: uno costruisce, uno collauda come utente reale, uno esegue un audit a caccia di difetti, uno revisiona il codice.
È governato da una costituzione scritta (hard rules) e da una memoria persistente (contextual RAG) su cui un solo agente ha il permesso di scrittura.

**Perché è rilevante:** l'audit incrociato ha individuato più volte difetti che una singola passata di sviluppo avrebbe lasciato passare — controlli di sicurezza esistenti solo nel prompt, falsi successi riportati all'utente, timeout mal calibrati.

Non è soltanto un sistema di orchestrazione: è l'ossatura del mio metodo di lavoro.

In concreto, ogni agente lavora solo con il contesto del proprio compito invece di trascinarsi dietro l'intera conversazione, e nessun lavoro viene dato per buono senza passare da un'unità che non l'ha scritto. Questo contiene la spesa ed evita di accumulare correzioni sopra un errore che nessuno ha intercettato in tempo.

È lo stesso argomento sostenuto dal team Applied AI di Anthropic: [in un sistema in produzione il fattore limitante non è più il modello, ma la struttura che lo avvolge](https://www.youtube.com/watch?v=K0X9QDRkIdg).

---

## Metodo di lavoro

Lavoro con un approccio modulare e la scalabilità come regola: ogni pezzo deve poter crescere o essere sostituito senza trascinarsi dietro il resto.

Prima di chiudere un progetto eseguo audit di funzionamento e test di sicurezza, e li consegno come parte finale del lavoro.

Tengo traccia di ogni progetto nei miei database, con un sistema RAG personale che consulto mentre sviluppo. Nel repository finisce il risultato; la conoscenza del progetto resta ordinata e pronta per il successivo.

---

## Stack

**Linguaggi** · Python · Java · SQL · Bash

**Piattaforme** · Odoo (modelli, ORM, QWeb, OWL) · PostgreSQL · n8n · systemd

**Integrazione** · XML-RPC · REST · SOAP · Webhook · Meta Graph API · file ufficiali a larghezza fissa

**IA applicata** · Claude Code · agenti basati su LLM (Llama, Qwen, Mistral, tramite Groq e modelli locali) · function calling e flussi JSON convalidati · RAG ed estrazione documentale · controllo delle allucinazioni con golden set

**Work tools** · Obsidian come base di conoscenza · Linux (Arch/Hyprland) · Docker · sandboxing con bwrap · CI/CD

---

## Conservazione, scienza e tecnologia

Come iniziativa personale, collaboro come volontario a progetti non profit legati alla conservazione della natura, alla ricerca scientifica e alla divulgazione.

Posso contribuire con sviluppo backend, automazione dei processi, elaborazione e visualizzazione di dati, API, applicazioni web, mappe interattive e integrazione di strumenti.

Lo sviluppo è a titolo gratuito, purché il progetto abbia una finalità reale, non commerciale e una portata sostenibile. Ogni proposta viene valutata in base alle esigenze tecniche, all'utilità e alla mia disponibilità.

Se fai parte di un'associazione, di un gruppo scientifico o di un'iniziativa di conservazione e hai bisogno di supporto tecnico, puoi scrivermi all'indirizzo di contatto qui sotto.

---

## Contatti

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mahes-sunsun-es250206) [![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mrm.sunsun@gmail.com)

*Disponibile a opportunità in integrazione IA, automazione dei processi e sviluppo backend.*
