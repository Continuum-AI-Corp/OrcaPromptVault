# Orca PromptVault

<sub>[English](../../README.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · **Deutsch** · [Français](README.fr.md) · [Español](README.es.md) · [العربية](README.ar.md)</sub>

### Das offene Archiv darüber, wie KI-Agenten tatsächlich funktionieren.

Ein versioniertes, überprüfbares Archiv der System-Prompts, Entwickleranweisungen, Tool-Schemata
und Agent-Harnesses hinter den heutigen KI-Produkten. Aufgezeichnet mit
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay).

<a href="https://www.orcarouter.ai">
  <img src="../orcarouter.svg" alt="OrcaRouter" height="28" align="left" hspace="10">
</a>

**Gebaut vom Team hinter [OrcaRouter](https://www.orcarouter.ai)** — ein API-Schlüssel und ein
Endpunkt für Claude, GPT, Gemini, Grok, DeepSeek, Qwen und den Rest.

Mehr: [Alle Modell-APIs](https://www.orcarouter.ai/models) · [OrcaCode Review](https://www.orcarouter.ai/code-review) · [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) · [OrcaRouter Lite](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)

Kontakt: [X](https://x.com/OrcaRouter) · [Discord](https://discord.com/invite/YEubt8enRA) · [Hugging Face](https://huggingface.co/orcarouter) · [Ollama](https://ollama.com/orcarouter)

<br clear="left">

[![Artifacts](https://img.shields.io/badge/artifacts-106-blue)](#was-drin-ist)
[![Captured](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../CAPTURES.md)
[![Tool schemas](https://img.shields.io/badge/tool%20schemas-15-brightgreen)](../CAPTURES.md)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](../../LICENSE)

## Warum es das gibt

Das Verhalten eines Agenten steckt nicht nur in seinen Gewichten. Es steckt in den gut
zwanzigtausend Zeichen Anweisungen, die ein Harness zusammensetzt und *vor* dem ersten Wort der
Nutzerin abschickt, und in den fünfunddreißig Tool-Definitionen, die mitgehen. Dieser Text
entscheidet, was der Agent ablehnt, nach welchem Werkzeug er zuerst greift, wie er spricht und was
man ihm über sein Gegenüber erzählt hat.

Wer ihn liest, hat kein Blackbox-Produkt mehr vor sich. Wer ihn datiert und diff-bar aufbewahrt,
muss über Verhaltensänderungen nicht mehr spekulieren, sondern kann auf die Zeile zeigen, die sich
geändert hat.

## Was drin ist

| Ordner | Inhalt | Dateien | 🐋 erfasst |
|---|---|---|---|
| [OpenAI](../../OpenAI/) | [ChatGPT](../../OpenAI/ChatGPT/) 4o · 4.1 · 4.5 · 5 · o3/o4-mini · Atlas, [Codex](../../OpenAI/Codex/) CLI · Cloud · Desktop, ChatKit Studio | 21 | 5 |
| [Anthropic](../../Anthropic/) | [Claude](../../Anthropic/Claude/) Sonnet 3.5 → Opus 5 · Fable 5.1 · Design · User Styles, [Claude Code](../../Anthropic/Claude-Code/) CLI und Agent SDK | 22 | 8 |
| [Google](../../Google/) | [Gemini](../../Google/Gemini/) 2.5 Pro · Diffusion · Gmail-Assistent | 3 | — |
| [xAI](../../xAI/) | [Grok](../../xAI/Grok/) 3 · 4 · 4.1 · 4.20 · Code Fast 1 | 7 | — |
| [Cursor](../../Cursor/) | Cursor Agent · Cursor 2.0 · Composer auf Grok 4.5 | 4 | 1 |
| [Moonshot](../../Moonshot/) | [Kimi](../../Moonshot/Kimi/) K2 · K2 Thinking | 2 | — |
| [Alibaba](../../Alibaba/) | [Qwen Code](../../Alibaba/Qwen/) CLI | 2 | 2 |
| [ZAI](../../ZAI/) | [ZCode](../../ZAI/GLM/) Prompt · Skills · Tools | 3 | — |
| [DeepSeek](../../DeepSeek/) | noch nichts — [gesucht](../../CONTRIBUTING.md#wanted) | 0 | — |
| [Meta](../../Meta/) | Meta AI auf Muse Spark · Llama 4 in WhatsApp | 2 | — |
| [Others](../../Others/) | OpenCode · Devin · Windsurf · Cline · Replit · Manus · v0 · Bolt · Lovable · Perplexity · Mistral · MiniMax · MiMoCode · Hermes · Kilo Code · Dia · Brave Leo · Factory Droid · Hume · Cluely · Same.dev · MultiOn | 40 | 15 |

🐋 Einunddreißig dieser Dateien stammen direkt aus der Leitung, auf unseren eigenen Rechnern — zwanzig
Aufzeichnungen, mit Größen, Harness-Versionen und dem Befehl, der jede reproduziert, in
**[docs/CAPTURES.md](../CAPTURES.md)**. Die anderen fünfundsiebzig sind unverändert aus CL4R1T4S
übernommen und Pfad für Pfad in **[docs/UPSTREAM.md](../UPSTREAM.md)** verzeichnet.

## Aufgezeichnet oder berichtet

Jede Datei hier ist eines von beidem, und der Unterschied wiegt schwerer als der Inhalt.

**Aufgezeichnet** — von einem lokalen Proxy aus der Leitung geholt, während das echte Harness
unverändert lief: der Prompt, den das Werkzeug auf dieser Maschine tatsächlich gesendet hat,
bereinigt um alles Identifizierende, abgelegt mit Harness-Version, Modus, Zeichenzahl und dem einen
Befehl, der ihn erneut erzeugt. Man muss dem nicht glauben. Befehl ausführen, diffen.

**Berichtet** — alles, was ein lokaler Proxy nicht sehen kann. Ein Chat-Produkt setzt seinen Prompt
serverseitig zusammen: claude.ai, ChatGPT und Gemini schicken ihn nie von der eigenen Maschine los.
Sein Text lässt sich also nur bekommen, indem das Modell ihn wiedergibt, und er kommt als
Mitschrift an, nicht als Bytes auf der Leitung. Diese Dateien werden so archiviert, wie sie
eingegangen sind, datiert wo das Datum bekannt ist, samt der Unsicherheit, die dazugehört.
Aufgezeichnetes ist Beweis, Berichtetes ist Zeugenaussage.

## Selbst eine aufzeichnen

```console
npm i -g orcareplay
git clone https://github.com/Continuum-AI-Corp/OrcaReplay
node capture/capture.mjs claude --model claude-opus-5
```

Das startet einen lokalen Proxy, lässt den Agenten unverändert laufen, wartet auf die Anfrage, die
den Prompt trägt, holt ihn heraus, ersetzt Home-Verzeichnis, Benutzernamen, Git-Identität und
Gateway durch Platzhalter und schreibt eine Datei. Danach hier einen Pull Request aufmachen — siehe
[CONTRIBUTING.md](../../CONTRIBUTING.md).

Codex, OpenCode, Qwen Code, Cursor, MiMoCode, Kilo und Hermes gehen denselben Weg; die
[Capture-Notizen](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/README.md)
decken die Details pro Harness ab, einschließlich der fünf, die mit `--tls-intercept` erreicht
werden müssen, weil sich ihr Ziel nicht per Umgebungsvariable verschieben lässt.

## Was das Archiv jetzt schon zeigt

Vier Befunde, alle an den Dateien in diesem Repository nachprüfbar:

- **Das Harness ist die Variable.** Ein Modell, `nemotron-3.5-lightning-free`, auf zwei Harnesses:
  [9.656 Zeichen und 11 Tools von OpenCode](../../Others/OpenCode/opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md),
  [14.049 und 19 von Hermes](../../Others/Hermes/hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md).
  Gleiches Modell, gleicher kostenloser Endpunkt, andere Anweisungen, andere Werkzeugfläche.
- **Das Modell ebenso.** [OpenCode](../../Others/OpenCode/) schickt über sieben Modelle drei
  verschiedene Vorlagen. Fünf kostenlose beginnen mit *You are opencode, an interactive CLI tool*;
  Muse Spark bekommt einen anderen Einstieg und den Responses-Dialekt; GPT-5.6-Sol bekommt eine
  dritte Vorlage und `apply_patch` statt `edit` und `write`. Prompt und Wire-Format werden pro
  Modell gewählt.
- **Interaktiv ist nicht derselbe Prompt wie `-p`.** Claude Code sendet auf Fable 5.1 aus dem
  Terminal [26.131 Zeichen und 35 Tools](../../Anthropic/Claude-Code/claude-code-fable-5.1-system-prompt-2026-09-02.md)
  und aus einem Skript [20.806 und 29](../../Anthropic/Claude-Code/claude-code-fable-5.1-print-system-prompt-2026-09-02.md),
  wobei sich schon die Identitätszeile zu *You are a Claude agent, built on Anthropic's Claude Agent
  SDK* ändert. Der Prompt des Alltags und der, den der CI-Job bekommt, sind zwei Prompts.
- **Eine Stufe ist kein Prompt.** MiMoCode sendet für `mimo-v2.5` und `mimo-v2.5-pro`
  [byte-identischen Text und identische Tools](../../Others/MiMoCode/mimocode-mimo-v2.5-system-prompt-2026-09-04.md).
  Die Stufe ändert das Modell hinter der Anfrage und nichts an der Anfrage. Und
  [Cursors System-Prompt](../../Cursor/cursor-grok-4.5-high-system-prompt-2026-09-03.md) hat 1.955
  Zeichen — serverseitig zusammengesetzt und in der *Antwort* zurückgeschickt, während weitere
  19 KB Umgebung, Regeln, Skills und Tool-Namespaces im User-Turn mitfahren.

## Aufbau

```
Orca-PromptVault/
├── README.md · CONTRIBUTING.md · LICENSE
├── docs/
│   ├── CAPTURES.md          jede Aufzeichnung + der Befehl, der sie reproduziert
│   ├── UPSTREAM.md          was aus CL4R1T4S stammt, Pfad für Pfad
│   └── i18n/                dieses README in 7 weiteren Sprachen
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
└── Others/         ein Ordner pro Produkt
```

Dateien liegen bei dem, **der den Prompt verschickt**, nicht bei dem, der das Modell trainiert hat.
Ein NVIDIA-Modell unter OpenCode liegt bei OpenCode, weil OpenCode diese Anweisungen geschrieben
hat; Metas eigener Assistent liegt bei Meta. Eine Datei pro Aufzeichnung, benannt nach
`<harness>-<model>-<artifact>-<date>`, damit eine einzeln herausgezogene Datei immer noch sagt,
woher sie kommt.

## Mitmachen

Prompts, Tool-Schemata, Skill-Definitionen, Harness-Anweisungen — aus jedem Produkt, in jeder
Sprache. Eine Aufzeichnung mit reproduzierbarem Befehl ist der Goldstandard; eine datierte,
ehrliche Mitschrift ist ebenfalls willkommen. [CONTRIBUTING.md](../../CONTRIBUTING.md) enthält die
Namensregeln, den Herkunfts-Header und die kurze Liste dessen, was wir nicht annehmen (alles mit
Zugangsdaten oder personenbezogenen Daten sowie selbst geschriebene Texte ohne Quelle).

Derzeit am dringendsten gesucht: DeepSeek, Gemini CLI, Kimi CLI / K2-Agent, GLMs Coding-Seite,
Copilot, Devins aktueller Build und alles aus nicht-englischsprachigen Produkten.

## Herkunft, Ethik, Löschungen

Das sind die Anweisungen, die ein Anbieter im Namen einer Nutzerin an ein Modell schickt — für
diese Nutzerin konstruktionsbedingt sichtbar und hier archiviert für Forschung,
Interoperabilität und das öffentliche Verständnis von Systemen, denen inzwischen Millionen
vertrauen. Nichts davon wurde durch Einbruch beschafft: Die Aufzeichnungen stammen von einem Proxy
auf unseren eigenen Rechnern, der unseren eigenen Verkehr in unseren eigenen Sitzungen liest.

Nichts hier enthält Zugangsdaten, API-Schlüssel, personenbezogene Daten oder Konto-Identifikatoren;
jede Aufzeichnung wird vor dem Schreiben bereinigt, und was sich nicht bereinigen lässt, wird nicht
veröffentlicht. Die Rechte an den Prompts bleiben bei ihren Autoren. Wer einen davon entfernt haben
möchte, macht ein Issue auf — dann verschwindet er.

Dieses Archiv dient dem Verstehen von Agenten, nicht dem Aushebeln ihrer Sicherheitsarbeit. Pull
Requests, deren Zweck ein Jailbreak-Payload ist, werden abgelehnt.

## Dank

Alles hier, was keine OrcaReplay-Aufzeichnung ist — 75 der 106 Artefakte, vier Fünftel der Bytes —
stammt aus [CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S) von **@elder_plinius**, dessen
Arbeit zuerst gezeigt hat, dass diese Dokumente überhaupt aufbewahrenswert sind. Dieses Repository
trägt jene Historie Commit für Commit weiter, behält AGPL-3.0 bei und ergänzt den Bestand, statt ihn
zu ersetzen. Jede übernommene Datei ist in [docs/UPSTREAM.md](../UPSTREAM.md) auf ihren
ursprünglichen Pfad zurückgeführt.

Die *aufgezeichnete* Hälfte entsteht mit
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay), das jeden Coding-Agenten aufnimmt und
den Lauf byte-für-byte wiedergibt, ohne ein Modell aufzurufen.

## Lizenz

[AGPL-3.0](../../LICENSE) für dieses Repository. Die archivierten Prompts sind das Werk ihrer
jeweiligen Urheber und werden hier unter Fair Use für Forschung und Transparenz gesammelt.
