---
name: seedance-production-master
description: >
  面向 Seedance 2.0 / 2.5 AI影视生产的导演执行与视频提示词Skill。用户明确要求
  Seedance、AI视频生成、小说/剧本转可执行导演分镜、可视化剧本转视频提示词、
  逐组生成、资产映射、镜头连续性、Seedance分组提示词、生成结果诊断返修、
  减少生成歧义或降低重复抽卡时使用。可处理真人短剧、电影、电视剧、漫剧、
  动画及其他影视视觉风格。重点负责从已给定故事内容到AI视频执行层的完整转译；
  普通故事/剧本创作且没有Seedance或AI视频生产目标时，不主动替代其他编剧Skill。
---

# Seedance Production Master

把故事内容转成**可独立复制给 Seedance 执行的导演级生成组**。先保证事实、人物、空间、动作和连续性正确，再做摄影、美术和VFX。目标是降低可设计避免的随机失败，不承诺零抽卡或100%一次成功。

## 最高优先级

1. 用户明确锁定与项目资产锁。
2. 当前批准版本与源文本事实。
3. 剧情因果、人物逻辑、信息权限。
4. 世界空间、动作、道具与连续性。
5. 资产身份与状态稳定。
6. 对白、VFX、摄影、表演、声音。
7. 风格与画面美感。

世界空间不等于画面左右；切反打后屏幕左右可变，但真实位置、视线、轴线与运动方向必须成立。

## 与其他编剧Skill的边界

- Skill 名固定为 `seedance-production-master`，不要覆盖、修改或依赖 `$screenwriting-master`。
- 普通故事/剧本创作、且用户没有 Seedance/AI视频生产意图时，不主动抢占其他编剧Skill。
- 用户明确调用本Skill、或明确要求从创意/小说一路做到Seedance时，本Skill可完成必要的故事开发与剧本医生工作。
- 已批准的剧本、世界观、资产或分镜不得无原因重做。

## 任务入口

先识别输入成熟度与任务模式，再从最低必要阶段开始：

- 概念/小说：必要时先锁故事事实，再进入可视化与生产。
- 完整剧本：不要重写剧本，除非用户授权修改。
- 可视化剧本：优先从资产、分组和导演层继续。
- 已有分镜：优先做执行性与连续性检查，再翻译为Seedance。
- 已有Seedance提示词：进入诊断/局部返修。
- 已生成视频：以实际视频结果诊断根因，再最小修改对应层。

详细路由读 `references/01-core-routing.md`。

## 生产总链

`输入识别 → 用户锁提取 → 故事事实 → 可视化事实 → 资产注册 → 全片组分配 → Shot Plan → 动作/表演/声音 → VFX → 连续性 → Seedance翻译 → Final QC`

复杂完整项目在写第1组前先内部完成全片生成组分配，不能边写边临时决定后续内容。

## Seedance生成组硬规则

- 每组是新的独立生成任务；不得依赖模型记住前一组文字。
- 分组由剧情、台词、场景、动作、信息、情绪、VFX和执行负荷决定。
- **单组硬上限 28 秒；28 秒是上限，不是目标。**
- 允许6秒、11秒、17秒、24秒、27秒等自然时长。
- 低于28秒仍可能因人物、动作、VFX或摄影过载而拆组。
- 能合并的碎组应合并；不能为了固定时长切断完整动作或对白。
- 每组组内时间轴从 `00:00` 开始，镜头无重叠、无空档。
- 每组只有一个最终 `GROUP_END_STATE`；中间镜只产生各自动作终点。
- 默认不设置独立“首帧/尾帧”文本栏目。用户实际使用连续参考图时，可以绑定参考附件，但文字仍需重述当前可见物理事实。

分组细则读 `references/04-grouping.md`。

## 资产与STYLE

- `STYLE_LOCK`只控制视觉表达，不改变故事、人物、关系、动作因果或世界规则。
- `PROJECT_ASSET_LOCK`高于任何通用资产模板。
- 真人、国漫、日漫、3D共享同一导演逻辑，只改变视觉表达。
- `@资产名`只是语义标签；必须区分“文字注册资产”和“已绑定视觉参考”。
- 情绪不是资产变体。物理状态优先用 `BASE_ASSET + STATE_OVERLAY`，只有显著长期差异才建独立变体。

详见 `references/03-assets.md`。

## 导演执行

内部必须先做 Shot Plan，再输出最终提示词。Shot Plan至少决定：视点、摄影机侧、相对位置、高度、景别、焦段逻辑、构图、轴线、视线、运动方向、运镜、动作、切镜理由与镜头终点。

最终提示词允许明确有执行价值的机位，例如“摄影机在柜台西南侧、人物眼平高度”。不要输出无意义的小数坐标、内部CAM ID或审计日志。

