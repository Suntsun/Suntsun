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

Experience building AI agents integrated into systems already running in production: ERPs, third-party APIs, generation of official regulatory files, and automated publishing to social networks.

The agents perform real actions against the database — creating records, advancing processes, generating documentation — with scoped permissions, human confirmation enforced at the ORM layer, and full traceability of every operation.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## What I do

I integrate AI agents and automation into real, running systems.
I work primarily with Python, Odoo, PostgreSQL, n8n and Linux.

---

## Featured projects

### 🏰 El Castillo — Linux automation with a governed conversational orchestrator

A system of 26 automations driven by natural language. The LLM cannot execute commands directly: it only proposes {binary, arguments}, and an independent layer validates every request against a closed allowlist of permitted commands.

Execution uses shell=False, rejects shell metacharacters, caps the number of operations, and records every attempt in a JSONL audit log.

Python — pure stdlib · systemd · unittest
440 tests in the orchestrator · 1,179 tests across the ecosystem

Core problem: letting a language model interact with a real Linux system without opening a privilege-escalation path. Security is enforced at the process and permission level, not through prompt instructions.

[View repository](https://github.com/Suntsun/el-castillo)

---

### 🤖 AI agents on top of an ERP — case study

Architecture of a fleet of conversational agents embedded in Odoo that carry out real operations against the ERP. They share a common pattern: dedicated data models, domain capabilities, a service user with explicit permissions, and document-level traceability.

Measured results:

| Metric | Value |
| --- | --- |
| CV extraction against an adversarial golden set | 14 cases, 0 hallucinations |
| Writes verified directly in the ERP | 930, no discrepancies |
| Latency after redesigning the flow | 90–200 s → 8.3 s on average |
| Tests per project | 625 · 511 · 300 · 94 |

Key design decisions:

- **Human confirmation at the ORM layer.** The first version governed outbound actions through instructions to the model. After an internal audit, the control was moved into guards in `create()` and `write()`, where the agent cannot bypass it.
- **Inverting the write flow.** The model stopped modifying the ERP directly and instead returns a JSON verdict. Application code validates that result and performs the write synchronously, eliminating intermittent failures and cutting latency by an order of magnitude.

The source code belongs to the client. The architecture, technical decisions and results are documented; the source code is not.

---

### 🎬 IRIS — automated content pipeline

A publishing pipeline that turns a natural-language request into a real Instagram post: script generation, video with a synthetic avatar and voice, subtitling, b-roll insertion, human approval, and final publication.

Odoo acts as the system core, n8n as the integration layer with more than 95 nodes, and a custom VPS runner performs post-production inside an isolated environment using bwrap.

Verified end to end with real published posts on Instagram.

Key technical decisions:

- **Validation in the real environment.** The sandbox was tested directly on the production server, where two failures surfaced that did not reproduce locally and could leave the pipeline stalled with no clear signal.
- **Control over generated content.** The system includes seven validation gates to prevent publishing unverified figures, including an OCR check on the final render.

[View repository](https://github.com/Suntsun/iris-pipeline-contenido)

---

### ⚙️ Captain system — multi-agent orchestration

A command layer coordinating more than 15 specialised single-responsibility agents: one builds, another tests as a real user, another audits adversarially, another reviews the diff. Governed by a written constitution and a persistent Markdown memory that only one agent is authorised to write to.

**Why it matters:** the cross-audit pattern repeatedly caught defects a single development pass would have missed — security gates implemented only in the prompt, false successes reported back to the user, badly calibrated timeouts.

---

## How I work

- **Verification against the database**, not against the system's own report: the figures I publish are counted, not estimated.
- **Tests as part of the deliverable**, not a later phase. Every project ships with its suite.
- **Validation in the target environment.** The failures that matter tend to appear on the server, not locally.
- **Security applied to AI-driven systems**: deny-by-default permissions, human confirmation enforced in code, full traceability, and adversarial review before deployment.

---

## Stack

**Languages** · Python · Java · SQL · Bash
**Platforms** · Odoo (models, ORM, QWeb, OWL) · PostgreSQL · n8n · systemd
**Integration** · XML-RPC · REST · SOAP · Webhooks · Meta Graph API · fixed-width regulatory files
**Applied AI** · LLM-based agents · function calling and validated JSON flows · RAG and document extraction · hallucination control with golden sets
**Systems** · Linux (Arch/Hyprland) · Docker · sandboxing with bwrap · CI/CD

---

## Conservation, science and technology

As a personal initiative, I volunteer on non-profit projects related to nature conservation, scientific research and outreach.

I can contribute backend development, process automation, data processing and visualisation, APIs, web applications, interactive maps and tool integration.

This work is done free of charge, provided the project has a genuine, non-commercial purpose and a manageable scope. Each proposal is assessed on its technical needs, usefulness and my availability.

If you are part of an association, research group or conservation initiative and need technical support, you can reach me by email (see contact below) or on Instagram (account dedicated to biology projects): @zurtopia_

---

## Contact

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mahes-sunsun-es250206)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mrm.sunsun@gmail.com)

*Open to opportunities in AI integration, process automation and backend development.*
