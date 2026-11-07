---
name: DeAI
version: 1.5.1
description: "DeAI: Edit AI drafts using the default MARK workflow: a floor that removes filler, adjusts rhythm and marks places for the author's own expressions, plus a weighted tone layer that estimates who will read the piece and sets register, case domain and quotation level to that reader. Dialect is the fingerprint, never profanity. Explicit PROFILE requests use a supplied evidence-based author profile to rewrite or draft text. MARK supports Chinese, English, Japanese and Korean; PROFILE uses only the languages supported by its supplied evidence."
author: ilang-ai
homepage: https://ilang.ai
tags:
  - writing
  - editing
  - authenticity
  - style
  - multilingual
  - content-quality
---

```ilang
::ILANG::v5.0
[TYPE:skill_router]
[ID:DEAI-MODE-ROUTER-20261106]
[BASE_VERSION:1.3.0]
[EXTENSION_VERSION:1.2]
[STATUS:calibrated_on_public_forum_corpus]

::RULE{route_before_loading}
  T:未显式选择个人 PROFILE 写作时 使用 MARK 默认模式 读取 prompt.md 按 DeAI: 前缀激活
  T:MARK 1.3.0 分两层 保底层每稿必跑 基调层按读者估计的置信加权 置信高全跑 置信中只标案例位置 置信低只跑保底
  T:两种模式的输出第一行都是读者估计 峰值 跨度 置信 用户一句话可改 改了就按改后的重做基调
  T:指纹是方言不是脏字 两种模式都不生成粗口 方言在 MARK 只标位置 在 PROFILE 只用画像有证据的词
  T:用户显式指定 mode=PROFILE 或明确要求使用已选定本人画像写作时 读取 references/profile-mode-v1.2-2026-11-06.ilang.md 与指定画像
  T:profile=SUN 映射到 profiles/sun-v1.1-2026-10-03.ilang.md 该画像为中文 已用本人2009年至2020年的公开论坛发言校准 画像文件是证据记录 1.2 的输出规则以执行规则为准
  T:PROFILE 和 MARK 为独立路径 不在 PROFILE 中叠加默认 prompt.md 的只标位置 固定问句数量或平台口吻
  T:PROFILE 必须有可用的作者画像与当前写作素材 缺失时明确说明 不把通用去 AI 味处理称为个人风格
  T:prompt.iml.md 只编译了 MARK 的 prompt.md 扩展与画像各有同名的 .iml.md
  T:下方分层说明 平台指南与各语言使用说明描述 MARK 默认模式 不覆盖 PROFILE 路由
  T:加载本技能不授权上传语料 读取私人日志或自动执行其他任务
```

# DeAI: Make AI Drafts Sound Like You

# DeAI：让AI初稿听起来像你自己写的

---

## English

### The Problem

AI drafts are useful but sound generic. They overuse filler phrases ("Furthermore", "值得注意的是"), write in monotonous rhythm, avoid colloquial language, and never ask rhetorical questions. The result reads like a committee wrote it, not a person.

DeAI is a writing quality tool that helps you edit AI drafts into text that carries your authentic voice.

### The floor and the tone layer

```text
FLOOR (runs on every draft, guarantees a passable text):
  CLEAN:       Remove overused filler phrases. Built-in lists for Chinese (21), English (16), Japanese (10), Korean (8).
  RESTRUCTURE: Vary sentence rhythm. Lead with opinions. Replace vague adjectives with specific numbers. Add rhetorical questions for natural tone.
  MARK:        Flag positions where your personal voice should go: [💬] your own words, [🗣] a word from your own dialect. YOU add the expressions; the tool only marks where.

TONE LAYER (weighted by the confidence of the reader estimate):
  READER ESTIMATE: who will most likely read this piece: peak register (STREET / PLAIN / LEARNED), spread, confidence. Printed as the first line, yours to correct.
  TONE:            one base register per piece set at the peak; one touch of the neighbouring band when the spread is wide.
  CASE:            one claim, one case from the reader's own world, mapped one to one, closed on the image, never explained afterwards. Written at high confidence inside a [🎯] marker you can swap; only positioned at mid confidence; skipped at low confidence.
  QUOTATION:       in the LEARNED register, verbatim with author and work, or dropped.
```

Dialect is the fingerprint. Profanity never is: the tool never proposes a swear word in any register.

### Default MARK scope

The default MARK prompt edits supplied text and adds review markers. The only text it authors is a [🎯] case, always wrapped so you can swap it. It does not access files, make network requests, or run automatically. Each use requires you to paste text and explicitly request editing. Explicit PROFILE requests follow the independent extension above, which can rewrite or draft from supplied material and a supplied author profile.

**Responsible use:** This tool improves writing style and authenticity. It is your responsibility to comply with applicable disclosure requirements, academic integrity policies, and platform rules regarding AI-assisted content. Do not use DeAI to misrepresent authorship where disclosure is required.

