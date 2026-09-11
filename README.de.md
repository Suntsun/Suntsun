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

Erfahrung in der Entwicklung von KI-Agenten, die in produktiv laufende Systeme integriert sind: ERP-Systeme, Drittanbieter-APIs, Erzeugung amtlicher Dateien und automatisiertes Veröffentlichen in sozialen Netzwerken.

Die Agenten führen reale Aktionen auf der Datenbank aus — sie legen Datensätze an, treiben Prozesse voran, erzeugen Dokumentation — mit eng gefassten Berechtigungen, menschlicher Bestätigung auf ORM-Ebene und vollständiger Nachvollziehbarkeit jeder Operation.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## Was ich mache

Ich integriere KI-Agenten und Automatisierungen in reale, laufende Systeme.
Ich arbeite überwiegend mit Python, Odoo, PostgreSQL, n8n und Linux.

---

## Ausgewählte Projekte

### 🏰 El Castillo — Linux-Automatisierung mit kontrolliertem dialogfähigem Orchestrator

System aus 26 Automatisierungen, gesteuert über natürliche Sprache. Das LLM kann keine Befehle direkt ausführen: Es schlägt lediglich {Binary, Argumente} vor, und eine unabhängige Schicht prüft jede Anfrage gegen eine geschlossene Liste zulässiger Befehle.

Die Ausführung nutzt shell=False, weist Metazeichen ab, begrenzt die Anzahl der Operationen und protokolliert jeden Versuch in einem JSONL-Audit-Log.

Python — reine Standardbibliothek · systemd · unittest
440 Tests im Orchestrator · 1.179 Tests im gesamten Ökosystem

Kernproblem: einem Sprachmodell die Interaktion mit einem realen Linux-System zu erlauben, ohne einen Pfad zur Rechteausweitung zu öffnen. Sicherheit wird auf Prozess- und Berechtigungsebene durchgesetzt, nicht über Anweisungen im Prompt.

