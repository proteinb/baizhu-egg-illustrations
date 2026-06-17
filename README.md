# baizhu-egg-illustrations

白煮蛋怪诞正文配图 skill，用于为中文文章、帖子、博客、Notion 文档、工作流文档、方法论和观点类内容生成清爽、怪诞、有留白的正文配图。

## 用途

- 为中文长文设计正文配图策略和 shot list
- 生成 16:9 横版白煮蛋风格插图
- 将观点、流程、结构、状态或隐喻转成可读但不死板的手绘解释图
- 保持固定视觉 IP：围裙白煮蛋、小工作鞋、黑色手绘线稿、少量红橙蓝中文批注

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

## 视觉原则

纯白背景、黑色手绘线稿、大量留白、少量中文手写批注。图像应服务文章的认知锚点，不做 PPT 化流程图，也不做商业插画或可爱装饰。