详见 `references/05-directing.md`。

## 动作与表演

关键动作检查：
`Trigger → Perception → Reaction → Action → Interaction(如有) → Feedback → Result`

- 刺激先发生，人物才能反应。
- 不机械规定眨眼、呼吸、手指和微肌肉。
- 一镜只保留真正可见且有戏剧意义的表演信号。
- 多人场景明确谁先动、谁主行动、谁次反应。
- 锁定对白逐字保留；长对白通过镜头覆盖、时长或分组处理，不偷改文字。
- 每镜都必须内部判断声音来源与连续性；项目 `AUDIO_LOCK` 高于通用习惯。

详见 `references/06-performance-audio.md`。

## VFX

超自然可以违反现实物理，但不能违反项目世界规则、自身因果与前后状态。复杂事件按：
`Trigger → Source → Propagation → Interaction → Feedback → Result → Residue`

非发光烟雾不得自动产生霓虹面光；爆炸、崩塌、液体、锁链、魂体、空间异常等必须留下与强度相称的环境或状态结果。

详见 `references/07-vfx.md`。

## 连续性

维护内部 `CONTINUITY_LEDGER`。对连续时空，必须满足：
`STATE OUT(N) → STATE IN(N+1)`

重点硬状态：人物位置/姿态/朝向、道具持有与开合、服装、伤势、污染、门窗、破坏、VFX、时间和信息状态。

区分：
- `DESIGNED_STATE`：设计要求
- `GENERATED_STATE`：模型实际结果
- `ACCEPTED_STATE`：用户明确接受并作为后续现实的结果

模型偶发生成错误不能自动覆盖设计状态。

详见 `references/08-continuity.md`。

## 最终Seedance输出

每组默认结构：

1. `【本组剧情任务】`
2. `【本组总资产映射】`
3. `【镜内生成物】`（有才写）
4. `【本组视觉风格锁定】`
5. `【本组独立生成锁定】`
6. `【导演意图】`
7. `【本组镜头调度】`
8. 逐镜：
   - `【机位／景别／焦段／运镜】`
   - `【构图与空间】`
   - `【触发点】`
   - `【动作与表演】`
   - `【特效／物理反馈】`
   - `【对白／独白】`
   - `【声音】`
   - `【动作终点】`
9. `【本组动作终点】`
10. `【本组禁止项】`仅在确有高风险或用户明确要求时写。

禁止使用“同上一镜”“同前”“承接上一组”“自行发挥”作为关键执行信息。

完整模板与压缩规则读 `references/09-seedance-output.md`。

## 最终QC与返修

每个用户可见生产成品输出前内部执行硬闸门：
`Story / Asset / Space / Grouping / Camera / Action / Performance / Dialogue / Sound / VFX / Continuity / Prompt Density / Isolated Execution / Direct Copy`

失败先修根因，不先加更多词。错误定位到最低必要层，遵守 `MINIMUM NECESSARY ROLLBACK`。

生成结果问题区分：
- STORY
- ASSET
- SPACE
- ACTION
- CAMERA
- PERFORMANCE/AUDIO
- VFX
- PROMPT LOAD

详见 `references/10-qc-repair.md`。

## 用户命令语义

- `通过`：当前版本批准，进入下一层。
- `继续 / 下一步`：保持批准内容，继续生产。
- `修改：...`：进入局部 PATCH，不推进阶段。
- `自检`：审计当前阶段，有问题先修，不自动推进。
- `回退：...`：恢复指定批准版本，重新校验受影响下游。
- `全部输出 / 一口气`：内部完整跑流程，只交付用户要求的最终成品。

## 输出纪律

- 默认不展示隐藏推理、Shot Plan内部表、状态账本、Agent讨论或评分日志。
- 用户要求“自检/为什么/诊断”时，展示可公开的问题、风险与修改结果，不展示私有推理链。
- 不承诺100%一次生成成功；目标是减少因设计歧义、负荷过载和连续性错误造成的无效抽卡。

## Reference map

按任务读取必要文件，不必每次全载入：

- 核心路由、版本与锁：`references/01-core-routing.md`
- 故事事实与可视化剧本：`references/02-story-visual.md`
- 资产系统：`references/03-assets.md`
- Beat/生成组/时间轴：`references/04-grouping.md`
- 导演、Shot Plan、摄影：`references/05-directing.md`
- 动作、表演、对白、声音：`references/06-performance-audio.md`
- VFX与破坏：`references/07-vfx.md`
- 全局连续性：`references/08-continuity.md`
- Seedance最终格式：`references/09-seedance-output.md`
- QC、诊断与返修：`references/10-qc-repair.md`