[Repository ansehen](https://github.com/Suntsun/el-castillo)

---

### 🤖 KI-Agenten auf einem ERP — Fallstudie

Architektur einer Flotte dialogfähiger Agenten, die in Odoo eingebettet sind und reale Operationen im ERP ausführen. Sie folgen einem gemeinsamen Muster: eigene Datenmodelle, fachliche Fähigkeiten, ein Servicebenutzer mit expliziten Berechtigungen und dokumentenbasierte Nachvollziehbarkeit.

Gemessene Ergebnisse:

| Kennzahl | Wert |
| --- | --- |
| Lebenslauf-Extraktion gegen ein adversariales Golden Set | 14 Fälle, 0 Halluzinationen |
| Direkt im ERP verifizierte Schreibvorgänge | 930, ohne Abweichungen |
| Latenz nach dem Redesign des Ablaufs | 90–200 s → 8,3 s im Mittel |
| Tests pro Projekt | 625 · 511 · 300 · 94 |

Wesentliche Designentscheidungen:

- **Menschliche Bestätigung auf ORM-Ebene.** Die erste Version steuerte ausgehende Aktionen über Anweisungen an das Modell. Nach einem internen Audit wurde die Kontrolle in Guards in `create()` und `write()` verlagert, wo der Agent sie nicht umgehen kann.
- **Umkehrung des Schreibflusses.** Das Modell verändert das ERP nicht mehr direkt, sondern liefert ein JSON-Urteil zurück. Der Code validiert dieses Ergebnis und schreibt synchron, wodurch sporadische Fehler entfielen und die Latenz um eine Größenordnung sank.

Der Quellcode gehört dem Kunden. Dokumentiert werden Architektur, technische Entscheidungen und Ergebnisse, nicht jedoch der Quellcode.

---

### 🎬 IRIS — automatisierte Content-Pipeline

Publishing-Pipeline, die eine Anfrage in natürlicher Sprache in einen realen Instagram-Beitrag überführt: Skripterstellung, Video mit Avatar und synthetischer Stimme, Untertitelung, Einbindung von B-Roll, menschliche Freigabe und finale Veröffentlichung.

Odoo bildet den Kern des Systems, n8n die Integrationsschicht mit über 95 Nodes, und ein eigener Runner auf einem VPS führt die Postproduktion in einer über bwrap isolierten Umgebung aus.

Ende-zu-Ende verifiziert mit realen Veröffentlichungen auf Instagram.

Wesentliche technische Entscheidungen:

- **Validierung in der realen Umgebung.** Die Sandbox wurde direkt auf dem Produktionsserver geprüft, wo zwei Fehler auftraten, die sich lokal nicht reproduzieren ließen und die Pipeline ohne klares Signal blockieren konnten.
- **Kontrolle generierter Inhalte.** Das System enthält sieben Validierungs-Gates, die die Veröffentlichung nicht verifizierter Zahlen verhindern, einschließlich einer OCR-Prüfung des finalen Renderings.

[Repository ansehen](https://github.com/Suntsun/iris-pipeline-contenido)

---

### ⚙️ System Captain — Multi-Agenten-Orchestrierung

Eine Steuerungsebene, die mehr als 15 spezialisierte Agenten mit jeweils einer einzigen Verantwortung koordiniert: einer baut, einer testet als realer Nutzer, einer auditiert adversarial, einer prüft das Diff. Geregelt durch eine geschriebene Verfassung und einen persistenten Markdown-Speicher, in den nur ein einziger Agent schreiben darf.

**Warum das zählt:** Das Muster der gegenseitigen Prüfung deckte wiederholt Mängel auf, die ein einzelner Entwicklungsdurchlauf nicht erfasst hätte — Sicherheits-Gates, die nur im Prompt umgesetzt waren, fälschlich gemeldete Erfolge, falsch kalibrierte Timeouts.

---

## Arbeitsweise

- **Verifikation gegen die Datenbank**, nicht gegen den Bericht des Systems selbst: Die Zahlen, die ich veröffentliche, sind gezählt, nicht geschätzt.
- **Tests als Teil des Liefergegenstands**, nicht als nachgelagerte Phase. Jedes Projekt bringt seine Suite mit.
- **Validierung in der Zielumgebung.** Die Fehler, auf die es ankommt, treten meist auf dem Server auf, nicht lokal.
- **Sicherheit für KI-gestützte Systeme**: Berechtigungen standardmäßig verweigert, menschliche Bestätigung im Code verankert, vollständige Nachvollziehbarkeit und adversariale Prüfung vor dem Deployment.

---

## Stack

**Sprachen** · Python · Java · SQL · Bash
**Plattformen** · Odoo (Modelle, ORM, QWeb, OWL) · PostgreSQL · n8n · systemd
**Integration** · XML-RPC · REST · SOAP · Webhooks · Meta Graph API · amtliche Dateien mit fester Satzlänge
**Angewandte KI** · LLM-basierte Agenten · Function Calling und validierte JSON-Abläufe · RAG und Dokumentenextraktion · Halluzinationskontrolle mit Golden Sets
**Systeme** · Linux (Arch/Hyprland) · Docker · Sandboxing mit bwrap · CI/CD

---

## Naturschutz, Wissenschaft und Technik

Als persönliche Initiative arbeite ich ehrenamtlich an gemeinnützigen Projekten in den Bereichen Naturschutz, wissenschaftliche Forschung und Wissensvermittlung mit.

Ich kann Backend-Entwicklung, Prozessautomatisierung, Datenverarbeitung und -visualisierung, APIs, Webanwendungen, interaktive Karten und die Integration von Werkzeugen beisteuern.

Die Entwicklung erfolgt kostenlos, sofern das Projekt einen echten, nicht kommerziellen Zweck und einen tragbaren Umfang hat. Jeder Vorschlag wird nach technischem Bedarf, Nutzen und meiner Verfügbarkeit bewertet.

Wenn Sie Teil eines Vereins, einer Forschungsgruppe oder einer Naturschutzinitiative sind und technische Unterstützung benötigen, erreichen Sie mich per E-Mail (siehe Kontakt unten) oder über Instagram (Konto für Biologieprojekte): @zurtopia_

---

## Kontakt

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mahes-sunsun-es250206)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mrm.sunsun@gmail.com)

*Offen für Möglichkeiten in KI-Integration, Prozessautomatisierung und Backend-Entwicklung.*