### Supported Languages

| Language | Filler phrases removed | Voice markers | Dialect marker |
|----------|----------------------|---------------|----------------|
| Chinese 中文 | 21 phrases | [💬] 只标位置，词你自己填 | [🗣 方言可入] |
| English | 16 phrases | [💬] position only, your own words | [🗣 regional word fits] |
| Japanese 日本語 | 10 phrases | [💬] 位置のみ、言葉は自分で | [🗣 方言可] |
| Korean 한국어 | 8 phrases | [💬] 위치만 표시, 표현은 직접 | [🗣 사투리 가능] |

### Platform Style Guides

Optionally specify a target platform for style-appropriate editing. DeAI will explain what changes it recommends and wait for your confirmation before applying platform-specific rules.

| Platform | Style guidance |
|----------|---------------|
| WeChat 微信 | Blogger first-person, bold section breaks, rhetorical endings |
| X/Twitter | Observer tone, concise, verdict-style endings |
| Hacker News | Developer essay, understated, factual |
| Reddit | Conversational, casual, short endings |

### How to Use

1. Open `prompt.md`, copy the full text into any AI
2. Paste your AI-drafted text with the prefix `DeAI:`, for example: "DeAI: [your text here]"
3. Optionally add platform: "DeAI: [your text] target: WeChat"
4. Read the first line, the reader estimate. If it is wrong, correct it in one sentence and the tone is redone
5. Review the output. [💬] and [🗣] markers show where to add your own words; each [🎯] case can be kept or swapped
6. Replace markers with your expressions, done

---

## 中文

### 痛点

AI写的初稿能用但太"模板化"。堆砌套话（"值得注意的是"、"综上所述"）、节奏单调、没有口语、没有反问。读起来像机器写的，不像人写的。

DeAI是一个写作编辑工具，帮你把AI初稿改成带有你个人风格的文字。

### 保底层与基调层

```text
保底层（每稿必跑，保证至少及格）：
  清理：删掉过度使用的套话。内置中文21个、英文16个、日文10个、韩文8个。
  重组：调节句子节奏、观点前置、数字替换形容词、加反问增加自然感。
  标注：标记应该加入你个人表达的位置。[💬] 你自己的话，[🗣] 你自己的方言。你自己加，工具只标位置。

基调层（按读者估计的置信加权）：
  读者估计：这篇大概率谁读。峰值档（市井 / 大众 / 高知）、跨度、置信。写在输出第一行，你一句话可改。
  基调：一篇一个基调，定在峰值；跨度宽就加一个相邻档的触点。
  案例：一个论点一个案例，从读者自己的世界里取，一比一演绎，画面收口，事后不解释。置信高时写出来放在 [🎯] 标记里由你留或换；置信中只标位置；置信低不做。
  引文：高知档引诗词典故，原文逐字加作者篇名，不确定就不引。
```

指纹是方言，不是脏字。工具在任何档位都不会给你一个粗口。

### 默认 MARK 模式的范围

默认 MARK 模式编辑已有文字并添加标记，唯一会自己写的是 [🎯] 案例，而且总是带标记让你随时换掉。不访问文件、不联网、不自动运行。每次使用都需要你主动粘贴文字并请求编辑。显式 PROFILE 请求走上面的独立扩展，根据当前素材和指定作者画像改写或写草稿。

**负责任使用：** 本工具用于提升写作风格和真实感。遵守适用的披露要求、学术诚信政策和平台关于AI辅助内容的规则是你的责任。

### 使用方法

1. 打开 `prompt.md`，复制全文到任何AI
2. 粘贴AI初稿，前面加 `DeAI:` 前缀，例如："DeAI: [粘贴文字]"
3. 可选在末尾加："目标：微信"
4. 先看第一行的读者估计，不对就一句话改，基调会重做
5. 查看输出，[💬] 和 [🗣] 标记了应该加你自己表达的位置，[🎯] 案例留或换
6. 替换标记，完成

---

## 日本語

AIの下書きを自然な文章に編集するツールです。`prompt.md`をAIに貼り付け、テキストの先頭に「DeAI:」と入力してください。「DeAI:」プレフィックスのみに反応します。

---

## 한국어

AI 초안을 자연스러운 글로 편집하는 도구입니다. `prompt.md`를 AI에 붙여넣고 텍스트 앞에 'DeAI:'를 입력하세요. 'DeAI:' 접두사에만 반응합니다.

---

## Ecosystem / 生态

| Resource | Link |
|----------|------|
| iLang Protocol | [ilang.ai](https://ilang.ai) |
| AutoCode | [ilang-ai/autocode](https://github.com/ilang-ai/autocode) |
| OpenClaw Skills | [ilang-ai/ilang-openclaw](https://github.com/ilang-ai/ilang-openclaw) |

## License

MIT

© 2026 iLang Inc., Canada.
