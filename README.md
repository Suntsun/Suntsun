# Mahes Omprakash

### Desarrollador de integración de IA y automatización

Experiencia en desarrollo de agentes de IA integrados en sistemas en explotación: ERP, APIs de terceros, generación de ficheros oficiales y automatización de publicación en redes.

Los agentes ejecutan acciones sobre la base de datos —crean registros, avanzan procesos, generan documentación— con permisos acotados, confirmación humana implementada en el ORM y trazabilidad de cada operación.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## En qué trabajo

**Agentes de IA integrados en ERP.** Agentes verticales sobre Odoo 17, cada uno con su dominio: selección de personal, licitaciones públicas, trámites laborales ante la Seguridad Social y el SEPE, logística, inteligencia de mercado y control de calidad de partes de mantenimiento. No son interfaces de consulta: ejecutan acciones reales sobre el ERP —crear registros, avanzar etapas, generar y enviar documentos— bajo usuario de servicio con permisos acotados.

**Automatización de procesos de punta a punta.** Ingesta de fuentes oficiales (sindicación ATOM/CODICE de la Plataforma de Contratación del Estado), generación de ficheros oficiales de ancho fijo byte-exactos para la Seguridad Social, integración SOAP con el SEPE, y publicación automatizada en redes sociales vía Meta Graph API orquestada con n8n.

**Infraestructura propia de trabajo.** Un sistema multiagente jerárquico con constitución escrita y memoria persistente, y una suite de 26 automatizaciones Linux gobernada por un orquestador conversacional con modelo de permisos default-deny.

---

## Proyectos destacados

### 🏰 El Castillo — automatizaciones Linux con orquestador conversacional gobernado

26 automatizaciones bajo un REPL en lenguaje natural cuyo cerebro es un LLM **sin capacidad de ejecución directa**. El modelo solo propone `{binario, argumentos}`; una capa propia valida contra una allowlist cerrada de binarios de solo lectura, ejecuta con `shell=False`, rechaza metacaracteres, limita el lote y deja auditoría JSONL de cada intento.

`Python (stdlib pura, cero dependencias)` · `systemd` · `unittest` · **349 tests verificados en ejecución**

**El problema interesante:** dar a un modelo de lenguaje acceso a un shell real sin abrir un vector de escalada de privilegios. Se resolvió con permisos a nivel de proceso, no de instrucción — porque a un LLM no se le pide que se porte bien, se le limita lo que puede tocar.

<!-- TODO: enlace al repo cuando se cree -->

---

### 🤖 Agentes de IA sobre ERP — caso de estudio

Arquitectura de una flota de agentes conversacionales embebidos en Odoo que operan el ERP de verdad. Patrón común: modelos de datos propios, skills de dominio, usuario de servicio con permisos explícitos y cierre documental trazable.

**Resultados medidos:**

| Métrica | Valor |
|---|---|
| Extracción de CVs sobre golden set adversarial | **14 casos, 0 alucinaciones** |
| Escrituras reales verificadas en ERP | **930, sin discrepancias** |
| Latencia tras rediseño de flujo | **90–200 s → 8,3 s de media** |
| Suites de test por proyecto | 625 · 511 · 300 · 94 |

**Dos decisiones de diseño relevantes:**

- **Confirmación humana implementada en el ORM.** Una auditoría interna rechazó la primera versión del control de envío por estar implementada como instrucción al modelo. Se reimplementó como guarda en `create()`/`write()`, donde el agente no puede saltársela.
- **Inversión del flujo de escritura.** El modelo dejó de escribir directamente en el ERP y pasó a devolver un veredicto JSON que el código valida y persiste de forma síncrona. Resolvió los fallos intermitentes y redujo la latencia en un orden de magnitud.

*Código propiedad del cliente — se documenta la arquitectura, no el fuente.*

<!-- TODO: enlace al repo cuando se cree -->

---

### 🎬 IRIS — pipeline de contenido automatizado

De una petición en lenguaje natural a una publicación real en Instagram: guion, vídeo con avatar y voz sintética, subtitulado, b-roll, aprobación humana y publicación. Odoo como hub, n8n como capa de integración (95+ nodos), y un runner de post-producción propio en VPS con ejecución en sandbox.

**Verificado de punta a punta con publicaciones reales en Instagram.**

Lo que más me enseñó: el sandbox de ejecución (`bwrap`) se comprobó **en el servidor real, no en local** — y ahí aparecieron dos fallos que en local no se veían y habrían dejado el sistema inoperante en silencio. Y un sistema de 7 puertas de validación para que un vídeo generado automáticamente no pueda mostrar jamás una cifra inventada, incluyendo comprobación por OCR del render final.

<!-- TODO: enlace al repo cuando se cree -->

---

### ⚙️ Sistema Captain — orquestación multiagente

Capa de mando que coordina más de 15 agentes especializados con responsabilidad única: uno construye, otro prueba como usuario real, otro audita de forma adversarial, otro revisa el diff. Gobernado por una constitución escrita y una memoria persistente en Markdown con un único agente autorizado a escribir en ella.

**Por qué importa:** el patrón de auditoría cruzada detectó repetidamente defectos que una sola pasada de desarrollo no habría capturado — gates de seguridad implementados solo en el prompt, éxitos falsos reportados al usuario, timeouts mal calibrados.

<!-- TODO: enlace al repo cuando se cree -->

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

## Contacto

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mahes-sunsun-es250206)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mrm.sunsun@gmail.com)

*Abierto a oportunidades en integración de IA, automatización de procesos y desarrollo backend.*
