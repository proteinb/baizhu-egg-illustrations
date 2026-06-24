# 生图提示词模板

每张图单独生成。根据正文内容替换变量，不要把多张图拼在一起。

```text
Generate one standalone 16:9 horizontal Chinese article illustration.

Visual DNA:
Pure white background. Minimalist black hand-drawn line art. Slightly wobbly pen lines. Lots of empty white space. Sparse red/orange/blue handwritten Chinese annotations. Clean absurd product-sketch feeling. No gradients, no shadows, no paper texture, no complex background, no commercial vector style, no PPT infographic look, no cute mascot poster, no children's illustration, no realistic UI.

Recurring IP character required:
白煮蛋, an empty white boiled-egg worker character drawn with a black hand-drawn outline, tiny thin arms and legs, black dot eyes, restrained blank expression, no glasses. It must have a front-center simple dark apron that is clearly visible and large enough to read as an apron, not just a belt line. The apron must include at least one visible detail: a small front knot, tied straps, thin vertical stripes, or a tiny pocket. Add small plain worker shoes on the feet. The apron and shoes are the stable visual hooks and must remain visible even if the egg changes form. The default body is a clean boiled egg shape. Use egg-state cues to express emotion: shell cracks, tiny shell chips, soft egg white edges, a small clean yolk leak, egg-drop fragments, or gentle steam. Keep these cues clean, sparse, and tied to the action, not decorative or gross.

Theme:
{正文配图主题}

Structure type:
{结构类型：Workflow / 系统局部 / 前后对比 / 角色状态 / 概念隐喻 / 方法分层 / 地图路线 / 小漫画分镜}

Core idea:
{这张图要表达的核心意思}

Composition:
{具体画面：白煮蛋在哪里、正在做什么、主要物件是什么、信息如何流动；同时写明围裙位于主体正面且没有被遮挡}

Egg form:
Default to A: complete apron boiled egg. Use B fried egg / C scrambled egg / D steamed egg / E egg-drop form only when the article meaning is strongly tied to spreading, fragmentation, warm stability, or diffusion. Do not switch forms just for variety. Selected form: {A 完整围裙白煮蛋 / B 荷包蛋 / C 炒蛋 / D 蒸鸡蛋 / E 蛋花}. Shell cracks or soft-boiled yolk leak are emotion details, not the default main form.

Egg-state emotion cues:
{front-center dark apron clearly visible, with knot/straps/stripes/pocket; small worker shoes visible} + {蛋壳裂纹 / 碎壳 / 蛋黄渗出 / 蛋白摊开 / 炒蛋碎片 / 蒸汽 / 蛋花扩散} must connect to the action and emotion.

Suggested elements:
{元素1} / {元素2} / {元素3} / {元素4}

Chinese handwritten labels:
{标注词1} / {标注词2} / {标注词3} / {标注词4} / {可选标注词5}

Color use:
Black for main line art, labels, and the egg outline. Orange for main flow/path/arrows. Red only for key warnings/problems/results. Blue only for secondary notes or feedback/system state. Use yolk yellow sparingly only when the egg state needs it.

Constraints:
One image explains only one core structure. Keep the main subject around 40%-60% of the canvas. Preserve at least 35% blank white space. Use at most 5-8 short handwritten Chinese labels. Do not write a title in the top-left corner. Do not write the structure type on the image. Do not make it a formal diagram, course slide, or dense explainer. Do not copy prior examples or reuse known case compositions unless explicitly requested; invent a fresh visual metaphor for this specific article. It should be clear but not instructional, interesting but not childish, strange but clean. No glasses. The apron must remain front-center, readable, and unobstructed; do not hide it behind yolk, egg white, labels, tools, hands, bowls, or props. Do not omit the small worker shoes.
```

## 图像编辑提示

去掉左上角标题：

```text
Edit the provided image. Remove only the handwritten title "{要删除的文字}" and its underline from the top-left corner. Fill that area with the same clean white background, matching the surrounding blank paper. Preserve everything else exactly: characters, labels, paths, line style, composition, aspect ratio, and image quality. Do not add any new text or objects.
```

增强 IP 识别：

```text
Regenerate this illustration with the same core meaning and simple layout, but make 白煮蛋 more central to the conceptual action. 白煮蛋 should be doing the strange work that explains the idea, not standing beside the diagram. Keep the front-center simple dark apron clearly visible, large enough to read as an apron, with a small knot/straps/vertical stripes/pocket detail; keep small worker shoes visible; preserve black dot eyes, thin limbs, and a restrained blank expression. Use egg-state cues such as shell cracks, yolk leak, soft egg white, egg-drop fragments, or steam only where they express the action. Keep it clean, sparse, hand-drawn, and not cute.
```
