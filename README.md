<p align="center">
  <img src="assets/iris.gif" width="170" alt="IRIS" />
</p>

<h1 align="center">Mahes Omprakash</h1>

<p align="center">
  <strong>Desarrollador de integración de IA y automatización</strong><br/>
  <a href="https://suntsun.github.io">suntsun.github.io</a>
</p>

<p align="center">
  <strong>Español</strong> ·
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.en.md">English</a> ·
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.it.md">Italiano</a> ·
  <a href="https://github.com/Suntsun/Suntsun/blob/main/README.de.md">Deutsch</a>
</p>

---

Experiencia en soluciones de Inteligencia Artificial aplicadas a empresas en funcionamiento: sistemas **Agentic AI**, integración y orquestación de **LLMs**, arquitecturas **RAG**, automatización de procesos, desarrollo de **APIs**, personalización de **ERPs** y automatización para **redes sociales**.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![Odoo](https://img.shields.io/badge/Odoo-714B67?style=flat-square&logo=odoo&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![SQL](https://img.shields.io/badge/SQL-003B57?style=flat-square&logo=databricks&logoColor=white) ![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white) ![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?style=flat-square&logo=claude&logoColor=white) ![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square&logo=groq&logoColor=white) ![Llama](https://img.shields.io/badge/Llama-0866FF?style=flat-square&logo=meta&logoColor=white) ![Qwen](https://img.shields.io/badge/Qwen-615CED?style=flat-square&logo=alibabacloud&logoColor=white) ![Mistral](https://img.shields.io/badge/Mistral-FA520F?style=flat-square&logo=mistralai&logoColor=white) ![Obsidian](https://img.shields.io/badge/Obsidian-7C3AED?style=flat-square&logo=obsidian&logoColor=white)

---
## Proyectos destacados

### 🏰 El Castillo — asistente de sistema con permisos blindados

Un asistente con el que hablo en lenguaje natural para manejar 26 automatizaciones de mi propio equipo Linux.

Lo interesante es lo que **no** puede hacer. El modelo nunca ejecuta nada por su cuenta: solo propone qué le gustaría lanzar, y una capa independiente —escrita a mano, sin IA— comprueba esa propuesta contra una lista cerrada de operaciones permitidas. Lo que no está en la lista, se rechaza. Cada intento, aceptado o denegado, queda registrado.

El problema de fondo es dejar que un modelo toque un sistema operativo real sin regalarle el control de la máquina. La solución fue separar por niveles lo que cada parte puede hacer, reservar las operaciones delicadas a un circuito aparte y marcar automáticamente todo lo que pasa por ahí. La seguridad vive en los permisos del sistema, no en una instrucción dentro del prompt: a un prompt se le puede convencer; a un permiso denegado, no.

El patrón no depende de Linux: aquí está aplicado a mi equipo, pero sirve para cualquier sistema. Permite poner límites y contenedores de acción a modelos más extensos o complejos, como Claude o Codex.

Python con librería estándar · 440 tests en el orquestador · 1.179 en el ecosistema completo

[Ver repositorio](https://github.com/Suntsun/el-castillo)

---

### 🤖 Flota de agentes de IA sobre ERP — caso de estudio

Siete agentes conversacionales que viven dentro de Odoo:

- **Sara — Recursos Humanos.** Recoge candidaturas por correo, WhatsApp y formulario web, extrae los datos del CV, criba según los requisitos de la vacante y agenda las entrevistas.
- **Emilio — Gestión laboral.** Altas y bajas en la Seguridad Social, generación de los ficheros oficiales de afiliación y comunicación de contratos al SEPE.
- **Lara — Inteligencia empresarial.** Vigila boletines oficiales y prensa —BOE, BORME, contratación pública, subvenciones— y avisa de lo que afecta al negocio. Se configura según el sector de la empresa.
- **Smith — Licitaciones.** Rastrea la contratación pública, descarta lo que no encaja con criterios objetivos y prepara la documentación de la propuesta.
- **Lia — Logística.** Stock, rutas de entrega, transportistas, indicadores de servicio del almacén y monitorización en tiempo real sobre un mapa con la flota desplegada.
- **Samy — Comercial.** Pipeline de CRM, priorización de oportunidades, aviso de las que se enfrían y seguimiento de cobros.
- **Marina — Mantenimiento técnico.** Instalaciones de tratamiento de aguas: partes de trabajo en campo y servicio de asistencia técnica.

Dos decisiones que cambiaron el proyecto:

- **La confirmación humana vive en el código, no en el prompt.** Al principio le pedía al modelo que no enviara nada sin permiso. Una auditoría interna dejó claro que eso no basta: ahora la comprobación está en el punto donde el ERP guarda los datos, y el agente no puede saltársela por mucho que se le insista.
- **El agente propone, el código decide.** Dejé de permitir que el modelo escribiera directamente en el ERP. Ahora devuelve su conclusión, el código la valida y es el código el que guarda. Desaparecieron los fallos intermitentes y el proceso pasó de minutos a segundos.

El código pertenece al cliente. Documento la arquitectura, las decisiones técnicas y los resultados, pero no el código fuente.

---

### 🎬 IRIS — Agente de creación de contenido desde el chat

Un agente integrado en Odoo con el que se habla por chat. Le pides una publicación y se encarga del resto: escribe el guion, genera el vídeo con avatar y voz sintética, lo subtitula, le añade el b-roll, te lo pasa para que des el visto bueno y lo publica en Instagram.

Odoo es el núcleo, n8n la capa de integración con más de 95 nodos, y un servidor propio hace la postproducción en un entorno aislado.

Verificado de principio a fin con publicaciones reales.

**Control de lo que se publica.** Siete comprobaciones impiden que salga una cifra sin verificar, incluida una lectura por OCR del vídeo ya montado.

[Ver repositorio](https://github.com/Suntsun/iris-pipeline-contenido)

---

### ⚙️ Sistema Captain — orquestación multiagente

Una capa de mando que coordina más de 15 agentes especializados, cada uno con una sola responsabilidad: uno construye, otro prueba como usuario real, otro audita buscando fallos, otro revisa el código.
Se gobierna con una constitución escrita (hard rules) y una memoria persistente (contextual RAG) en la que solo un agente tiene permiso de escritura.

**Por qué importa:** la auditoría cruzada detectó una y otra vez defectos que una sola pasada de desarrollo habría dejado pasar — controles de seguridad que solo existían en el prompt, éxitos falsos reportados al usuario, tiempos de espera mal calibrados.

Esto no es solo un sistema de orquestación: es el soporte de mi metodología de trabajo.

En la práctica, cada agente trabaja solo con el contexto de su tarea en lugar de arrastrar la conversación entera, y ningún trabajo se da por bueno sin pasar por una unidad que no lo escribió. Eso contiene el gasto y evita encadenar correcciones sobre un error que nadie revisó a tiempo.

Es el mismo argumento que defiende el equipo de Applied AI de Anthropic: [en un sistema en producción, el límite ya no lo pone el modelo, sino la estructura que lo rodea](https://www.youtube.com/watch?v=K0X9QDRkIdg).

---

## Método de trabajo

Trabajo con metodología modular y la escalabilidad como regla: cada pieza debe poder crecer o sustituirse sin arrastrar al resto.

Antes de cerrar un proyecto realizo auditorías de funcionamiento y pruebas de seguridad, y las entrego como parte final del trabajo.

Mantengo el registro de cada proyecto en mis propias bases de datos, con un sistema RAG propio que consulto mientras desarrollo. Al repositorio sube el resultado; el conocimiento del proyecto se queda ordenado y disponible para el siguiente.

---

## Stack

**Lenguajes** · Python · Java · SQL · Bash
**Plataformas** · Odoo (modelos, ORM, QWeb, OWL) · PostgreSQL · n8n · systemd
**Integración** · XML-RPC · REST · SOAP · Webhooks · Meta Graph API · ficheros oficiales de ancho fijo
**IA aplicada** · Claude Code · agentes sobre LLM (Llama, Qwen, Mistral, vía Groq y modelos locales) · function calling y flujos JSON validados · RAG y extracción documental · control de alucinación con golden sets
**Herramientas** · Obsidian como base de conocimiento · Linux (Arch/Hyprland) · Docker · sandboxing con bwrap · CI/CD

---

## Conservación, ciencia y tecnología

Como iniciativa personal, colaboro de forma voluntaria en proyectos sin ánimo de lucro relacionados con la conservación de la naturaleza, la investigación científica y la divulgación.

Puedo aportar desarrollo backend, automatización de procesos, tratamiento y visualización de datos, APIs, aplicaciones web, mapas interactivos e integración de herramientas.

El desarrollo se realiza sin coste, siempre que el proyecto tenga una finalidad real, no comercial y un alcance asumible. Cada propuesta se valorará según sus necesidades técnicas, utilidad y mi disponibilidad.

Si formas parte de una asociación, grupo científico o iniciativa de conservación y necesitas apoyo tecnológico, puedes escribirme al correo de contacto.

---

## Contacto

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mahes-sunsun-es250206) [![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mrm.sunsun@gmail.com)

*Abierto a oportunidades en integración de IA, automatización de procesos y desarrollo backend.*
