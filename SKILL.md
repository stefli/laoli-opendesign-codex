---
name: OpenDesign Codex免费动效
description: >-
  当要用 Open Design 动效设计（Motion）做产品介绍短片、且希望走本机 Codex→Magpie→WorkBuddy 免费
  DeepSeek（不花 OpenDesign Cloud 额度）时使用。
---
# Open Design · Codex 免费动效通道

## 何时用
- 要做 **产品介绍 / 功能讲解** 类短动效视频（约 10–20 秒）。
- 希望用 **Open Design「动效设计」**，但 **不消耗 OpenDesign Cloud 免费额度**。
- 本机已装 Open Design、Codex CLI、Magpie，且 Magpie 已接到 WorkBuddy 免费 DeepSeek（或等价免费路由）。

## 架构一句话
**Open Design UI（动效设计）→ 本机 Codex CLI → Magpie（本机网关）→ WorkBuddy 免费档 DeepSeek Flash**。  
成片仍在 Open Design 里导出；Codex 只是执行通道，不是另开软件做片。

## 与 Cloud 通道的区分（硬性）
| | Codex 免费通道（本技能） | OpenDesign Cloud 免费 |
|---|---|---|
| 设置 | **本机 CLI** → Codex | OpenDesign 官方 / Cloud 模型 |
| 模型芯片 | 「Codex CLI · 默认」 | 「OpenDesign · v4.1-flash」等 |
| 扣什么 | Magpie / WorkBuddy 免费配额 | OD Cloud $ / 积分 |
| 适用 | 日常产品介绍片、省 OD 额度 | 对照评测、官方路径演示 |

两篇图文/两次演示不要混写路径。

## 前置检查（每次开跑前）
1. Magpie 本机可达（常见 `http://127.0.0.1:3425`）；`/v1/models` 能看到免费路由（如 `group/workbuddyfree` 或 `workbuddy-ai-plugin/deepseek-v4.1-flash`）。
2. Codex 配置指向 Magpie，例如 `~/.codex/config.toml`：
   - `model_provider = "magpie"`
   - `model = "workbuddy-ai-plugin/deepseek-v4.1-flash"`（以本机实际暴露的免费模型 id 为准）
3. Open Design 已登录；语言可中文。
4. **设置 → 模型与提供商 → 本机 CLI → 选中 Codex CLI**，模型选「CLI 默认设置」。确认内联模型芯片是 Codex，不是 Cloud。

## 出片步骤
1. 首页创作类型选 **动效设计**（Motion / HyperFrames）。
2. **清空** composer / 当前插件示例文案（防残留导致双交付、多烧配额）。
3. 粘贴**一条**产品介绍提示词（见下模板），只点 **运行一次**。
4. 等 HyperFrames 写出并渲染 MP4；导出到约定目录。
5. 抽 3–5 帧关键画面备查；记录墙钟与是否误开其它交付。
6. 若 Agent 开始做额外无关项目：Motion MP4 一落地就 **停止**，勿继续烧配额。

## 产品介绍提示词模板
按产品改括号内容；默认约 15 秒、16:9、中文、无旁白音轨：

```
请用 HyperFrames 做一段约15秒、16:9 的中文动效短片：主题「（产品名）（一句话卖点）」。
三幕依次出现：(1)（痛点/打开场景）→ (2)（核心操作）→ (3)（结果/收益）。
风格简洁扁平、（品牌主色）配色、大标题+短字幕，节奏明快，结尾定格「（收束口号）」。
不要旁白音轨，不要过度花哨，不要额外做第二个无关产品。
```

## 产出落点
- 工作目录：`/workspace/reviews/<topic-slug>/outputs/`（一题一目录）。
- 至少保留：`*.mp4`、源 `*.html`（若有）、`NOTES.md`（提示词、模型芯片文案、耗时、配额说明）。
- 对外路径用虚拟用户 `laoli`；密钥/邮箱/额度数字截图须遮或隔离工程。

## 省配额硬规则
- **只生成一次**；失败最多再试一次，先查设置是否仍是 Codex。
- 提交前必须清空示例文案。
- 不要为了「再好看一点」重生。
- 不要切到 Opus / 需升级的 Cloud 模型。
- 不要在本通道里填付费 DeepSeek API Key（除非用户明确要求且接受扣费）。

## 验收
- [ ] 模型芯片显示 Codex CLI（非 OD Cloud）
- [ ] 有可播放 MP4，时长接近提示词
- [ ] OD Cloud 积分/额度前后无扣（或可证明未走 Cloud）
- [ ] NOTES 写清「Codex→Magpie→免费 DeepSeek」
- [ ] 无把无关第二项目做完

## 不要做
- 不要把本技能写成「用 Codex 单独做视频」——必须是 Open Design 动效设计 UI。
- 不要与 Cloud 免费成片混在同一 NOTES 里不标注路径。
- 不要占用用户当前工作区截图；产品演示素材用独立测试目录。
