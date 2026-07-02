# 视频化分层输出规则

## 适用场景

当用户要求视频化、剪辑、动效、透明 PNG、分层导出、口播稿对齐、manifest 或 `unit_id` 对齐时，使用本规则。不要改变白煮蛋画风、IP 锁定项、Shot List 质量要求和生成风格。

## unit_id 规则

- `unit_id` 是口播稿语义单元的唯一主键。
- 当上游已经提供 `unit_id` 时，只能消费、透传和引用，不允许重新生成另一套编号。
- 不允许用 `图 N`、段落序号、图片序号替代 `unit_id`。
- 每个视觉模块和视觉元素都必须能追溯到一个或多个 `unit_id`。
- 如果没有上游 `unit_id`，继续按原有文章配图流程生成 Shot List，但必须标记 `unit_id_source: missing`。
- 没有上游 `unit_id` 时，不要伪造 `u001/u002`，也不要声称已对齐口播稿。

## 语义模块

每张图可以拆成 2-5 个语义模块。模块用于视频后期理解“什么东西一起动”，不是为了把画面拆碎。

字段：

- `module_id`：图内模块 ID，例如 `m01`, `m02`；在 manifest 中建议组合成 `shot01_m01`。
- `source_unit_ids`：模块对应的上游 `unit_id` 列表；没有上游时为空数组。
- `module_role`：模块职责，例如 `main_actor`, `conflict_object`, `flow_path`, `evidence`, `annotation`, `background_context`。
- `elements`：模块内元素，例如 `apron_egg_worker`, `cracked_wall`, `orange_arrow`, `red_warning_label`。

模块粒度：

- 白煮蛋主体、围裙、鞋子、黑点眼和细手细脚通常作为同一 `main_actor` 模块整体保留。
- 围裙不能被拆成单独漂浮层，除非是局部修复或极轻微强调动画。
- 箭头、批注词、警告符号、掉落碎壳、蒸汽、蛋黄渗出、外部道具可以单独分层。
- 一个模块应表达一个语义动作；不要把无关元素塞进同一模块。

## 分层建议

分层用于动效，不用于破坏插图整体性。

推荐独立透明 PNG 图层：

- `main_actor`：围裙白煮蛋主体，含围裙、鞋子、手脚、眼睛和表情。
- `props`：关键道具，如机器、门、桥、漏斗、画框、饭盒、按钮。
- `flow`：橙色路径、箭头、连接线。
- `warnings`：红色问题点、裂纹、警告牌。
- `annotations`：短中文批注词。
- `atmosphere`：蒸汽、少量碎壳、蛋花、轻微震动线。

必须整体保留：

- 白煮蛋身体 + 围裙 + 鞋子 + 手脚 + 眼睛。
- 同一动作中的手和正在拿的核心物件，除非后期需要做拿起/放下动作。
- 一个不可拆的隐喻装置，例如“筛选器白煮蛋”“承接盘白煮蛋”。

不要分层：

- 不要把每条线都拆成图层。
- 不要把围裙、鞋、眼睛拆到失去 IP 识别。
- 不要为了动效把一张图拆成 PPT 零件。

## 文件命名

有上游 `unit_id`：

```text
assets/<slug>-illustrations/
  manifest.json
  01-<topic>.png
  layers/
    u003_m01_main-actor.png
    u003_m02_machine.png
    u003_m03_orange-flow.png
    u003_m04_annotations.png
```

没有上游 `unit_id`：

```text
assets/<slug>-illustrations/
  manifest.json
  01-<topic>.png
  layers/
    missing_shot01_m01_main-actor.png
    missing_shot01_m02_props.png
```

## manifest.json 最小结构

```json
{
  "manifest_version": "1.0",
  "skill": "baizhu-egg-illustrations",
  "unit_id_source": "provided",
  "canvas": {
    "aspect_ratio": "16:9",
    "background": "transparent_or_white",
    "style": "white egg hand-drawn article illustration"
  },
  "shots": [
    {
      "shot_id": "shot01",
      "title": "短主题",
      "covered_unit_ids": ["u003", "u004"],
      "full_image": "01-topic.png",
      "modules": [
        {
          "module_id": "shot01_m01",
          "source_unit_ids": ["u003"],
          "module_role": "main_actor",
          "elements": ["apron_egg_worker", "front_dark_apron", "worker_shoes"],
          "layer_file": "layers/u003_m01_main-actor.png",
          "must_keep_together": true,
          "motion_hint": "subtle_enter_from_bottom_or_hold"
        }
      ]
    }
  ]
}
```

`unit_id_source` 只能使用：

- `"provided"`：上游提供了 `unit_id`，已透传。
- `"missing"`：没有上游 `unit_id`，未伪造。

## manifest 必填字段

每个 shot 必填：

- `shot_id`
- `title`
- `covered_unit_ids`
- `full_image`
- `modules`

每个 module 必填：

- `module_id`
- `source_unit_ids`
- `module_role`
- `elements`
- `layer_file`
- `must_keep_together`
- `motion_hint`

## QA

输出前检查：

- 上游有 `unit_id` 时，manifest 中的 `covered_unit_ids` 和 `source_unit_ids` 必须来自上游原值。
- 没有上游 `unit_id` 时，所有 `covered_unit_ids` 写空数组或 `missing`，并标记 `unit_id_source: "missing"`。
- 每个图层都能追溯到一个模块。
- 每个模块都能追溯到一个或多个 `unit_id`，或明确是 missing。
- 白煮蛋 IP 锁定项没有被分层破坏。
- 图层命名和 manifest 引用一致。
