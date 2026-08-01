<p align="center">
  <img src="assets/iris.gif" width="170" alt="IRIS" />
</p>

<h1 align="center">Mahes Omprakash</h1>

<p align="center">
  <strong>Desarrollador de integración de IA y automatización</strong><br/>
  <a href="https://suntsun.github.io">suntsun.github.io</a>
</p>

---

Experiencia en desarrollo de agentes de IA integrados en sistemas en explotación: ERP, APIs de terceros, generación de ficheros oficiales y automatización de publicación en redes.

Los agentes ejecutan acciones sobre la base de datos —crean registros, avanzan procesos, generan documentación— con permisos acotados, confirmación humana implementada en el ORM y trazabilidad de cada operación.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## Que hago ?

Integro agentes de IA y automatizaciones en sistemas reales.
Trabajo principalmente con Python, Odoo, PostgreSQL, n8n y Linux.

---

## Proyectos destacados

### 🏰 El Castillo — automatizaciones Linux con orquestador conversacional gobernado

Sistema de 26 automatizaciones controladas mediante lenguaje natural. El LLM no puede ejecutar comandos directamente: únicamente propone {binario, argumentos} y una capa independiente valida cada petición contra una lista cerrada de comandos permitidos.

La ejecución utiliza shell=False, rechaza metacaracteres, limita el número de operaciones y registra cada intento en una auditoría JSONL.

Python — stdlib pura · systemd · unittest
440 tests en el orquestador · 1.179 tests en el ecosistema

Problema principal: permitir que un modelo de lenguaje interactúe con un sistema Linux real sin abrir una vía de escalada de privilegios. La seguridad se aplica a nivel de proceso y permisos, no mediante instrucciones en el prompt.

[Ver repositorio](https://github.com/Suntsun/el-castillo)

---

### 🤖 Agentes de IA sobre ERP — caso de estudio

Arquitectura de una flota de agentes conversacionales integrados en Odoo que ejecutan operaciones reales sobre el ERP. Comparten un patrón común: modelos de datos propios, capacidades de dominio, usuario de servicio con permisos explícitos y trazabilidad documental.

Resultados medidos:

Métrica	Valor
Extracción de CVs sobre golden set adversarial	14 casos, 0 alucinaciones
Escrituras verificadas directamente en el ERP	930, sin discrepancias
Latencia tras el rediseño del flujo	90–200 s → 8,3 s de media
Tests por proyecto	625 · 511 · 300 · 94

Decisiones de diseño relevantes:

Confirmación humana en el ORM. La primera versión controlaba los envíos mediante instrucciones al modelo. Tras una auditoría interna, el control se trasladó a guardas en create() y write(), donde el agente no puede eludirlo.
Inversión del flujo de escritura. El modelo dejó de modificar directamente el ERP y pasó a devolver un veredicto JSON. El código valida ese resultado y realiza la persistencia de forma síncrona, eliminando fallos intermitentes y reduciendo la latencia en un orden de magnitud.

El código pertenece al cliente. Se documentan la arquitectura, las decisiones técnicas y los resultados, pero no el código fuente.

---

### 🎬 IRIS — pipeline de contenido automatizado

Pipeline de publicación que transforma una petición en lenguaje natural en una publicación real para Instagram: generación de guion, vídeo con avatar y voz sintética, subtitulado, incorporación de b-roll, aprobación humana y publicación final.

Odoo actúa como núcleo del sistema, n8n como capa de integración con más de 95 nodos y un runner propio en VPS ejecuta la postproducción dentro de un entorno aislado mediante bwrap.

Verificado de punta a punta con publicaciones reales en Instagram.

Decisiones técnicas relevantes:

Validación en el entorno real. El sandbox se comprobó directamente en el servidor de producción, donde aparecieron dos fallos que no se reproducían en local y podían dejar el pipeline bloqueado sin una señal clara.
Control de contenido generado. El sistema incorpora siete puertas de validación para impedir la publicación de cifras no verificadas, incluida una comprobación mediante OCR sobre el render final.

[Ver repositorio](https://github.com/Suntsun/iris-pipeline-contenido)

---

### ⚙️ Sistema Captain — orquestación multiagente

Capa de mando que coordina más de 15 agentes especializados con responsabilidad única: uno construye, otro prueba como usuario real, otro audita de forma adversarial, otro revisa el diff. Gobernado por una constitución escrita y una memoria persistente en Markdown con un único agente autorizado a escribir en ella.

**Por qué importa:** el patrón de auditoría cruzada detectó repetidamente defectos que una sola pasada de desarrollo no habría capturado — gates de seguridad implementados solo en el prompt, éxitos falsos reportados al usuario, timeouts mal calibrados.



---

## Método de trabajo

- **Verificación sobre la base de datos**, no sobre el informe del propio sistema: las cifras que publico están contadas, no estimadas.
- **Pruebas como parte del entregable**, no como fase posterior. Cada proyecto incluye su suite.
- **Validación en el entorno de destino.** Los fallos que importan suelen aparecer en el servidor, no en local.
- **Seguridad aplicada a sistemas con IA**: permisos denegados por defecto, confirmación humana en código, trazabilidad completa y revisión adversarial previa al despliegue.

---

## Stack

**Lenguajes** · Python · Java · SQL · Bash
**Plataformas** · Odoo (modelos, ORM, QWeb, OWL) · PostgreSQL · n8n · systemd
**Integración** · XML-RPC · REST · SOAP · Webhooks · Meta Graph API · ficheros oficiales de ancho fijo
**IA aplicada** · agentes sobre LLM · function calling y flujos JSON validados · RAG y extracción documental · control de alucinación con golden sets
**Sistemas** · Linux (Arch/Hyprland) · Docker · sandboxing con bwrap · CI/CD

---

## Conservación, ciencia y tecnología.

Como iniciativa personal, colaboro de forma voluntaria en proyectos sin ánimo de lucro relacionados con la conservación de la naturaleza, la investigación científica y la divulgación.

Puedo aportar desarrollo backend, automatización de procesos, tratamiento y visualización de datos, APIs, aplicaciones web, mapas interactivos e integración de herramientas.

El desarrollo se realiza sin coste, siempre que el proyecto tenga una finalidad real, no comercial y un alcance asumible. Cada propuesta se valorará según sus necesidades técnicas, utilidad y mi disponibilidad.

Si formas parte de una asociación, grupo científico o iniciativa de conservación y necesitas apoyo tecnológico, puedes contactar conmigo a través de mi correo (abajo en contacto) o instagram (cuenta dedicada a proyectos de biologia): @zurtopia_

---

## Contacto

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mahes-sunsun-es250206)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mrm.sunsun@gmail.com)

*Abierto a oportunidades en integración de IA, automatización de procesos y desarrollo backend.*
