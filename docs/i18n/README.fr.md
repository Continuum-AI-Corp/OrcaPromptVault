# Orca PromptVault

<sub>[English](../../README.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Deutsch](README.de.md) · **Français** · [Español](README.es.md) · [العربية](README.ar.md)</sub>

### L'archive ouverte du fonctionnement réel des agents IA.

Une archive versionnée et vérifiable des prompts système, instructions développeur, schémas
d'outils et harnais d'agents qui font tourner les produits IA d'aujourd'hui. Capturée avec
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay).

<a href="https://www.orcarouter.ai">
  <img src="../orcarouter.svg" alt="OrcaRouter" height="28" align="left" hspace="10">
</a>

**Construit par l'équipe derrière [OrcaRouter](https://www.orcarouter.ai)** — une clé d'API et un
point d'entrée pour Claude, GPT, Gemini, Grok, DeepSeek, Qwen et les autres.

Aussi : [toutes les API modèles](https://www.orcarouter.ai/models) · [OrcaCode Review](https://www.orcarouter.ai/code-review) · [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) · [OrcaRouter Lite](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)

Nous joindre : [X](https://x.com/OrcaRouter) · [Discord](https://discord.com/invite/YEubt8enRA) · [Hugging Face](https://huggingface.co/orcarouter) · [Ollama](https://ollama.com/orcarouter)

<br clear="left">

[![Artifacts](https://img.shields.io/badge/artifacts-106-blue)](#ce-quon-y-trouve)
[![Captured](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../CAPTURES.md)
[![Tool schemas](https://img.shields.io/badge/tool%20schemas-15-brightgreen)](../CAPTURES.md)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](../../LICENSE)

## Pourquoi cette archive

Le comportement d'un agent ne tient pas qu'à ses poids. Il tient aussi aux quelque vingt mille
caractères d'instructions que le harnais assemble et envoie *avant* votre premier mot, et aux
trente-cinq définitions d'outils qui partent avec. Ce texte décide de ce que l'agent refuse, de
l'outil qu'il saisit en premier, du ton qu'il adopte, et de ce qu'on lui a dit de vous.

Le lire, c'est cesser d'avoir affaire à une boîte noire. Le conserver daté et comparable, c'est
transformer un changement de comportement en une ligne qu'on peut montrer du doigt.

## Ce qu'on y trouve

| dossier | contenu | fichiers | 🐋 captures |
|---|---|---|---|
| [OpenAI](../../OpenAI/) | [ChatGPT](../../OpenAI/ChatGPT/) 4o · 4.1 · 4.5 · 5 · o3/o4-mini · Atlas, [Codex](../../OpenAI/Codex/) CLI · cloud · desktop, ChatKit Studio | 21 | 5 |
| [Anthropic](../../Anthropic/) | [Claude](../../Anthropic/Claude/) Sonnet 3.5 → Opus 5 · Fable 5.1 · Design · styles utilisateur, [Claude Code](../../Anthropic/Claude-Code/) CLI et Agent SDK | 22 | 8 |
| [Google](../../Google/) | [Gemini](../../Google/Gemini/) 2.5 Pro · Diffusion · assistant Gmail | 3 | — |
| [xAI](../../xAI/) | [Grok](../../xAI/Grok/) 3 · 4 · 4.1 · 4.20 · Code Fast 1 | 7 | — |
| [Cursor](../../Cursor/) | agent Cursor · Cursor 2.0 · Composer sur Grok 4.5 | 4 | 1 |
| [Moonshot](../../Moonshot/) | [Kimi](../../Moonshot/Kimi/) K2 · K2 Thinking | 2 | — |
| [Alibaba](../../Alibaba/) | [Qwen Code](../../Alibaba/Qwen/) CLI | 2 | 2 |
| [ZAI](../../ZAI/) | [ZCode](../../ZAI/GLM/) prompt · skills · tools | 3 | — |
| [DeepSeek](../../DeepSeek/) | rien encore — [recherché](../../CONTRIBUTING.md#wanted) | 0 | — |
| [Meta](../../Meta/) | Meta AI sur Muse Spark · Llama 4 dans WhatsApp | 2 | — |
| [Others](../../Others/) | OpenCode · Devin · Windsurf · Cline · Replit · Manus · v0 · Bolt · Lovable · Perplexity · Mistral · MiniMax · MiMoCode · Hermes · Kilo Code · Dia · Brave Leo · Factory Droid · Hume · Cluely · Same.dev · MultiOn | 40 | 15 |

🐋 Trente et un de ces fichiers ont été pris sur le fil, sur nos propres machines — vingt captures,
avec tailles, versions de harnais et la commande qui reproduit chacune :
**[docs/CAPTURES.md](../CAPTURES.md)**. Les soixante-quinze autres sont hérités de CL4R1T4S sans
retouche, et répertoriés chemin par chemin dans **[docs/UPSTREAM.md](../UPSTREAM.md)**.

## Capturé, ou rapporté

Chaque fichier ici est l'un ou l'autre, et la différence compte davantage que le contenu.

**Capturé** — prélevé sur le fil par un proxy local pendant que le vrai harnais tournait sans
modification : le prompt que l'outil de cette machine a effectivement envoyé, nettoyé de tout
élément identifiant, classé avec sa version de harnais, son mode, sa taille et l'unique commande
qui le reproduit. Inutile de nous croire : lancez la commande et faites le diff.

**Rapporté** — tout ce qu'un proxy local ne peut pas voir. Un produit de chat assemble son prompt
côté serveur : claude.ai, ChatGPT et Gemini ne l'envoient jamais depuis votre machine. Son texte ne
s'obtient donc qu'en le faisant répéter par le modèle, et il arrive sous forme de transcription, pas
d'octets sur le fil. Ces fichiers sont archivés tels que reçus, datés quand la date est connue, avec
l'incertitude que cela suppose. Le capturé est une preuve, le rapporté un témoignage.

## Capturez-en un vous-même

```console
npm i -g orcareplay
git clone https://github.com/Continuum-AI-Corp/OrcaReplay
node capture/capture.mjs claude --model claude-opus-5
```

Le script monte un proxy local, lance l'agent sans le modifier, attend la requête qui porte le
prompt, l'en extrait, remplace votre répertoire personnel, votre nom d'utilisateur, votre identité
git et votre passerelle par des marqueurs, puis écrit un fichier. Ensuite, ouvrez une pull request
ici — voir [CONTRIBUTING.md](../../CONTRIBUTING.md).

Codex, OpenCode, Qwen Code, Cursor, MiMoCode, Kilo et Hermes suivent le même chemin ; les
[notes de capture](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/README.md)
couvrent le détail par harnais, dont les cinq qu'il faut atteindre avec `--tls-intercept`, faute de
pouvoir déplacer leur origine par une variable d'environnement.

## Ce que l'archive montre déjà

Quatre constats, tous vérifiables sur les fichiers de ce dépôt :

- **La variable, c'est le harnais.** Un même modèle, `nemotron-3.5-lightning-free`, sur deux
  harnais : [9 656 caractères et 11 outils chez OpenCode](../../Others/OpenCode/opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md),
  [14 049 et 19 chez Hermes](../../Others/Hermes/hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md).
  Même modèle, même point d'entrée gratuit, instructions et surface d'outils différentes.
- **Le modèle aussi.** [OpenCode](../../Others/OpenCode/) envoie trois gabarits différents sur sept
  modèles. Cinq modèles gratuits ouvrent sur *You are opencode, an interactive CLI tool* ; Muse
  Spark reçoit une autre ouverture et le dialecte responses ; GPT-5.6-Sol reçoit un troisième
  gabarit, avec `apply_patch` à la place de `edit` et `write`. Le prompt et le format de transport
  sont choisis modèle par modèle.
- **L'interactif n'est pas le même prompt que `-p`.** Sur Fable 5.1, Claude Code envoie depuis un
  terminal [26 131 caractères et 35 outils](../../Anthropic/Claude-Code/claude-code-fable-5.1-system-prompt-2026-09-02.md),
  et depuis un script [20 806 et 29](../../Anthropic/Claude-Code/claude-code-fable-5.1-print-system-prompt-2026-09-02.md),
  la ligne d'identité elle-même devenant *You are a Claude agent, built on Anthropic's Claude Agent
  SDK*. Le prompt de l'usage quotidien et celui que reçoit votre CI sont deux prompts.
- **Un palier n'est pas un prompt.** MiMoCode envoie à `mimo-v2.5` et `mimo-v2.5-pro`
  [un texte et des outils identiques à l'octet](../../Others/MiMoCode/mimocode-mimo-v2.5-system-prompt-2026-09-04.md) :
  le palier change le modèle derrière la requête, pas la requête. Et
  [le prompt système de Cursor](../../Cursor/cursor-grok-4.5-high-system-prompt-2026-09-03.md) fait
  1 955 caractères — composé sur les serveurs de Cursor et renvoyé dans la *réponse*, tandis que
  19 Ko d'environnement, de règles, de skills et d'espaces de noms d'outils voyagent dans le tour
  utilisateur.

## Organisation

```
Orca-PromptVault/
├── README.md · CONTRIBUTING.md · LICENSE
├── docs/
│   ├── CAPTURES.md          chaque capture + la commande qui la reproduit
│   ├── UPSTREAM.md          ce qui vient de CL4R1T4S, chemin par chemin
│   └── i18n/                ce README en 7 autres langues
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
└── Others/         un dossier par produit
```

Les fichiers sont classés sous **celui qui envoie le prompt**, pas sous celui qui a entraîné le
modèle. Un modèle NVIDIA piloté par OpenCode est classé sous OpenCode, parce que ces instructions
sont celles d'OpenCode ; l'assistant maison de Meta est classé sous Meta. Un fichier par capture,
nommé `<harness>-<model>-<artifact>-<date>`, pour qu'un fichier sorti seul de son dossier dise
encore d'où il vient.

## Contribuer

Prompts, schémas d'outils, définitions de skills, instructions de harnais — de n'importe quel
produit, dans n'importe quelle langue. Une capture assortie d'une commande reproductible est
l'étalon-or ; une transcription datée et honnête est également bienvenue.
[CONTRIBUTING.md](../../CONTRIBUTING.md) donne les règles de nommage, l'en-tête de provenance et la
courte liste de ce que nous refusons (tout ce qui contient des identifiants ou des données
personnelles, et les textes que vous avez écrits sans pouvoir en citer la source).

Les plus recherchés en ce moment : DeepSeek, Gemini CLI, Kimi CLI / l'agent K2, la partie codage de
GLM, Copilot, la build actuelle de Devin, et tout ce qui vient d'un produit non anglophone.

## Provenance, éthique, retraits

Ce sont les instructions qu'un éditeur envoie à un modèle au nom d'un utilisateur — visibles par cet
utilisateur par construction, et archivées ici pour la recherche, l'interopérabilité et la
compréhension publique de systèmes auxquels des millions de personnes font désormais confiance. Rien
n'a été obtenu en forçant quoi que ce soit : les captures viennent d'un proxy sur nos propres
machines, lisant notre propre trafic, pendant nos propres sessions.

Rien ici ne contient d'identifiants, de clés d'API, de données personnelles ou d'identifiants de
compte ; chaque capture est nettoyée avant d'être écrite, et une capture qui ne peut pas l'être
n'est pas publiée. Les prompts restent la propriété de leurs auteurs. Si l'un d'eux est le vôtre et
que vous voulez son retrait, ouvrez une issue : il disparaît.

Cette archive sert à comprendre les agents, pas à défaire leur travail de sécurité. Les pull
requests dont l'objet est une charge de jailbreak sont refusées.

## Remerciements

Tout ce qui n'est pas une capture OrcaReplay — 75 des 106 pièces, quatre cinquièmes des octets —
est hérité de [CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S) de **@elder_plinius**, dont le
travail a d'abord montré que ces documents méritaient d'être conservés. Ce dépôt reprend cet
historique commit par commit, conserve l'AGPL-3.0 et complète le fonds au lieu de le remplacer. Chaque fichier hérité
est ramené à son chemin d'origine dans [docs/UPSTREAM.md](../UPSTREAM.md).

La moitié *capturée* est produite par
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay), qui enregistre n'importe quel agent
de code et rejoue la session octet pour octet sans appeler le moindre modèle.

## Licence

[AGPL-3.0](../../LICENSE) pour ce dépôt. Les prompts archivés sont l'œuvre de leurs propriétaires
respectifs et sont réunis ici au titre du fair use, pour la recherche et la transparence.
