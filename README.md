# Seedance Production Master

一个面向 Seedance 2.0 / 2.5 AI 影视生产的 Codex Skill / Plugin。

主要用于：

- 小说 / 剧本 → Seedance 可执行导演分镜
- 可视化剧本 → 逐组 Seedance 生成提示词
- 资产映射、空间关系、人物站位、摄影、构图、运镜
- 动作因果、自然表演、对白、声音、VFX
- 跨镜 / 跨组连续性
- 已生成视频的问题诊断与局部返修

## 核心生产规则

- 单个 Seedance 生成组硬上限：**28 秒**
- 实际组时长根据剧情、台词、场景、动作、情绪、VFX 和模型执行负荷自然决定
- 每个生成组都必须能单独复制执行
- 不使用“同上一镜 / 同前 / 承接上一组”作为关键执行信息
- 已锁定剧本和对白不得无授权修改
- 世界空间高于画面左右
- 动作必须有 Trigger 和 Result
- VFX 可以超自然，但必须遵守项目世界规则和连续状态
- 生成失败先诊断根因，不默认继续堆提示词

## 仓库结构

```text
.
├── .agents/
│   └── plugins/
│       └── marketplace.json
└── plugins/
    └── seedance-production-master/
        ├── .codex-plugin/
        │   └── plugin.json
        └── skills/
            └── seedance-production-master/
                ├── SKILL.md
                └── references/
                    ├── 01-core-routing.md
                    ├── 02-story-visual.md
                    ├── 03-assets.md
                    ├── 04-grouping.md
                    ├── 05-directing.md
                    ├── 06-performance-audio.md
                    ├── 07-vfx.md
                    ├── 08-continuity.md
                    ├── 09-seedance-output.md
                    └── 10-qc-repair.md
```

## Codex 中安装

### 方法一：Codex UI / TUI

打开 Codex 的 Plugins 页面或在 TUI 输入：

```text
/plugins
```

选择：

```text
Add Marketplace
```

输入你的 GitHub 仓库：

```text
你的GitHub用户名/seedance-production-master
```

然后在 Marketplace 中找到：

```text
seedance-production-master
```

并启用 / 安装。

### 方法二：CLI 添加 Marketplace

```bash
codex plugin marketplace add 你的GitHub用户名/seedance-production-master
```

然后在 Codex `/plugins` 中找到并启用 `seedance-production-master`。

## 调用示例

```text
使用 $seedance-production-master，
把这个剧本转换成可以逐组直接复制到 Seedance 的可执行导演分镜。
```

也可以：

```text
使用 $seedance-production-master，
自检第6组，重点检查空间、人物站位、动作轨迹、摄影机、道具和上下组连续性。
```

或：

```text
使用 $seedance-production-master，
分析我生成的这个视频为什么出现方向翻转，并只返修相关提示词。
```

## 与 screenwriting-master 的关系

本 Skill 独立存在，不覆盖、不修改、不依赖 `$screenwriting-master`。

推荐工作流：

```text
$screenwriting-master
        ↓
完成 / 修正剧本
        ↓
$seedance-production-master
        ↓
Seedance 影视生产执行
```
