# DeAI

默认 MARK 模式把 AI 初稿改成带你自己声音的文字。删套话，调节奏，标出该由你亲自写的位置。只标，不替你写。

The default MARK mode removes filler, restores rhythm and marks where your own voice belongs. Marks only, never writes for you.

## 默认用法 / Default use

1. 打开 `prompt.md`，整篇复制到任何 AI。
2. 粘贴你的初稿，前面加 `DeAI:`。
3. 看输出里的 `[💬]` 和 `[📝]` 标记，自己填。

Open `prompt.md`, paste it into any AI, then send your draft prefixed with `DeAI:`. Fill the `[💬]` and `[📝]` markers yourself.

## 个人写作 / Personal PROFILE mode

PROFILE 扩展支持显式请求：依据有来源的作者画像改写文字，或按你提供的事实与观点写草稿。画像可以保留粗口、讽刺和攻击性，并说明何时使用；它不通过固定的粗口数量、问句数量或段落模板制造相似感。

加载 `references/profile-mode-v1.0-2026-10-03.ilang.md`，同时提供你选定的作者画像和当前素材。通过技能使用时，`SKILL.md` 会先选择模式。没有显式 PROFILE 请求，继续使用原 MARK。直接粘贴默认 `prompt.md` 不会自动增加 PROFILE 能力。

已附 SUN 中文候选画像：`profiles/sun-v1.0-2026-10-03.ilang.md`。最方便的用法是完整复制 `sun-writing-v1.0-2026-10-03.ilang.md` 给 AI，再提供本次素材与写作要求；该文件已经内嵌执行规则和画像。通过技能使用时可明确选定 PROFILE 与 SUN。也可以提供其他作者画像。

SUN 画像来自本人历史消息、本人修订稿与本次明确偏好，目前仍待本人样文校准。它不证明跨作者唯一性。画像缺失时会如实说明；历史对话里的经历、数字和具体事实不会自动搬进新稿。

PROFILE is a candidate extension for explicit requests to rewrite or draft with a supplied, evidence-based author profile. Load its separate I-Lang prompt and the selected profile. It preserves supported personal expression without fixed slang or question quotas. Without an explicit PROFILE request, the original MARK workflow remains the default.

原始对话应保存在本地私有分析目录；此仓库的集成材料只需包含派生画像。画像仍待本人样文校准；静态文件检查不能证明写作效果已经得到本人认可。

## 文件 / Files

| 文件 | 是什么 |
|---|---|
| `prompt.md` | MARK 默认产品本体，iLang v5.0 写的 |
| `*.iml.md` | 同名 iLang 文件的 IML 0.5 机器层编译版，用参考编解码器编译，给程序读 |
| `SKILL.md` | 模式路由与默认技能说明（中英日韩） |
| `references/profile-mode-v1.0-2026-10-03.ilang.md` | PROFILE 独立执行规则；需要指定作者画像 |
| `profiles/sun-v1.0-2026-10-03.ilang.md` | SUN 中文候选画像；证据身份与适用边界随文件提供 |
| `sun-writing-v1.0-2026-10-03.ilang.md` | SUN 一体化写作提示词，内嵌 PROFILE 执行规则与画像，可直接复制使用 |

## 版本 / Version

1.3.0：MARK 1.2.1 加 PROFILE 1.0（候选，待本人样文校准）。变更记录看 git tag。

## License

MIT. © 2026 iLang Inc.

基于 iLang 协议编写 · Written in iLang · [ilang.ai](https://ilang.ai)
