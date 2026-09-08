# Seedance Final Translation and Direct-Copy Template

## Purpose

Translate approved production facts into Seedance 2.0/2.5 execution language.

Do not rewrite story, redesign characters, invent props, change world rules, alter locked dialogue or casually re-split content.

## Core rule

Write what the model may guess wrong and whose error would damage result.

Do not repeat natural details that can vary harmlessly.

`complete ≠ verbose`  
`precise ≠ numeric overload`  
`cinematic ≠ adjective pile`

## Isolated group

Every group must stand alone.

Restate assets, time/place, relevant space, initial positions/orientation, prop states, environment/VFX, core event and shots.

Do not rely on previous prompt text.

## Duration

Every group ≤28s. No minimum. Content/capacity decides.

## Default group structure

1. `【本组剧情任务】`
2. `【本组总资产映射】`
3. `【镜内生成物】` if needed
4. `【本组视觉风格锁定】`
5. `【本组独立生成锁定】`
6. `【导演意图】`
7. `【本组镜头调度】`
8. shots
9. `【本组动作终点】`
10. `【本组禁止项】` only when needed

No dedicated first-frame/last-frame prose sections by default.

## Group task

One causal sentence:
who + trigger → action → feedback → result.

Avoid vague summaries.

## Asset mapping

Use full registered names:

```text
【本组总资产映射】

场景：
@场景_...

人物：
@人物_...

道具：
@道具_...

生物／怪物：
@...
```

Omit empty categories.

Add `当前状态覆盖` only for physical differences from base asset.

Do not pretend an `@` tag proves a visual reference is attached.

## In-shot generated elements

Use for temporary rain, ordinary smoke/dust, sparks, paper debris, mist.

Do not use to bypass stable creature/core prop assets.

## Style lock

Keep concise:

```text
【本组视觉风格锁定】
画幅：
视觉类型：
色彩：
材质：
摄影质感：
光影：
表演：
VFX：
声音：
```

Only include fields that matter.

## Independent generation lock

Recommended:

```text
【本组独立生成锁定】
时间：
地点：

空间结构：
...

人物起始位置：
...

关键道具状态：
...

环境状态：
...

当前异常状态：
...

空间轴线：
...（仅必要时）
```

Do not write “承接上一组，仍在原位”.

## Director intent

One useful sentence.

## Group shot flow

One concise flow:
`建立空间 → Trigger → reaction/action → result/reveal`

## Shot title

```text
### 镜头1｜00:00—00:02.5｜2.5秒｜镜头功能
```

Local timeline starts at 00:00.

No overlapping/gapped shots.

## Shot fields

Default:

```text
【机位／景别／焦段／运镜】
【构图与空间】
【触发点】
【动作与表演】
【特效／物理反馈】
【对白／独白】
【声音】
【动作终点】
```

Each shot is complete. Never use “同上一镜” as key information.

## Camera

State useful:
- relative position
- height/angle
- shot scale
- focal length/logical lens
- movement
- movement start/end if moving

Example:
`35mm中景；摄影机在柜台西南侧、店长眼平高度，固定。`

Avoid contradictions such as “locked-off tracking shot”.

## Composition/space

State screen placement for this shot, foreground/mid/background, character distance, eyelines, movement direction and key spatial references.

Screen side is shot-specific, not world geography.

## Trigger

State the visible/audible/perceivable cause that starts this shot's action.

Avoid abstract reasons.

## Action/performance

Use:
stimulus → first reaction → action path → contact if needed → feedback → result.

Keep performance details visible at current shot scale.

## VFX

Simple effects may be one sentence.

Complex effects need:
source → path → interaction/force → environment/light response → end state.

Use `无。` when structurally useful; do not invent VFX.

## Dialogue

```text
【对白／独白】
人物（语气＋语速＋必要语调）：“锁定原台词。”
```

No dialogue: `无。`

Never optimize locked wording.

## Sound

Use only present items:

```text
【声音】
环境音：
动作音：
道具音：
呼吸：
画外声：
VFX声：
```

Project-level `无BGM` is stated once per group, not every shot.

## Action endpoint

Every shot ends with one physical state sufficient for next shot:
character final position/orientation/pose, core prop and relevant environment/VFX.

This is not a freeze-frame instruction.

## Group endpoint

`【本组动作终点】` summarizes only hard state the next group must inherit.

Do not copy final-shot prose.

## Prohibitions

Use group-specific prohibitions only for real high-risk failures or explicit user locks.

Positive correct state is usually stronger than a giant negative list.

## Compression

Remove:
- repeated face descriptions when asset bound
- full room decoration repeated per shot
- repeated global style
- director rationale
- long negative lists
- filler adjectives
- internal QC/results

Keep:
- hard state
- spatial facts
- trigger
- action path/result
- core prop
- dialogue
- VFX source/result
- camera geometry needed for disambiguation

## Direct-copy template

```text
# 第XX组｜剧情节点名称｜XX秒

【本组剧情任务】
谁因为哪个触发 → 做什么 → 遭遇什么反馈 → 本组最终结果。

【本组总资产映射】
场景：
@完整场景资产名

人物：
@完整人物资产名

道具：
@完整道具资产名

生物／怪物：
@完整资产名

当前状态覆盖：
只写与基础资产不同且本组必须继承的物理状态。

【镜内生成物】
仅存在时写。

【本组视觉风格锁定】
画幅：
视觉类型：
色彩：
材质：
摄影质感：
光影：
表演：
VFX：
声音：

【本组独立生成锁定】
时间：
地点：

空间结构：
人物起始位置：
关键道具状态：
环境状态：
当前异常状态：
空间轴线：（仅必要时）

【导演意图】
一句话。

【本组镜头调度】
建立空间 → Trigger → 人物反应/动作 → 结果/揭示。

---

### 镜头1｜00:00—00:XX｜X秒｜镜头功能

【机位／景别／焦段／运镜】
...

【构图与空间】
...

【触发点】
...

【动作与表演】
...

【特效／物理反馈】
无；或具体事件。

【对白／独白】
无；或人物（语气＋语速＋必要语调）：“原台词。”

【声音】
...

【动作终点】
...

---

### 镜头2｜...
每镜完整描述。

【本组动作终点】
只总结下一组必须继承的Hard State。

【本组禁止项】
仅高风险/用户明确要求时写。
```

## Isolated group test

Pretend Seedance sees only this group.

Can it identify who, where, current state, what happens, how camera sees it, who speaks and what result remains?

If not, add only missing information.

## Ambiguity test

Reduce ambiguous pronouns in multi-character scenes.

Disambiguate multiple doors/props by stable names/anchors.

Movement/attack/collapse/VFX direction must be explicit when continuity depends on it.

## Do not expose process

Never put Story Lock reports, Shot Plan JSON, CAM IDs, validator logs, hash/run IDs, chain-of-thought or internal scoring inside Seedance prompt.
