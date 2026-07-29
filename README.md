# Mahes Omprakash

### Desarrollador de integración de IA y automatización

Construyo sistemas donde un modelo de lenguaje **hace trabajo real** contra sistemas de producción — ERPs, APIs, ficheros oficiales, redes sociales — con las barreras de seguridad puestas en el código, no en el prompt.

No hago demos de chatbot. Hago agentes que leen, deciden, escriben en la base de datos y dejan traza de lo que hicieron.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## En qué trabajo

**Agentes de IA integrados en ERP.** Once agentes verticales sobre Odoo 17, cada uno con su dominio: conciliación bancaria, pedidos B2B por WhatsApp, selección de personal, licitaciones públicas, trámites laborales, logística, gestión documental, inteligencia de mercado y control de calidad de partes de mantenimiento. No son interfaces de consulta: ejecutan acciones reales sobre el ERP —crear registros, avanzar etapas, generar y enviar documentos— bajo usuario de servicio con permisos acotados.

El bucle de razonamiento y ejecución de herramientas está **implementado a mano sobre la API HTTP del modelo**, sin frameworks de agentes: definición del esquema de tools, despacho de las llamadas contra métodos del ORM, y control del ciclo. Sé lo que pasa en cada vuelta del bucle porque lo escribí.

**Automatización de procesos de punta a punta.** Ingesta de fuentes oficiales (sindicación ATOM/CODICE de la Plataforma de Contratación del Estado), generación de ficheros oficiales de ancho fijo byte-exactos para la Seguridad Social, integración SOAP con el SEPE, y publicación automatizada en redes sociales vía Meta Graph API orquestada con n8n.

**Infraestructura propia de trabajo.** Un sistema multiagente jerárquico con constitución escrita y memoria persistente, y una suite de 26 automatizaciones Linux gobernada por un orquestador conversacional con modelo de permisos default-deny.

---

## Proyectos destacados

### 🏰 El Castillo — automatizaciones Linux con orquestador conversacional gobernado

26 automatizaciones bajo un REPL en lenguaje natural cuyo cerebro es un LLM **sin capacidad de ejecución directa**. El modelo solo propone `{binario, argumentos}`; una capa propia valida contra una allowlist cerrada de binarios de solo lectura, ejecuta con `shell=False`, rechaza metacaracteres, limita el lote y deja auditoría JSONL de cada intento.

`Python (stdlib pura, cero dependencias)` · `systemd` · `unittest` · **~1.000 tests**

**El problema interesante:** dar a un modelo de lenguaje acceso a un shell real sin abrir un vector de escalada de privilegios. Se resolvió con permisos a nivel de proceso, no de instrucción — porque a un LLM no se le pide que se porte bien, se le limita lo que puede tocar.

<!-- TODO: enlace al repo cuando se cree -->

---

### 🤖 Agentes de IA sobre ERP — caso de estudio

Arquitectura de una flota de agentes conversacionales embebidos en Odoo que operan el ERP de verdad. Patrón común: modelos de datos propios, skills de dominio, usuario de servicio con permisos explícitos y cierre documental trazable.

**Resultados medidos:**

| Métrica | Valor |
|---|---|
| Agentes verticales construidos | **11**, sobre Odoo 17 |
| Volumen de trabajo | **179 commits · ~77.500 líneas** (45.000 Python) |
| Extracción de CVs sobre golden set adversarial | **14 casos, 0 alucinaciones** |
| Escrituras reales verificadas en ERP | **930, sin discrepancias** |
| Latencia tras rediseño de flujo | **90–200 s → 8,3 s de media** |
| Suites de test por proyecto | 625 · 511 · 300 · 94 |

**Dos decisiones de diseño que defiendo en cualquier entrevista:**

- **El gate humano va en el ORM, no en el prompt.** Una auditoría interna rechazó mi primera versión del control de envío porque estaba implementada como instrucción al modelo. Se reimplementó como guarda real en `create()`/`write()`. Un LLM puede ignorar una instrucción; no puede ignorar una excepción.
- **Flujo invertido.** Quité al LLM la escritura directa sobre el ERP: ahora devuelve un veredicto JSON que el código valida y persiste de forma síncrona. Eliminó los fallos intermitentes y bajó la latencia un orden de magnitud.

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

## Cómo trabajo

- **Evidencia antes que narración.** Si un sistema dice que escribió 930 registros, los cuento en la base de datos. He corregido más de una vez cifras propias que resultaron ser errores de agregación.
- **Tests como parte del entregable**, no como fase posterior. Cada proyecto de arriba tiene su suite.
- **Verificación en el entorno real.** Lo que funciona en local no está verificado; los fallos que importan aparecen en el servidor de destino.
- **Seguridad por diseño en sistemas con IA**: permisos default-deny, human-in-the-loop implementado en código, trazabilidad completa y revisión adversarial antes de desplegar.

---

## Stack

**Lenguajes** · Python · Java · SQL · Bash
**Plataformas** · Odoo (modelos, ORM, QWeb, OWL) · PostgreSQL · n8n · systemd
**Integración** · XML-RPC · REST · SOAP · Webhooks · Meta Graph API · ficheros oficiales de ancho fijo
**IA aplicada** · agentes sobre LLM · function calling y flujos JSON validados · RAG y extracción documental · control de alucinación con golden sets
**Sistemas** · Linux (Arch/Hyprland) · Docker · sandboxing con bwrap · CI/CD

---

## Contacto

📧 **mrm.sunsun@gmail.com**

<!-- TODO: añadir LinkedIn cuando el mando facilite la URL -->

*Abierto a oportunidades en integración de IA, automatización de procesos y desarrollo backend.*
