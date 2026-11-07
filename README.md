# DeAI

[![DOI](https://zenodo.org/badge/1403191717.svg)](https://zenodo.org/badge/latestdoi/1403191717)

默认 MARK 模式把 AI 初稿改成带你自己声音的文字。保底层删套话、调节奏、标出该由你亲自写的位置，只标，不替你写。基调层先算这篇大概率谁读，再把整篇的基调、案例和引文定到那个读者身上：读者在市井，就用最直白的话和人人见过的场面；读者在高知，就引诗词典故。指纹是方言，不是脏字。

The default MARK mode has a floor and a tone layer. The floor removes filler, restores rhythm and marks where your own voice belongs; it marks only, never writes for you. The tone layer estimates who will most likely read the piece and sets the register, the case domain and the quotation level to that reader. Dialect is the fingerprint, never profanity.

## 默认用法 / Default use

1. 打开 `prompt.md`，整篇复制到任何 AI。
2. 粘贴你的初稿，前面加 `DeAI:`。
3. 看输出第一行的读者估计，不对就一句话改。
4. 看 `[💬]` `[🗣]` `[📝]` 标记，自己填；`[🎯]` 案例留或换。

Open `prompt.md`, paste it into any AI, then send your draft prefixed with `DeAI:`. Check the reader estimate on the first line and correct it in one sentence if needed. Fill the `[💬]` `[🗣]` `[📝]` markers yourself; keep or swap each `[🎯]` case.

## 个人写作 / Personal PROFILE mode

PROFILE 扩展支持显式请求：依据有来源的作者画像改写文字，或按你提供的事实与观点写草稿。画像可以保留讽刺、攻击性和方言，并说明何时使用；指纹是方言不是脏字，它不生成粗口，原稿里已有的粗口留还是去由你当次决定；它不通过固定的方言数量、问句数量或段落模板制造相似感。PROFILE 也先出读者估计，读者估计优先于画像里的体裁默认。

加载 `references/profile-mode-v1.2-2026-11-06.ilang.md`，同时提供你选定的作者画像和当前素材。通过技能使用时，`SKILL.md` 会先选择模式。没有显式 PROFILE 请求，继续使用原 MARK。直接粘贴默认 `prompt.md` 不会自动增加 PROFILE 能力。

已附 SUN 中文画像 1.1：`profiles/sun-v1.1-2026-10-03.ilang.md`。最方便的用法是完整复制 `sun-writing-v1.2-2026-11-06.ilang.md` 给 AI，再提供本次素材与写作要求；该文件已经内嵌执行规则 1.2 和画像 1.1。画像文件是证据记录，1.2 起里面的粗口模块只作证据，输出规则以执行规则为准。通过技能使用时可明确选定 PROFILE 与 SUN。也可以提供其他作者画像。

SUN 画像 1.1 用本人 2009 至 2020 年在赚客论坛的全部公开发言校准（去掉转载后约 48 万字原创文字），并保留本人历史消息与本人修订稿的证据。它不证明跨作者唯一性。画像缺失时会如实说明；历史对话里的经历、数字和具体事实不会自动搬进新稿。

PROFILE is an extension for explicit requests to rewrite or draft with a supplied, evidence-based author profile; the bundled SUN profile 1.1 is calibrated on the owner's public forum posts from 2009 to 2020. Load its separate I-Lang prompt and the selected profile. It preserves supported personal expression, dialect included, without fixed dialect or question quotas, and it never generates profanity. It prints a reader estimate first, and that estimate outranks the profile's genre defaults. Without an explicit PROFILE request, the original MARK workflow remains the default.

原始对话和论坛语料分析保存在本地私有分析目录；此仓库的集成材料只需包含派生画像。静态文件检查不能证明写作效果已经得到本人认可，合格以本人认可为准。

## 文件 / Files

| 文件 | 是什么 |
|---|---|
| `prompt.md` | MARK 默认产品本体，iLang v5.0 写的 |
| `*.iml.md` | 同名 iLang 文件的 IML 0.5 机器层编译版，用参考编解码器编译，给程序读 |
| `SKILL.md` | 模式路由与默认技能说明（中英日韩） |
| `references/profile-mode-v1.2-2026-11-06.ilang.md` | PROFILE 独立执行规则 1.2；需要指定作者画像 |
| `profiles/sun-v1.1-2026-10-03.ilang.md` | SUN 中文画像 1.1；证据编号、体裁分档与适用边界随文件提供；证据记录，不是输出规则 |
| `sun-writing-v1.2-2026-11-06.ilang.md` | SUN 一体化写作提示词，内嵌 PROFILE 执行规则 1.2 与画像 1.1，可直接复制使用 |

## 版本 / Version

1.5.1：加 CITATION.cff、.zenodo.json 与自动发版工作流，Zenodo 存档发 DOI；正文与 1.5.0 相同。

1.5.0：MARK 1.3.0（保底层不变，加读者估计、按置信加权的基调层、方言指纹、案例算法、引文逐字）加 PROFILE 1.2（读者估计优先于体裁默认、脏字不作指纹、方言只用有证据的词、引文逐字）。变更记录看 git tag。

## License

MIT. © 2026 iLang Inc.

基于 iLang 协议编写 · Written in iLang · [ilang.ai](https://ilang.ai)
