<p align="center">
  <img src="assets/iris.gif" width="170" alt="IRIS" />
</p>

<h1 align="center">Mahes Omprakash</h1>

<p align="center">
  <strong>Entwickler für KI-Integration und Automatisierung</strong><br/>
  <a href="https://suntsun.github.io">suntsun.github.io</a>
</p>

<p align="center">
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.md">Español</a> ·
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.en.md">English</a> ·
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.it.md">Italiano</a> ·
  <strong>Deutsch</strong>
</p>

---

Erfahrung mit Lösungen der Künstlichen Intelligenz für Unternehmen im laufenden Betrieb: **Agentic-AI**-Systeme, Integration und Orchestrierung von **LLMs**, **RAG**-Architekturen, Prozessautomatisierung, **API**-Entwicklung, Anpassung von **ERP-Systemen** und Automatisierung für **Social Media**.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![SQL](https://img.shields.io/badge/SQL-003B57?style=flat-square&logo=databricks&logoColor=white) ![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white) ![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?style=flat-square&logo=claude&logoColor=white) ![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square&logo=groq&logoColor=white) ![Llama](https://img.shields.io/badge/Llama-0866FF?style=flat-square&logo=meta&logoColor=white) ![Qwen](https://img.shields.io/badge/Qwen-615CED?style=flat-square&logo=alibabacloud&logoColor=white) ![Mistral](https://img.shields.io/badge/Mistral-FA520F?style=flat-square&logo=mistralai&logoColor=white) ![Obsidian](https://img.shields.io/badge/Obsidian-7C3AED?style=flat-square&logo=obsidian&logoColor=white)

---
## Ausgewählte Projekte

### 🏰 El Castillo — Systemassistent mit abgeriegelten Berechtigungen

Ein Assistent, mit dem ich in natürlicher Sprache 26 Automatisierungen auf meinem eigenen Linux-Rechner steuere.

Interessant ist, was er **nicht** kann. Das Modell führt nie etwas von sich aus aus: Es schlägt lediglich vor, was es starten möchte, und eine unabhängige Schicht — von Hand geschrieben, ohne KI — prüft diesen Vorschlag gegen eine geschlossene Liste erlaubter Operationen. Was nicht auf der Liste steht, wird abgewiesen. Jeder Versuch, zugelassen oder abgelehnt, wird protokolliert.

Das eigentliche Problem: ein Modell an ein reales Betriebssystem zu lassen, ohne ihm die Kontrolle über die Maschine zu schenken. Die Lösung war, nach Ebenen zu trennen, was jeder Teil darf, heikle Operationen über einen eigenen Pfad zu führen und alles, was dort durchläuft, automatisch zu kennzeichnen. Sicherheit steckt in den Berechtigungen des Systems, nicht in einer Anweisung im Prompt: Einen Prompt kann man überreden, eine verweigerte Berechtigung nicht.

Das Muster hängt nicht an Linux: Hier läuft es auf meinem Rechner, funktioniert aber für jedes System. Es erlaubt, größeren oder leistungsfähigeren Modellen wie Claude oder Codex klare Grenzen und Handlungsräume zu setzen.

Python mit reiner Standardbibliothek · 440 Tests im Orchestrator · 1.179 im gesamten Ökosystem

[Repository ansehen](https://github.com/Suntsun/el-castillo)

---

### 🤖 Eine Flotte von KI-Agenten auf einem ERP — Fallstudie

Sieben dialogfähige Agenten, die innerhalb von Odoo leben:

- **Sara — Personalwesen.** Nimmt Bewerbungen per E-Mail, WhatsApp und Webformular entgegen, extrahiert die Daten aus dem Lebenslauf, prüft sie gegen die Anforderungen der Stelle und terminiert die Vorstellungsgespräche.
- **Emilio — Personaladministration.** An- und Abmeldungen bei der Sozialversicherung, Erzeugung der amtlichen Meldedateien und Übermittlung der Arbeitsverträge an die Arbeitsverwaltung.
- **Lara — Business Intelligence.** Beobachtet Amtsblätter und Presse — Handelsregister, öffentliche Vergaben, Fördermittel — und meldet, was das Geschäft betrifft. Nach Branche der jeweiligen Firma konfigurierbar.
- **Smith — Ausschreibungen.** Verfolgt öffentliche Vergabeverfahren, sortiert nach objektiven Kriterien aus, was nicht passt, und bereitet die Angebotsunterlagen vor.
- **Lia — Logistik.** Bestände, Lieferrouten, Frachtführer, Servicekennzahlen des Lagers und Echtzeitüberwachung der unterwegs befindlichen Flotte auf einer Karte.
- **Samy — Vertrieb.** CRM-Pipeline, Priorisierung von Opportunities, Hinweis auf abkühlende Abschlüsse und Nachverfolgung der Zahlungseingänge.
- **Marina — Technische Instandhaltung.** Anlagen der Wasseraufbereitung: Arbeitsberichte im Außendienst und technischer Kundendienst.

Zwei Entscheidungen, die das Projekt verändert haben:

- **Die menschliche Bestätigung steckt im Code, nicht im Prompt.** Anfangs bat ich das Modell schlicht darum, nichts ohne Freigabe zu verschicken. Ein internes Audit machte klar, dass das nicht reicht: Die Prüfung sitzt jetzt an der Stelle, an der das ERP die Daten schreibt, und der Agent kommt nicht daran vorbei, so sehr man ihn auch drängt.
- **Der Agent schlägt vor, der Code entscheidet.** Ich habe dem Modell das direkte Schreiben ins ERP entzogen. Es liefert nun sein Ergebnis, der Code validiert es, und der Code ist es, der speichert. Die sporadischen Fehler verschwanden, und der Vorgang ging von Minuten auf Sekunden zurück.

Der Quellcode gehört dem Kunden. Ich dokumentiere die Architektur, die technischen Entscheidungen und die Ergebnisse, nicht jedoch den Quellcode.

---

### 🎬 IRIS — Agent für Content-Erstellung per Chat

Ein in Odoo eingebetteter Agent, mit dem man über einen Chat spricht. Man bittet ihn um einen Beitrag, und er erledigt den Rest: Er schreibt das Skript, erzeugt das Video mit synthetischem Avatar und synthetischer Stimme, untertitelt es, fügt das B-Roll-Material hinzu, legt es zur Freigabe vor und veröffentlicht es auf Instagram.

Odoo ist der Kern, n8n die Integrationsschicht mit über 95 Nodes, und ein eigener Server übernimmt die Postproduktion in einer isolierten Umgebung.

Ende-zu-Ende verifiziert mit realen Veröffentlichungen.

**Kontrolle darüber, was veröffentlicht wird.** Sieben Prüfungen verhindern, dass eine unbestätigte Zahl nach außen geht — einschließlich einer OCR-Auswertung des fertig montierten Videos.

[Repository ansehen](https://github.com/Suntsun/iris-pipeline-contenido)

---

### ⚙️ System Captain — Multi-Agenten-Orchestrierung

Eine Steuerungsebene, die mehr als 15 spezialisierte Agenten koordiniert, jeder mit genau einer Verantwortung: Einer baut, einer testet als realer Nutzer, einer auditiert auf der Suche nach Fehlern, einer prüft den Code.
Geregelt wird sie durch eine geschriebene Verfassung (Hard Rules) und einen persistenten Speicher (Contextual RAG), in den nur ein einziger Agent schreiben darf.

**Warum das zählt:** Die gegenseitige Prüfung fand immer wieder Mängel, die ein einzelner Entwicklungsdurchlauf durchgelassen hätte — Sicherheitskontrollen, die nur im Prompt existierten, fälschlich gemeldete Erfolge, falsch kalibrierte Timeouts.

Das ist nicht bloß ein Orchestrierungssystem: Es ist das Rückgrat meiner Arbeitsweise.

Praktisch heißt das: Jeder Agent arbeitet nur mit dem Kontext seiner eigenen Aufgabe, statt das gesamte Gespräch mitzuschleppen, und kein Arbeitsergebnis gilt als fertig, ohne eine Einheit durchlaufen zu haben, die es nicht selbst geschrieben hat. Das hält die Kosten im Rahmen und verhindert, dass sich Korrekturen auf einem Fehler stapeln, den niemand rechtzeitig bemerkt hat.

Es ist dasselbe Argument, das das Applied-AI-Team von Anthropic vertritt: [in einem Produktivsystem ist nicht mehr das Modell der begrenzende Faktor, sondern die Struktur, die es umgibt](https://www.youtube.com/watch?v=K0X9QDRkIdg).

---

## Arbeitsweise

Ich arbeite modular, mit Skalierbarkeit als Regel: Jedes Teil muss wachsen oder ersetzt werden können, ohne den Rest mitzureißen.

Bevor ich ein Projekt abschließe, führe ich Funktions-Audits und Sicherheitstests durch und liefere sie als abschließenden Teil der Arbeit mit.

Die Aufzeichnungen zu jedem Projekt pflege ich in eigenen Datenbanken, mit einem eigenen RAG-System, das ich während der Entwicklung abfrage. Ins Repository wandert das Ergebnis; das Wissen des Projekts bleibt geordnet und für das nächste verfügbar.

---

## Stack

**Sprachen** · Python · Java · SQL · Bash
**Plattformen** · Odoo (Modelle, ORM, QWeb, OWL) · PostgreSQL · n8n · systemd
**Integration** · XML-RPC · REST · SOAP · Webhooks · Meta Graph API · amtliche Dateien mit fester Satzlänge
**Angewandte KI** · Claude Code · LLM-basierte Agenten (Llama, Qwen, Mistral, über Groq und lokale Modelle) · Function Calling und validierte JSON-Abläufe · RAG und Dokumentenextraktion · Halluzinationskontrolle mit Golden Sets
**Werkzeuge** · Obsidian als Wissensbasis · Linux (Arch/Hyprland) · Docker · Sandboxing mit bwrap · CI/CD

---

## Naturschutz, Wissenschaft und Technik

Als persönliche Initiative arbeite ich ehrenamtlich an gemeinnützigen Projekten in den Bereichen Naturschutz, wissenschaftliche Forschung und Wissensvermittlung mit.

Ich kann Backend-Entwicklung, Prozessautomatisierung, Datenverarbeitung und -visualisierung, APIs, Webanwendungen, interaktive Karten und die Integration von Werkzeugen beisteuern.

Die Entwicklung erfolgt kostenlos, sofern das Projekt einen echten, nicht kommerziellen Zweck und einen tragbaren Umfang hat. Jeder Vorschlag wird nach technischem Bedarf, Nutzen und meiner Verfügbarkeit bewertet.

Wenn Sie Teil eines Vereins, einer Forschungsgruppe oder einer Naturschutzinitiative sind und technische Unterstützung brauchen, schreiben Sie mir gern an die unten genannte Kontaktadresse.

---

## Kontakt

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mahes-sunsun-es250206) [![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mrm.sunsun@gmail.com)

*Offen für Möglichkeiten in KI-Integration, Prozessautomatisierung und Backend-Entwicklung.*
