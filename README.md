# baizhu-egg-illustrations

白煮蛋怪诞正文配图 skill，用于为中文文章、帖子、博客、Notion 文档、工作流文档、方法论和观点类内容生成清爽、怪诞、有留白的正文配图。

## 这次更新：A 是主角，B/C/D/E 不能乱用

这次更新解决一个很简单的问题：白煮蛋有很多形态，但不能每张图都换衣服。

可以把它想成一个班级：

- **A 是班长**：完整的围裙白煮蛋，平时都用它。
- **B 是摊开的荷包蛋**：只有文章在讲“摊开、扩张、外溢”时才用。
- **C 是炒蛋**：只有文章在讲“混乱、碎掉、重新组合”时才用。
- **D 是蒸鸡蛋**：只有文章在讲“温和、稳定、被托住、长期照护”时才用。
- **E 是蛋花**：只有文章在讲“扩散、渗透、很多小触点”时才用。

一句话：**默认画 A。除非文章真的需要 B/C/D/E 来说明意思，否则不要为了好看硬换形态。**

![白煮蛋 A/B/C/D/E 形态系统](assets/05-egg-form-system.png)

## 这次更新：图片要真的落盘，还要够小

这次更新把“能看到图”和“能交付图”分开处理。

以前的问题是：内置 AI 生图有时只在对话里显示预览，但本地没有稳定生成图片文件。这样不能算可靠交付。

现在规则改成：

- 需要可靠交付时，默认用本地脚本、SVG、PIL 或 canvas 生成确定性 PNG。
- 内置 AI 生图只作为方向预览；预览成功不代表文件已经保存。
- 图片必须真实存在于 workspace 路径里。
- 单张图片目标大小控制在 **100KB 以内**。
- 单张图片硬上限是 **1MB**；超过 1MB 不允许交付。
- 如果文件太大，优先压缩 PNG、减少细碎元素，或量化到 32-64 色。

一句话：**交付图片必须找得到、打得开、够小。**

## 这次更新：中文长文先做 Shot List

中文长文配图不再按段落平均画图，而是先提炼文章的认知锚点，再决定哪些地方值得画。

**中文长文先做 Shot List。除非文章本身是严格步骤教程，否则不要逐段画。每张图必须对应一个认知转折点或结构锚点。**

Shot List 固定模板：

```text
文章主题 -> 认知转折点 -> 关键动作 -> 画面构图 -> 批注词 -> 禁忌项
```

工具清单类文章默认使用“三图法”：

```text
入口选择图 -> 流程接力图 -> 结果复用图
```

## 测试配图

![饭盒废品重新定价样张](assets/01-lunchbox-repricing.png)

这组图来自白煮蛋正文配图测试，用来展示 skill 预期生成的构图、线稿、留白、中文批注和少量强调色。

![单位发放处写检查样张](assets/02-unit-distribution-check.png)

![准时上班路径样张](assets/03-punctual-work-route.png)

![铝超标压力挤出样张](assets/04-aluminum-pressure-test.png)

![白煮蛋形态系统样张](assets/05-egg-form-system.png)

## 用途

- 为中文长文设计正文配图策略和 shot list
- 生成 16:9 横版白煮蛋风格插图
- 将观点、流程、结构、状态或隐喻转成可读但不死板的手绘解释图
- 保持固定视觉 IP：围裙白煮蛋、小工作鞋、黑色手绘线稿、少量红橙蓝中文批注

## 技术规范

完整 IP 技术规范见 [docs/egg-ip-technical-spec.md](docs/egg-ip-technical-spec.md)。这份规范定义了围裙白煮蛋的默认主视觉、稳定识别点、蛋形态系统、情绪语言、构图规范和验收标准。

## 安装

把本仓库克隆或复制到 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/proteinb/baizhu-egg-illustrations.git ~/.codex/skills/baizhu-egg-illustrations
```

## 调用

在 Codex 里可以直接说：

```text
使用 baizhu-egg-illustrations，给这篇中文文章设计几张白煮蛋正文配图。
```

或显式调用：

```text
Use $baizhu-egg-illustrations to 为这篇中文文章设计并生成几张白煮蛋怪诞正文配图。
```

## 文件结构

- `SKILL.md`：主 skill 说明和工作流
- `agents/openai.yaml`：Codex/OpenAI agent 调用元信息
- `references/style-dna.md`：风格 DNA、颜色和禁忌
- `references/egg-ip.md`：白煮蛋 IP 设定
- `references/composition-patterns.md`：构图和隐喻模式
- `references/prompt-template.md`：生图提示词模板
- `references/qa-checklist.md`：生成后检查清单
- `docs/egg-ip-technical-spec.md`：更细的 IP 技术规格
- `assets/*.png`：白煮蛋正文配图测试样张

## 视觉原则

纯白背景、黑色手绘线稿、大量留白、少量中文手写批注。图像应服务文章的认知锚点，不做 PPT 化流程图，也不做商业插画或可爱装饰。

## 更新记录

- 2026-06-20：增加中文长文 Shot List 规则。中文长文先做 Shot List；除非文章是严格步骤教程，否则不要逐段画；每张图必须对应一个认知转折点或结构锚点；工具清单类文章默认使用三图法。
- 2026-06-19：增加可靠文件交付规则。默认使用本地脚本/SVG/PIL/canvas 生成确定性 PNG，不依赖内置 AI 生图自动落盘；新增单张 100KB 目标和 1MB 硬上限。
- 2026-06-17：明确 A 是默认主视觉，B/C/D/E 只在文章语义强相关时使用。
