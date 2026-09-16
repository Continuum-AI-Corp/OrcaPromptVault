# Orca PromptVault

<sub>[English](../../README.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [Español](README.es.md) · **العربية**</sub>

<div dir="rtl">

### الأرشيف المفتوح لكيفية عمل وكلاء الذكاء الاصطناعي فعليًا.

أرشيف مُؤرَّخ وقابل للتحقق يضم مُوجّهات النظام، وتعليمات المطوّرين، ومخططات الأدوات، وأُطر تشغيل
الوكلاء التي تُشغّل منتجات الذكاء الاصطناعي اليوم. مُلتقط بواسطة
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay).

<a href="https://www.orcarouter.ai">
  <img src="../orcarouter.svg" alt="OrcaRouter" height="28" align="left" hspace="10">
</a>

**من صنع الفريق الذي يقف خلف [OrcaRouter](https://www.orcarouter.ai)** — مفتاح API واحد ونقطة نهاية
واحدة تصل إلى Claude وGPT وGemini وGrok وDeepSeek وQwen وسواها.

روابط: [كل واجهات النماذج](https://www.orcarouter.ai/models) · [OrcaCode Review](https://www.orcarouter.ai/code-review) · [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) · [OrcaRouter Lite](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)

تواصل: [X](https://x.com/OrcaRouter) · [Discord](https://discord.com/invite/YEubt8enRA) · [Hugging Face](https://huggingface.co/orcarouter) · [Ollama](https://ollama.com/orcarouter)

<br clear="left">

[![Artifacts](https://img.shields.io/badge/artifacts-106-blue)](../CAPTURES.md)
[![Captured](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../CAPTURES.md)
[![Tool schemas](https://img.shields.io/badge/tool%20schemas-15-brightgreen)](../CAPTURES.md)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](../../LICENSE)

## لماذا هذا الأرشيف

سلوك الوكيل لا يسكن في أوزانه وحدها. إنه يسكن كذلك في نحو عشرين ألف حرف من التعليمات التي يجمعها
إطار التشغيل ويرسلها *قبل* كلمتك الأولى، وفي خمسة وثلاثين تعريف أداة تُرسَل معها. هذا النص هو ما
يقرّر ما الذي يرفضه الوكيل، وأي أداة يمدّ يده إليها أولًا، وبأي نبرة يخاطبك، وما الذي قيل له عنك.

اقرأه، فيكفّ المنتج عن كونه صندوقًا أسود. احفظه مؤرَّخًا وقابلًا للمقارنة، فيكفّ تغيّر السلوك عن
كونه إشاعة: يصير سطرًا يمكن الإشارة إليه.

## ماذا يضم

| المجلد | المحتوى | الملفات | منها ملتقَط |
|---|---|---|---|
| [OpenAI](../../OpenAI/) | [ChatGPT](../../OpenAI/ChatGPT/) 4o · 4.1 · 4.5 · 5 · o3/o4-mini · Atlas، و[Codex](../../OpenAI/Codex/) CLI · cloud · desktop، وChatKit Studio | 21 | 5 |
| [Anthropic](../../Anthropic/) | [Claude](../../Anthropic/Claude/) من Sonnet 3.5 إلى Opus 5 · Fable 5.1 · Design · أنماط المستخدم، و[Claude Code](../../Anthropic/Claude-Code/) بواجهة CLI وAgent SDK | 22 | 8 |
| [Google](../../Google/) | [Gemini](../../Google/Gemini/) 2.5 Pro · Diffusion · مساعد Gmail | 3 | — |
| [xAI](../../xAI/) | [Grok](../../xAI/Grok/) 3 · 4 · 4.1 · 4.20 · Code Fast 1 | 7 | — |
| [Cursor](../../Cursor/) | وكيل Cursor · Cursor 2.0 · Composer على Grok 4.5 | 4 | 1 |
| [Moonshot](../../Moonshot/) | [Kimi](../../Moonshot/Kimi/) K2 · K2 Thinking | 2 | — |
| [Alibaba](../../Alibaba/) | [Qwen Code](../../Alibaba/Qwen/) CLI | 2 | 2 |
| [ZAI](../../ZAI/) | [ZCode](../../ZAI/GLM/): المُوجّه · المهارات · الأدوات | 3 | — |
| [DeepSeek](../../DeepSeek/) | لا شيء بعد — [مطلوب](../../CONTRIBUTING.md#wanted) | 0 | — |
| [Meta](../../Meta/) | Meta AI على Muse Spark · Llama 4 داخل WhatsApp | 2 | — |
| [Others](../../Others/) | OpenCode · Devin · Windsurf · Cline · Replit · Manus · v0 · Bolt · Lovable · Perplexity · Mistral · MiniMax · MiMoCode · Hermes · Kilo Code · Dia · Brave Leo · Factory Droid · Hume · Cluely · Same.dev · MultiOn | 40 | 15 |

واحد وثلاثون من هذه الملفات أُخذت من الشبكة مباشرة على أجهزتنا — عشرون عملية التقاط، بأحجامها
وإصدارات أطر تشغيلها والأمر الذي يعيد إنتاج كل واحدة، في **[docs/CAPTURES.md](../CAPTURES.md)**.
أما الخمسة والسبعون الأخرى فموروثة من CL4R1T4S دون أي تعديل، ومفهرسة مسارًا بمسار في
**[docs/UPSTREAM.md](../UPSTREAM.md)**.

## مُلتقَط أم منقول

كل ملف هنا ينتمي إلى أحد نوعين، والفرق بينهما أهم من المحتوى نفسه.

**مُلتقَط** — انتُزع من الشبكة عبر وسيط محلي بينما كان إطار التشغيل الحقيقي يعمل دون أي تعديل: هو
المُوجّه الذي أرسلته الأداة فعلًا من هذا الجهاز، منزوعًا منه كل ما يدل على صاحبه، ومحفوظًا مع إصدار
إطار التشغيل ونمط التشغيل وعدد الحروف والأمر الوحيد الذي ينتجه من جديد. لا داعي لتصديقنا: شغّل
الأمر ثم قارن.

**منقول** — كل ما لا يستطيع وسيط محلي رؤيته. منتجات المحادثة تجمع مُوجّهها على الخادم: لا يرسله
claude.ai ولا ChatGPT ولا Gemini من جهازك أبدًا، فلا سبيل إلى نصه إلا بأن يعيده النموذج نفسه، ويصلنا
تفريغًا لا بايتات على الشبكة. تُحفظ هذه الملفات كما وصلت، مؤرَّخة حيث يُعرف التاريخ، وبما يرافقها من
عدم يقين. عامل المُلتقَط معاملة الدليل، والمنقول معاملة الشهادة.

## التقط واحدًا بنفسك

<div dir="ltr">

```console
npm i -g orcareplay
git clone https://github.com/Continuum-AI-Corp/OrcaReplay
node capture/capture.mjs claude --model claude-opus-5
```

</div>

يُشغّل وسيطًا محليًا، ويطلق الوكيل دون تعديل، وينتظر الطلب الذي يحمل المُوجّه، ثم ينتزعه ويستبدل
بمجلد المنزل واسم المستخدم وهوية git وعنوان البوابة رموزًا نائبة، ويكتب ملفًا واحدًا. بعدها افتح طلب
سحب هنا — انظر [CONTRIBUTING.md](../../CONTRIBUTING.md).

وتسلك Codex وOpenCode وQwen Code وCursor وMiMoCode وKilo وHermes الطريق نفسه؛ وتغطي
[ملاحظات الالتقاط](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/README.md)
تفاصيل كل إطار، ومنها خمسة لا بد من بلوغها بـ `--tls-intercept` لأن وجهتها لا تتحرك بمتغيّر بيئة.

## ما يكشفه الأرشيف بالفعل

أربع نتائج، كلها قابلة للتحقق من ملفات هذا المستودع:

- **إطار التشغيل هو المتغيّر.** نموذج واحد، `nemotron-3.5-lightning-free`، على إطارين:
  [9,656 حرفًا و11 أداة من OpenCode](../../Others/OpenCode/opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md)،
  مقابل [14,049 حرفًا و19 أداة من Hermes](../../Others/Hermes/hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md).
  النموذج نفسه، ونقطة النهاية المجانية نفسها، وتعليمات وسطح أدوات مختلفان.
- **والنموذج متغيّر أيضًا.** يرسل [OpenCode](../../Others/OpenCode/) ثلاثة قوالب مختلفة عبر سبعة
  نماذج. خمسة نماذج مجانية تبدأ بـ *You are opencode, an interactive CLI tool*؛ ويحصل Muse Spark
  على مطلع آخر وعلى لهجة responses؛ ويحصل GPT-5.6-Sol على قالب ثالث وعلى `apply_patch` بدل `edit`
  و`write`. المُوجّه وصيغة النقل كلاهما يُختار حسب النموذج.
- **الوضع التفاعلي ليس المُوجّه نفسه الذي يعطيه `-p`.** يرسل Claude Code على Fable 5.1 من الطرفية
  [26,131 حرفًا و35 أداة](../../Anthropic/Claude-Code/claude-code-fable-5.1-system-prompt-2026-09-02.md)،
  ومن سكربت [20,806 حرفًا و29 أداة](../../Anthropic/Claude-Code/claude-code-fable-5.1-print-system-prompt-2026-09-02.md)،
  حتى إن سطر التعريف نفسه يتحول إلى *You are a Claude agent, built on Anthropic's Claude Agent SDK*.
  المُوجّه الذي تستعمله يوميًا وذاك الذي تحصل عليه وظيفة CI مُوجّهان مختلفان.
- **الدرجة ليست مُوجّهًا.** يرسل MiMoCode إلى `mimo-v2.5` و`mimo-v2.5-pro`
  [نصًا وأدوات متطابقة بايتًا ببايت](../../Others/MiMoCode/mimocode-mimo-v2.5-system-prompt-2026-09-04.md):
  الدرجة تغيّر النموذج خلف الطلب ولا تغيّر من الطلب شيئًا. أما
  [مُوجّه نظام Cursor](../../Cursor/cursor-grok-4.5-high-system-prompt-2026-09-03.md) فطوله 1,955
  حرفًا — يُركَّب على خوادم Cursor ويعود في *الاستجابة*، بينما يسافر نحو 19 كيلوبايت من البيئة
  والقواعد والمهارات وفضاءات أسماء الأدوات في دور المستخدم.

## البنية

<div dir="ltr">

```
Orca-PromptVault/
├── README.md · CONTRIBUTING.md · LICENSE
├── docs/
│   ├── CAPTURES.md          كل التقاط + الأمر الذي يعيد إنتاجه
│   ├── UPSTREAM.md          ما جاء من CL4R1T4S، مسارًا بمسار
│   └── i18n/                هذا الملف بسبع لغات أخرى
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
└── Others/         مجلد لكل منتج
```

</div>

تُصنَّف الملفات تحت **من يرسل المُوجّه**، لا تحت من درّب النموذج. نموذج NVIDIA الذي يقوده OpenCode
يُصنَّف تحت OpenCode لأن تلك التعليمات كتبها OpenCode؛ ومساعد Meta الخاص يُصنَّف تحت Meta. ملف واحد
لكل التقاط، باسم `<harness>-<model>-<artifact>-<date>`، حتى يظل الملف — لو أُخرج وحده — قادرًا على
الإفصاح عن مصدره.

## المساهمة

مُوجّهات، مخططات أدوات، تعريفات مهارات، تعليمات أطر تشغيل — من أي منتج وبأي لغة. الالتقاط المصحوب
بأمر قابل للتكرار هو المعيار الذهبي؛ والتفريغ المؤرَّخ الأمين مرحّب به كذلك. في
[CONTRIBUTING.md](../../CONTRIBUTING.md) قواعد التسمية، وترويسة المصدر، والقائمة القصيرة لما لا
نقبله (أي شيء يحمل بيانات اعتماد أو بيانات شخصية، أو نصًا كتبته أنت ولا تستطيع بيان مصدره).

الأكثر طلبًا الآن: DeepSeek، وGemini CLI، وKimi CLI / وكيل K2، وجانب البرمجة في GLM، وCopilot،
وإصدار Devin الحالي، وأي شيء من منتج غير ناطق بالإنجليزية.

## المصدر والأخلاقيات وطلبات الحذف

هذه تعليمات يرسلها المزوّد إلى النموذج نيابةً عن المستخدم — مرئية لذلك المستخدم بحكم التكوين،
ومحفوظة هنا من أجل البحث والتشغيل البيني وفهم الجمهور لأنظمة صار يثق بها الملايين. لم يُنتزع أي شيء
هنا باقتحام: الالتقاطات كلها من وسيط على أجهزتنا، يقرأ حركتنا نحن، أثناء جلساتنا نحن.

لا يحتوي شيء هنا على بيانات اعتماد أو مفاتيح API أو بيانات شخصية أو معرّفات حسابات؛ كل التقاط
يُنظَّف قبل كتابته، وما لا يمكن تنظيفه لا يُنشر. تبقى المُوجّهات ملكًا لأصحابها. إن كان أحدها لك
وأردت إزالته، افتح issue وسيُحذف.

هذا الأرشيف لفهم الوكلاء، لا لتقويض عملهم في مجال الأمان. وتُرفض طلبات السحب التي غرضها حمولة
اختراق (jailbreak).

## شكر وتقدير

كل ما ليس التقاطًا من OrcaReplay — أي 75 من أصل 106 مادة، وأربعة أخماس البايتات — موروث من
[CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S) لـ **@elder_plinius**، وعمله هو أول من أثبت
أن هذه الوثائق تستحق الحفظ أصلًا. يحمل هذا المستودع ذلك التاريخ التزامًا بعد آخر، ويُبقي المجموعة
تحت رخصة AGPL-3.0، ويضيف إليها بدل أن يحل محلها. وكل ملف موروث مردود إلى مساره الأصلي في
[docs/UPSTREAM.md](../UPSTREAM.md).

أما النصف *المُلتقَط* فيُنتجه [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay)، الذي
يسجّل أي وكيل برمجي ويعيد تشغيله بايتًا ببايت دون استدعاء أي نموذج.

## الرخصة

[AGPL-3.0](../../LICENSE) لهذا المستودع. المُوجّهات المحفوظة من عمل أصحابها، وهي مجموعة هنا في إطار
الاستخدام العادل، لأغراض البحث والشفافية.

</div>
