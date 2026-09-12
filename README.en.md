<p align="center">
  <img src="assets/iris.gif" width="170" alt="IRIS" />
</p>

<h1 align="center">Mahes Omprakash</h1>

<p align="center">
  <strong>AI Integration & Automation Developer</strong><br/>
  <a href="https://suntsun.github.io">suntsun.github.io</a>
</p>

<p align="center">
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.md">Español</a> ·
  <strong>English</strong> ·
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.it.md">Italiano</a> ·
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.de.md">Deutsch</a>
</p>

---

Experience in Artificial Intelligence solutions applied to companies already up and running: **Agentic AI** systems, **LLM** integration and orchestration, **RAG** architectures, process automation, **API** development, **ERP** customisation and **social media** automation.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![SQL](https://img.shields.io/badge/SQL-003B57?style=flat-square&logo=databricks&logoColor=white) ![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white) ![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?style=flat-square&logo=claude&logoColor=white) ![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square&logo=groq&logoColor=white) ![Llama](https://img.shields.io/badge/Llama-0866FF?style=flat-square&logo=meta&logoColor=white) ![Qwen](https://img.shields.io/badge/Qwen-615CED?style=flat-square&logo=alibabacloud&logoColor=white) ![Mistral](https://img.shields.io/badge/Mistral-FA520F?style=flat-square&logo=mistralai&logoColor=white) ![Obsidian](https://img.shields.io/badge/Obsidian-7C3AED?style=flat-square&logo=obsidian&logoColor=white)

---
## Featured projects

### 🏰 El Castillo — a system assistant with locked-down permissions

An assistant I talk to in plain language to drive 26 automations on my own Linux machine.

The interesting part is what it **cannot** do. The model never executes anything on its own: it only proposes what it would like to run, and a separate layer — hand-written, no AI involved — checks that proposal against a closed list of permitted operations. Anything not on the list is rejected. Every attempt, allowed or denied, is logged.

The underlying problem is letting a model touch a real operating system without handing it control of the machine. The answer was to separate, by level, what each part is allowed to do, route the sensitive operations through a circuit of their own, and automatically flag everything that passes through it. Security lives in the system's permissions, not in an instruction inside the prompt: a prompt can be talked round; a denied permission cannot.

The pattern is not tied to Linux: here it runs on my own machine, but it works for any system. It lets you put limits and action boundaries around larger or more capable models such as Claude or Codex.

Python, standard library only · 440 tests in the orchestrator · 1,179 across the whole ecosystem

[View repository](https://github.com/Suntsun/el-castillo)

---

### 🤖 A fleet of AI agents on top of an ERP — case study

Seven conversational agents living inside Odoo:

- **Sara — Human Resources.** Collects applications by email, WhatsApp and web form, extracts the CV data, screens candidates against the role's requirements and books the interviews.
- **Emilio — Employment administration.** Social-security registrations and deregistrations, generation of the official affiliation files, and filing of employment contracts with the public employment service.
- **Lara — Business intelligence.** Watches official gazettes and the press — company registry, public procurement, grants — and flags what affects the business. Configurable for each company's sector.
- **Smith — Public tenders.** Tracks public procurement, discards what does not fit against objective criteria, and prepares the bid documentation.
- **Lia — Logistics.** Stock, delivery routes, carriers, warehouse service indicators, and real-time monitoring on a map of the deployed fleet.
- **Samy — Sales.** CRM pipeline, opportunity prioritisation, alerts on deals going cold, and payment follow-up.
- **Marina — Technical maintenance.** Water treatment installations: field work orders and technical support service.

Two decisions that changed the project:

- **Human confirmation lives in the code, not in the prompt.** At first I simply asked the model not to send anything without permission. An internal audit made it clear that this is not enough: the check now sits at the point where the ERP writes its data, and the agent cannot get around it no matter how hard it is pushed.
- **The agent proposes, the code decides.** I stopped letting the model write to the ERP directly. It now returns its conclusion, the code validates it, and the code is what saves. The intermittent failures disappeared and the process went from minutes to seconds.

The source code belongs to the client. I document the architecture, the technical decisions and the results, but not the code itself.

---

### 🎬 IRIS — a content creation agent you talk to in chat

An agent embedded in Odoo that you speak to through a chat. You ask it for a post and it handles the rest: it writes the script, generates the video with a synthetic avatar and voice, subtitles it, adds the b-roll, hands it back for your approval, and publishes it on Instagram.

Odoo is the core, n8n the integration layer with more than 95 nodes, and a dedicated server handles post-production in an isolated environment.

Verified end to end with real published posts.

**Control over what goes out.** Seven checks prevent an unverified figure from being published, including an OCR reading of the finished video.

[View repository](https://github.com/Suntsun/iris-pipeline-contenido)

---

### ⚙️ Captain system — multi-agent orchestration

A command layer coordinating more than 15 specialised agents, each with a single responsibility: one builds, one tests as a real user, one audits hunting for faults, one reviews the code.
It is governed by a written constitution (hard rules) and a persistent memory (contextual RAG) that only one agent may write to.

**Why it matters:** cross-auditing caught, time and again, defects a single development pass would have let through — security controls that only existed in the prompt, false successes reported back to the user, badly calibrated timeouts.

This is not just an orchestration system: it is the backbone of how I work.

In practice, each agent works only with the context of its own task instead of dragging the whole conversation along, and no piece of work is accepted without passing through a unit that did not write it. That keeps the cost down and avoids stacking fixes on top of a mistake nobody caught in time.

It is the same argument made by Anthropic's Applied AI team: [in a production system, the limiting factor is no longer the model but the structure wrapped around it](https://www.youtube.com/watch?v=K0X9QDRkIdg).

---

## How I work

I work in a modular way, with scalability as a rule: every piece must be able to grow or be replaced without dragging the rest with it.

Before closing a project I run functional audits and security tests, and I deliver them as the final part of the work.

I keep the record of every project in my own databases, with a RAG system of my own that I query while developing. What goes up to the repository is the result; the project's knowledge stays organised and ready for the next one.

---

## Stack

**Languages** · Python · Java · SQL · Bash

**Platforms** · Odoo (models, ORM, QWeb, OWL) · PostgreSQL · n8n · systemd

**Integration** · XML-RPC · REST · SOAP · Webhooks · Meta Graph API · fixed-width regulatory files

**Applied AI** · Claude Code · LLM-based agents (Llama, Qwen, Mistral, via Groq and local models) · function calling and validated JSON flows · RAG and document extraction · hallucination control with golden sets

**Tools** · Obsidian as a knowledge base · Linux (Arch/Hyprland) · Docker · sandboxing with bwrap · CI/CD

---

## Conservation, science and technology

As a personal initiative, I volunteer on non-profit projects related to nature conservation, scientific research and outreach.

I can contribute backend development, process automation, data processing and visualisation, APIs, web applications, interactive maps and tool integration.

This work is done free of charge, provided the project has a genuine, non-commercial purpose and a manageable scope. Each proposal is assessed on its technical needs, usefulness and my availability.

If you are part of an association, research group or conservation initiative and need technical support, you can write to me at the contact address below.

---

## Contact

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mahes-sunsun-es250206) [![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mrm.sunsun@gmail.com)

*Open to opportunities in AI integration, process automation and backend development.*
