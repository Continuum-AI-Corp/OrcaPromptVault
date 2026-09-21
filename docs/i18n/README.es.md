# Orca PromptVault

<sub>[English](../../README.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · **Español** · [العربية](README.ar.md)</sub>

### El archivo abierto de cómo funcionan realmente los agentes de IA.

Un archivo versionado y verificable de los prompts de sistema, instrucciones para desarrolladores,
esquemas de herramientas y arneses de agente que mueven los productos de IA de hoy. Capturado con
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay).

<a href="https://www.orcarouter.ai">
  <img src="../orcarouter.svg" alt="OrcaRouter" height="28" align="left" hspace="10">
</a>

**Creado por el equipo detrás de [OrcaRouter](https://www.orcarouter.ai)** — una clave de API y un
único endpoint para Claude, GPT, Gemini, Grok, DeepSeek, Qwen y el resto.

Además: [todas las APIs de modelos](https://www.orcarouter.ai/models) · [OrcaCode Review](https://www.orcarouter.ai/code-review) · [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) · [OrcaRouter Lite](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)

Contacto: [X](https://x.com/OrcaRouter) · [Discord](https://discord.com/invite/YEubt8enRA) · [Hugging Face](https://huggingface.co/orcarouter) · [Ollama](https://ollama.com/orcarouter)

<br clear="left">

[![Artifacts](https://img.shields.io/badge/artifacts-106-blue)](#qué-hay-dentro)
[![Captured](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../CAPTURES.md)
[![Tool schemas](https://img.shields.io/badge/tool%20schemas-15-brightgreen)](../CAPTURES.md)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](../../LICENSE)

## Por qué existe

El comportamiento de un agente no está solo en sus pesos. Está en los veintitantos mil caracteres de
instrucciones que el arnés ensambla y envía *antes* de tu primera palabra, y en las treinta y cinco
definiciones de herramientas que van con ellas. Ese texto decide qué rechaza, a qué herramienta echa
mano primero, cómo te habla y qué le han contado sobre ti.

Leerlo hace que el producto deje de ser una caja negra. Guardarlo fechado y comparable convierte un
cambio de comportamiento en una línea que se puede señalar.

## Qué hay dentro

| carpeta | contenido | archivos | de ellas capturadas |
|---|---|---|---|
| OpenAI | [ChatGPT](../../ChatGPT/) 4o · 4.1 · 4.5 · 5 · o3/o4-mini · Atlas, [Codex](../../Codex/) CLI · cloud · desktop, ChatKit Studio | 21 | 5 |
| Anthropic | [Claude](../../Claude/) Sonnet 3.5 → Opus 5 · Fable 5.1 · Design · estilos de usuario, [Claude Code](../../Claude-Code/) CLI y Agent SDK | 22 | 8 |
| Google | [Gemini](../../Gemini/) 2.5 Pro · Diffusion · asistente de Gmail | 3 | — |
| xAI | [Grok](../../Grok/) 3 · 4 · 4.1 · 4.20 · Code Fast 1 | 7 | — |
| [Cursor](../../Cursor/) | agente de Cursor · Cursor 2.0 · Composer sobre Grok 4.5 | 4 | 1 |
| Moonshot | [Kimi](../../Kimi/) K2 · K2 Thinking | 2 | — |
| Alibaba | [Qwen Code](../../Qwen/) CLI | 2 | 2 |
| ZAI | [ZCode](../../GLM/) prompt · skills · tools | 3 | — |
| [DeepSeek](../../DeepSeek/) | todavía nada — [se busca](../../CONTRIBUTING.md#wanted) | 0 | — |
| Meta | Meta AI sobre Muse Spark · Llama 4 en WhatsApp | 2 | — |
| Others | OpenCode · Devin · Windsurf · Cline · Replit · Manus · v0 · Bolt · Lovable · Perplexity · Mistral · MiniMax · MiMoCode · Hermes · Kilo Code · Dia · Brave Leo · Factory Droid · Hume · Cluely · Same.dev · MultiOn | 40 | 15 |

Treinta y uno de estos archivos salieron del cable en nuestras propias máquinas — veinte capturas,
con tamaños, versiones del arnés y el comando que reproduce cada una en
**[docs/CAPTURES.md](../CAPTURES.md)**. Los otros setenta y cinco se heredan de CL4R1T4S sin
retocar, y están indexados ruta por ruta en **[docs/UPSTREAM.md](../UPSTREAM.md)**.

## Capturado o referido

Cada archivo aquí es una de dos cosas, y la diferencia importa más que el contenido.

**Capturado** — extraído del cable por un proxy local mientras el arnés real corría sin
modificaciones: el prompt que la herramienta de esa máquina envió de verdad, limpio de todo dato
identificativo, archivado con su versión de arnés, su modo, su tamaño y el único comando que lo
vuelve a producir. No hace falta creernos: ejecuta el comando y haz el diff.

**Referido** — todo lo que un proxy local no puede ver. Un producto de chat ensambla su prompt en el
servidor: claude.ai, ChatGPT y Gemini nunca lo envían desde tu máquina, así que su texto solo se
consigue haciendo que el modelo lo repita, y llega como transcripción, no como bytes en el cable.
Esos archivos se guardan tal y como llegaron, fechados cuando la fecha se conoce, con la
incertidumbre que eso arrastra. Lo capturado es prueba; lo referido, testimonio.

## Captura uno tú mismo

```console
npm i -g orcareplay
git clone https://github.com/Continuum-AI-Corp/OrcaReplay
node capture/capture.mjs claude --model claude-opus-5
```

Levanta un proxy local, lanza el agente sin tocarlo, espera la petición que lleva el prompt, lo
extrae, sustituye tu directorio personal, tu usuario, tu identidad de git y tu pasarela por marcadores,
y escribe un archivo. Después abre un pull request aquí — ver
[CONTRIBUTING.md](../../CONTRIBUTING.md).

Codex, OpenCode, Qwen Code, Cursor, MiMoCode, Kilo y Hermes siguen el mismo camino; las
[notas de captura](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/README.md)
cubren el detalle por arnés, incluidos los cinco a los que hay que llegar con `--tls-intercept`,
porque su origen no se mueve con una variable de entorno.

## Lo que el archivo ya demuestra

Cuatro hallazgos, todos comprobables contra los archivos de este repositorio:

- **La variable es el arnés.** Un modelo, `nemotron-3.5-lightning-free`, en dos arneses:
  [9.656 caracteres y 11 herramientas desde OpenCode](../../OpenCode/opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md),
  [14.049 y 19 desde Hermes](../../Hermes/hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md).
  Mismo modelo, mismo endpoint gratuito, instrucciones y superficie de herramientas distintas.
- **El modelo también.** [OpenCode](../../OpenCode/) envía tres plantillas distintas a siete
  modelos. Cinco gratuitos abren con *You are opencode, an interactive CLI tool*; Muse Spark recibe
  otra apertura y el dialecto responses; GPT-5.6-Sol recibe una tercera plantilla y `apply_patch` en
  lugar de `edit` y `write`. El prompt y el formato de transporte se eligen por modelo.
- **Interactivo no es el mismo prompt que `-p`.** En Fable 5.1, Claude Code envía desde una terminal
  [26.131 caracteres y 35 herramientas](../../Claude-Code/claude-code-fable-5.1-system-prompt-2026-09-02.md)
  y desde un script [20.806 y 29](../../Claude-Code/claude-code-fable-5.1-print-system-prompt-2026-09-02.md),
  y hasta la línea de identidad cambia a *You are a Claude agent, built on Anthropic's Claude Agent
  SDK*. El prompt del uso diario y el que recibe tu CI son dos prompts.
- **Un nivel no es un prompt.** MiMoCode envía a `mimo-v2.5` y `mimo-v2.5-pro`
  [texto y herramientas idénticos byte a byte](../../MiMoCode/mimocode-mimo-v2.5-system-prompt-2026-09-04.md):
  el nivel cambia el modelo detrás de la petición y nada de la petición. Y
  [el prompt de sistema de Cursor](../../Cursor/cursor-grok-4.5-high-system-prompt-2026-09-03.md)
  son 1.955 caracteres — se compone en los servidores de Cursor y vuelve en la *respuesta*, mientras
  otros 19 KB de entorno, reglas, skills y espacios de nombres de herramientas viajan en el turno
  del usuario.

## Estructura

```
Orca-PromptVault/
├── README.md · CONTRIBUTING.md · LICENSE
├── docs/
│   ├── CAPTURES.md          cada captura + el comando que la reproduce
│   ├── UPSTREAM.md          lo que viene de CL4R1T4S, ruta por ruta
│   └── i18n/                este README en 7 idiomas más
├── OpenAI/         ChatGPT/ · Codex/
├── Anthropic/      Claude/ · Claude-Code/
├── Google/         Gemini/ · Gemini-CLI/
├── xAI/            Grok/
├── Cursor/
├── Moonshot/       Kimi/
├── Alibaba/        Qwen/
├── ZAI/            GLM/
├── DeepSeek/
├── Meta/
└── Others/         una carpeta por producto
```

Los archivos van bajo **quien envía el prompt**, no bajo quien entrenó el modelo. Un modelo de
NVIDIA movido por OpenCode va bajo OpenCode, porque esas instrucciones las escribió OpenCode; el
asistente propio de Meta va bajo Meta. Un archivo por captura, nombrado
`<harness>-<model>-<artifact>-<date>`, para que un archivo sacado por su cuenta siga diciendo de
dónde salió.

## Contribuir

Prompts, esquemas de herramientas, definiciones de skills, instrucciones de arnés — de cualquier
producto y en cualquier idioma. Una captura con comando reproducible es el patrón oro; una
transcripción fechada y honesta también es bienvenida. [CONTRIBUTING.md](../../CONTRIBUTING.md)
tiene las reglas de nombrado, la cabecera de procedencia y la lista corta de lo que no aceptamos
(nada con credenciales ni datos personales, ni textos escritos por ti sin fuente).

Lo más buscado ahora mismo: DeepSeek, Gemini CLI, Kimi CLI / el agente K2, la parte de código de
GLM, Copilot, la build actual de Devin, y cualquier cosa de un producto que no sea en inglés.

## Procedencia, ética, retiradas

Son las instrucciones que un proveedor envía a un modelo en nombre de una persona usuaria —
visibles para esa persona por construcción, y archivadas aquí para investigación, interoperabilidad
y comprensión pública de sistemas en los que ya confían millones. Nada de esto se obtuvo forzando
nada: las capturas vienen de un proxy en nuestras propias máquinas, leyendo nuestro propio tráfico,
durante nuestras propias sesiones.

Nada aquí contiene credenciales, claves de API, datos personales ni identificadores de cuenta; cada
captura se limpia antes de escribirse y la que no se puede limpiar no se publica. Los prompts siguen
siendo de sus autores. Si uno es tuyo y quieres que desaparezca, abre una issue y se va.

Este archivo sirve para entender agentes, no para desmontar su trabajo de seguridad. Los pull
requests cuyo propósito es una carga de jailbreak se rechazan.

## Créditos

Todo lo que aquí no es una captura de OrcaReplay — 75 de las 106 piezas, cuatro quintas partes de
los bytes — se hereda de [CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S), de
**@elder_plinius**, cuyo trabajo demostró primero que estos documentos merecían conservarse. Este
repositorio arrastra esa historia commit a commit, mantiene la AGPL-3.0 y suma al fondo en lugar de
sustituirlo. Cada archivo heredado está referido a su ruta original en
[docs/UPSTREAM.md](../UPSTREAM.md).

La mitad *capturada* la produce
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay), que graba cualquier agente de código
y reproduce la sesión byte a byte sin llamar a ningún modelo.

## Licencia

[AGPL-3.0](../../LICENSE) para este repositorio. Los prompts archivados son obra de sus respectivos
dueños y se recogen aquí bajo fair use, para investigación y transparencia.
