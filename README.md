# Awesome Free LLM API（免费大模型 API 导航）

**简体中文** | [English](README.en.md)

> 以**渠道**为主体：下面每个渠道都给出官网、免费形式和官网上的免费说明。
> 想按模型找免费渠道：重点模型见[模型免费渠道索引](#模型免费渠道索引)。
> 最近一次全量实测复核：**2026-11-12**（逐个拉取 `/v1/models` 与定价、POST 试调端点）；**2026-11-14** 单点实测新增 cheapllm.shop。免费名单轮换极快，正文中的历史日期按条目保留，带「2026-11-12」字样的为该次全量实测结论，带「2026-11-14」字样的为新增条目实测。

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

本列表只收录你能**持续调用**的**永久免费** API，以及**明确标注限时免费**的 API。**只认 API**——必须能拿到 API Key、通过 endpoint 调用才算数；模型官网的网页对话（Chat 界面）免费开放，**不属于本列表范畴**。


---

## 目录

- [收录范围](#收录范围)
- [匿名模型（Stealth）](#匿名模型stealth)
- [模型免费渠道索引](#模型免费渠道索引)
- [免费渠道一览](#免费渠道一览)
  - [海外官方免费层](#海外官方免费层)
  - [中国平台](#中国平台)
  - [聚合与网关](#聚合与网关)
  - [限时免费](#限时免费)
  - [小型网关（谨慎）](#小型网关谨慎)
  - [客户端内免费（无公开 API）](#客户端内免费无公开-api)
- [参与贡献](#参与贡献)
- [免责声明](#免责声明)
- [许可证](#许可证)

---

## 收录范围

本列表只收录**两类**：

| 类型 | 含义 | 标签 |
|------|------|------|
| **永久免费层** | 周期性额度（按天/月重置），不会过期 | `permanent-free` |
| **永久免费模型** | 指定模型完全免费，只有速率限制 | `permanent-free` |
| **限时/限量免费** | 明确标注"限时免费 / Limited-Time Free / 限量免费"的模型或渠道 | `limited-free` |

以上都限定为 **API 层面的免费**：能申请 API Key、能通过 HTTP endpoint / SDK 程序化调用。仅网页对话免费（如各家官网的 Chat 页面）不在此列。

**唯一例外**是[客户端内免费](#客户端内免费无公开-api)一节：Freebuff、AtomCode 这类把额度锁在自家客户端、拿不到公开 endpoint 的产品，单独列出仅供了解——**不属于收录渠道，不进模型索引，也不代表其条款允许外部调用**（Freebuff 的条款反而明令禁止）。

## 匿名模型（Stealth）

> 本节收录**不公开身份**的模型：没有厂商名、没有可考的模型代号，只有一个代号和一份限时免费的上游合约。它们**不适合放进下面的具名模型索引**（无处落脚，也无从判断强弱），因此单独成节。

匿名模型的性质需要先说清楚，它们和其他渠道不是一回事：

| 特征 | 说明 |
|------|------|
| **身份不明** | 开发者不公开，`tokenizer` 多数标 `Other`；有第三方测评发现其 tokenizer 指纹接近 MiniMax 家族，但这**只是指纹相似，不等于官方确认**，不要按 MiniMax 对待 |
| **随时消失** | 没有任何公开的稳定性承诺，通常是发布前的短期评测窗口，说不准哪天就下架或换成付费 |
| **能力无基线** | 没有公开 benchmark 榜单，模型索引里那些"上下文多大、编码能力如何"的说法都来自单方测评，不可当结论 |
| **隐私条款因渠道而异** | 同一模型在不同网关的数据处理政策**完全不同**，有的零保留不训练，有的明确写"免费期数据可用于改进模型"——见下表逐条标注 |

| 模型 | 免费渠道 | 免费形式 | 上下文 / 输出 | 数据政策 | 备注 |
|------|------|------|------|------|------|
| **Glyph Cluster** | [BazaarLink](https://bazaarlink.ai) · [Vercel AI Gateway](https://vercel.com/ai-gateway) · [Kilo Gateway](https://kilo.ai) | 免费档 $0（`stealth/glyph-cluster`；BazaarLink 免费路由写 `stealth/glyph-cluster:free`） | 256K / 未公布 | 未公布（BazaarLink 目录标 `owned_by: stealth`、`zdr_available: false`；Kilo 标 `mayTrainOnYourPrompts: true`） | ⚠️ 2026-10-07 上架；2026-11-12 实测三处目录均在列、定价均为 $0，但 Vercel / BazaarLink 均需 key，**仅 Kilo 免 key POST 返 200**；无厂商名、无公开 benchmark；BazaarLink 侧受免费档共享额度约束（未充值 10 RPM / 每日 60 加权单位） |

> ℹ️ **匿名代号会被「揭晓」**：Reflection 的 **Beam**（501B MoE）此前正是以匿名代号 `cat-jam`（OpenCode 通道）/ `MissingNo`（Nous Portal）流通，2026-10-16 权重与身份公开后即转为具名模型（见[海外模型](#海外模型)）。这说明匿名模型通常只是**揭晓前的临时窗口**；反过来也有等不到揭晓就消失的——OpenCode Zen 上那批匿名款（`space-bunny-free`、`big-pickle`）已全部退出本表，详见下方接入说明。

- **接入**（对应上表在列的 Glyph Cluster，2026-11-12 实测端点可达）：
  - BazaarLink：`POST https://api.bazaarlink.ai/v1/chat/completions`，模型名 `stealth/glyph-cluster:free`（免 key 实测 401 缺鉴权）
  - Vercel AI Gateway：`POST https://ai-gateway.vercel.sh/v1/chat/completions`，模型名 `stealth/glyph-cluster`（免 key 实测 401 缺鉴权）
  - Kilo Gateway：`POST https://api.kilo.ai/api/gateway/v1/chat/completions`，模型名 `stealth/glyph-cluster`——**免注册免 key 实测 200**，是本节唯一能直接调通的通道
- **已移除的匿名款（备查）**：OpenCode Zen 的 `space-bunny-free`（`POST https://opencode.ai/zen/v1/chat/completions`）与 `big-pickle` —— ⚠️ 2026-10-12 实测免 key 与带有效 Zen API key 均返 403 `FreeTierError`（"can only be used from within OpenCode"；key 有效性已验证：同 key 调付费模型返 402 余额不足），免费层只能在 OpenCode 客户端内调用；⚠️ 2026-10-24 复核：`space-bunny-free` 已下架、`big-pickle` 仍在 Zen 目录但同样 403，故从本表删除。另有 OpenRouter 的 `stealth/space-bunny-alpha` 通道已于 2026-10-06 下架，原端点 `POST https://openrouter.ai/api/v1/chat/completions` 不再可用

## 模型免费渠道索引

### DeepSeek 系列

#### DeepSeek V4.1 Flash

> 552B 新架构 MoE（8B/16B 激活）,原生多模态,1M 上下文；2026-09-10 发布

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(不限 token),40 RPM | 优势:官方托管、免绑卡、无积分/无日限、1M 上下文;限制:需短信验证手机号,40 RPM 全站共享,高峰期需排队 | 经常超时 |
| [Token Harbor](https://tokenharbor.ai) | 免费层月额度内(4 周滚动刷新) | 优势:小型网关、免卡注册、**Free 档明确含 V4.1 Flash**;限制:⚠️ **中国大陆/香港/澳门被区域封锁**,需境外网络;额度未公开、按 4 周滚动刷新,网关资历浅 | 区域受限 |
| ~~[Onomeo](https://onomeo.com/zh)~~ | ⚠️ 机制待核实（2026-11-12） | ⚠️ 站点已改版：签到/问卷文案下线（内嵌 `survey: false`）、premium 改为 `buyersOnly: true`，**当前是否还有免费调用入口无法证实**；原「8,409 额度/次、签到满额约 23 次」及 9/22 的 1,473 全部作废，勿据此估算次数 |  |
| [魔搭 ModelScope](https://modelscope.cn) | 共享额度内（全站 2000 次/日） | 优势:国产、国内直连免代理、OpenAI 兼容、目录含 `deepseek-ai/DeepSeek-V4.1-Flash`（2026-10-12 实测在列）;限制:免费质量较低——与全站共享每日 2000 次总量、单模型约 500 次/日，需阿里云实名、仅限个人非商业用途 | 质量较低 |
| [BeatAPI](https://beatapi.io) | 限时免费（`deepseek-v4.1-flash-free`，输入/输出均 $0） | 优势:OpenAI 兼容、免卡免充值、**零余额即可调用**、每日 2000 次成功请求、国内直连可通;限制:⚠️ **首充前仅 1 次成功请求/分钟**（任意充值后 10 次/分钟），免费为限时提供、名单随时变，2026-10 新上线的折扣转售商，端到端调用未经本仓库实测 | 未实测 |
| [Zro (MoonMath)](https://zro.moonmath.ai) | 免费档每日额度（`deepseek-v4.1-flash`，每日重置、数值未公开） | 优势:一手推理服务、OpenAI 兼容、零请求保留且不用于训练、无需付费、国内直连可通;限制:每日免费额度未公开、仅 Flash 模型免费、一人一号禁止多账号刷额度、端到端未实测 | 未实测 |
| [cheapllm.shop](https://cheapllm.shop) | 限时免费（beta 期 $0、无速率限制；ToS 承诺 beta 后每小时 ≥5,000/1,000 tokens 的永久免费额度） | 优势:注册只需邮箱+密码、无卡无手机号无邮箱验证即拿 key、OpenAI 兼容、国内直连可通;限制:⚠️ 法律信息页主体信息全空、上线仅一周无第三方验证、无 SLA 且可无理由封号、备用推理商可能保留数据用于训练、端到端未实测 | 未实测 |

> ⚠️ **官方无免费层**（仅付费，闲时 $0.15/$0.60 per 1M）。Ollama Cloud、OrcaRouter 均不提供 V4.1 免费。✅ 真正的「档位免费」入口有五个：**NVIDIA NIM**（永久免费 40 RPM、免绑卡）、**魔搭 ModelScope**（每日免费额度内、国内直连）、**BeatAPI**（限时免费 `deepseek-v4.1-flash-free`，零余额可调但仅 1 次/分钟）、**Zro**（免费档每日额度、零请求保留）与 **cheapllm.shop**（beta 期 $0，ToS 承诺 beta 后每小时 ≥5,000/1,000 tokens 的永久免费额度）；Token Harbor 对国内封锁；⚠️ **Onomeo 已于 2026-11-12 改版、签到机制下线，免费入口待核实**，不再按「签到额度」计入本表。

#### ~~DeepSeek V4 Pro~~（2026-09-14 起官方路由退役）

> 旗舰 MoE,1M 上下文,编程与智能体场景最强。⚠️ 官方 API 自 2026-09-14 12:00 起将 `deepseek-v4-pro` 请求全部转发到 V4.1 Flash 并按 Flash 价计费，直至 V4.1 Pro 上线

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [书生·端砚 墨点计划](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | 测试期每月赠送墨点，按墨点折算 tokens（1 墨点最多抵 50,000,000 tokens，以 DeepSeek-V4-Flash 为例） | 优势:上海人工智能实验室官方平台、墨点额度每月自动到账、免绑卡、同时支持 OpenAI 与 Anthropic 协议; ⚠️ 官方从未公布每月赠送多少墨点、需注册才能查看实际余额、科研向平台非通用聊天网关、额度不可提现、规则随时可能调整 |  |

#### DeepSeek V4 Flash

> 284B MoE,1M 上下文,代码 / 推理性价比首选。⚠️ 官方模型名 `deepseek-v4-flash` 已自动路由到 V4.1 Flash,旧 ID 仍可用

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OrcaRouter](https://www.orcarouter.ai) | 免费池限流,零加价 | 优势:200+ 模型统一网关、0% token 加价、免卡;限制:免费额度未公开、429 限流、best-effort 非生产可用 |  |
| [BazaarLink](https://bazaarlink.ai) | 免费档 `deepseek-v4-flash-0731free:free`(输入/输出均 $0) | 优势:台湾网关、免绑卡、含 0731 正式版;限制:小型网关资历浅、限流使用、免费额度未公开 |  |
| [OpenCode Zen](https://opencode.ai/zen) | 限时免费(`deepseek-v4.1-flash-free`) | 优势:OpenCode 官方网关、免卡、1M 上下文;限制:⚠️ 2026-10-24 实测旧 `deepseek-v4-flash-free` 已退出、现为 `deepseek-v4.1-flash-free`，但**免 key 调用返 403 `FreeTierError`，只能在 OpenCode 客户端内用**；免费期数据用于改进模型、名单反复横跳 | 客户端锁定 |
| [Hugging Face](https://huggingface.co) | 每月 $0.10 免费推理额度,超额按量付费 | 优势:社区模型极全、OpenAI 兼容;限制:免费额度仅 $0.10/月、超额即按量付费(hard stop),共享端点限流、无 SLA | 额度极小 |
| [书生·端砚 墨点计划](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | 测试期每月赠送墨点，按墨点折算 tokens（1 墨点最多抵 50,000,000 tokens，以 DeepSeek-V4-Flash 为例） | 优势:官方唯一明示的换算基准模型、上海 AI 实验室官方平台、每月自动到账、OpenAI + Anthropic 双协议; ⚠️ 官方从未公布每月赠送多少墨点、需注册才能查看实际余额、1 墨点为「最多」抵 50,000,000（调用贵模型消耗更快）、科研向平台 |  |
| [魔搭 ModelScope](https://modelscope.cn) | 约 200 次/日 | 优势:国产、OpenAI 兼容、模型全;限制:免费质量较低——单模型仅约 200 次/日,与全站共享 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |

### GLM 系列

#### GLM-5.3 Flash

> 原生多模态,320B,1M 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(不限 token),40 RPM | 优势:官方托管、免绑卡、无积分/无日限、1.3M 上下文多模态;限制:需短信验证手机号,40 RPM 全站共享,高峰期需排队 | 经常超时 |
| [OrcaRouter](https://www.orcarouter.ai) | 免费池限流,零加价 | 优势:200+ 模型统一网关、0% token 加价、免卡;限制:免费额度未公开、2026-09-07 起替换 Qwen3.8-27B 成为免费默认,TTFT 偏高(约 7.66 秒) | 限流 |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | 限时免费(ZZ.ai) | 优势:AMD 官方托管、每日 $10 等值额度;限制:限时免费、TTFT 偏高、并发限流 | TTFT 偏高 |
| [BeatAPI](https://beatapi.io) | 限时免费（`glm-5.3-flash-free`，输入/输出均 $0） | 优势:OpenAI 兼容、免卡免充值、零余额即可调用、每日 2000 次成功请求;限制:⚠️ **首充前仅 1 次成功请求/分钟**（充值后 10 次/分钟）、免费层限时、端到端调用未实测 | 未实测 |
| [Zro (MoonMath)](https://zro.moonmath.ai) | 免费档每日额度（`glm-5.3-flash`，每日重置、数值未公开） | 优势:一手推理服务、OpenAI 兼容、零请求保留且不用于训练、无需付费、236 tok/s、1M 上下文;限制:每日免费额度未公开、仅 Flash 模型免费、一人一号禁止多账号刷额度、端到端未实测 | 未实测 |
| ~~[Onomeo](https://onomeo.com/zh)~~ | ⚠️ 机制待核实（2026-11-12） | ⚠️ 站点改版后 `z-ai/glm-5.3-flash-free` 这个 ID 已不存在于当前目录（现为 `glm-5.3-flash`，cost 7,701），签到文案与「premium 每日 5 万上限」规则均已下线；原「3,149 额度/次、约 63 次」作废 |  |
| [书生·端砚 墨点计划](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | 测试期每月赠送墨点，按墨点折算 tokens（1 墨点最多抵 50,000,000 tokens，以 DeepSeek-V4-Flash 为例） | 优势:上海 AI 实验室官方平台、每月自动到账、免绑卡、1M 上下文、OpenAI + Anthropic 双协议; ⚠️ 官方从未公布每月赠送多少墨点、需注册才能查看实际余额、⚠️ 未经证实 GLM-5.3 是否在墨点免费池内（官方页面仅明示 V4-Flash）、科研向平台 |  |

#### GLM 5.2 / 5.1

> 智能体工作流旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenCode Zen](https://opencode.ai/zen) | 限时免费模型(`glm-5.3-flash-free`) | 优势:OpenCode 官方网关、免卡;限制:仅限时免费的 Flash 款,正式版 GLM 5.3 为付费($1.4/$4.4);⚠️ 2026-10-24 实测 Zen 目录新增 `glm-5.3-flash-free`（$0），但免 key 调用仍返 403 `FreeTierError`，只能在 OpenCode 客户端内用 |  |

> ✅ **GLM-5.3-Flash 已在 NVIDIA NIM 上架**：截至 2026-09-12 实测 `integrate.api.nvidia.com/v1/models` 共 82 个模型，其中 `z-ai/glm-5.3-flash` 在列（1.3M 上下文、多模态、40 RPM）。注意这不是"整个 GLM 系列回归"——GLM 5.2 / 5.1 / 4.7 仍未在列。

#### GLM-4.7-Flash / GLM-4-Flash

> 智谱免费引流款,200K 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [智谱 BigModel](https://open.bigmodel.cn) | 永久免费,仅限速 | 优势:官方永久免费、200K 上下文、无需付费;限制:仅 Flash 小模型,有速率限制 |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [OpenCode Zen](https://opencode.ai/zen) | 限时免费(客户端内) | 优势:OpenCode 官方网关、无卡;限制:限时免费,仅客户端内使用,免费名单随时变动 |  |

> ⚠️ **GLM-4.7 不在 NVIDIA NIM 免费名单**：2026-09 初一度上架后又移除；截至 2026-09-12，NIM 上仅新上架了 `z-ai/glm-5.3-flash` 一款，GLM-4.7 仍不在列，勿再依赖。

### Qwen 系列

#### Qwen3.5 122B / 397B

> 阿里旗舰 MoE,多模态,智能体就绪

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [魔搭 ModelScope](https://modelscope.cn) | 共享额度内 | 优势:国产、模型全家桶;限制:免费质量较低——与全站共享每日 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |

> ⚠️ **Qwen3.5 122B / 397B 已不在 NVIDIA NIM**：截至 2026-09-11 已从 NIM 模型列表移除。

#### Qwen3 Coder Plus

> 代码专项，1M 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| — | **无免费 API 渠道** | ⚠️ 2026-11-12 复核：xKiro AI 目录从 97 款缩至 **69 款**、`access_tier: free` 从 47 款降至 **26 款**，**Qwen 全家桶全部退出免费档**，该网关现存的免费款与 Qwen 无关；`qwen/qwen3-coder-plus` 已不在目录，原免费行删除 |  |

#### Qwen3 Coder 480B

> 代码专项 SOTA,Agent 编码

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| ~~[魔搭 ModelScope](https://modelscope.cn)~~ | ⚠️ 已不在目录（2026-11-12） | ⚠️ 2026-11-12 实测 `api-inference.modelscope.cn/v1/models` 共 38 款，**`Qwen3-Coder-480B` 已不在列**；原「约 500 次/日」作废 |  |

> ⚠️ **Qwen3 Coder 480B 已不在 OpenRouter 免费名单**（2026-09-11 实测）。

#### Qwen3 235B

> 通用 MoE 旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| ~~[魔搭 ModelScope](https://modelscope.cn)~~ | ⚠️ 已不在目录（2026-11-12） | ⚠️ 同上，`Qwen3-235B` 已不在当前 38 款目录，原「约 500 次/日」作废 |  |

> ⚠️ **Qwen3 235B 已不在 OpenRouter 免费名单**（2026-09-11 实测）。

#### Qwen3.8 Max / Qwen3.7 Max

> 阿里旗舰 Max 档，1M 上下文（此前本仓库 Qwen 系列几乎无优质免费渠道）

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| — | **无免费 API 渠道** | ⚠️ 2026-11-12 复核：xKiro AI 的 `qwen/qwen3.8-max:free`、`qwen/qwen3.7-max:free` 已全部退出目录，该网关现无任何 Qwen 免费款；此前「唯一 Qwen Max 免费入口」的结论作废 |  |

#### Qwen3.8 Flash

> 轻量多模态,中文写作强

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Groq](https://console.groq.com) | 1000 次/日 | 优势:LPU 极速推理(700+ token/s);限制:30 RPM / 1000 RPD,TPM 8K |  |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | 限时免费(Qwen3.8-Flash-Next) | 优势:AMD 官方托管、每日 $10 等值额度;限制:限时免费、TTFT 偏高、并发限流 | TTFT 偏高 |

#### Qwen3.6 27B

> 轻量通用,多语言

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Groq](https://console.groq.com) | 1000 次/日 | 优势:LPU 极速推理;限制:30 RPM / 1000 RPD,TPM 8K |  |

#### Qwen2.5 72B

> 通用大杯

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| ~~[魔搭 ModelScope](https://modelscope.cn)~~ | ⚠️ 已不在目录（2026-11-12） | ⚠️ 2026-11-12 实测目录已无 `Qwen2.5-72B`；Qwen 侧当前仅 `Qwen3.5-122B-A10B` / `Qwen3.5-397B-A17B` / `Qwen3.8-27B` / `Qwen3.8-Flash-Next` 等在列 | 质量较低 |

#### Qwen3-8B / GLM-4-9B

> 9B 级轻量模型

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [硅基流动](https://cloud.siliconflow.cn) | 9B 及以下永久免费 | 优势:国产、9B 以下全免费;限制:仅小模型免费,大模型需付费 |  |


### 其他国产模型

#### MiniMax M2.7

> 230B,代码 / 推理 / 办公

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenCode Zen](https://opencode.ai/zen) | MiniMax M3 限时免费(客户端内) | 优势:OpenCode 官方网关;限制:仅客户端内使用,M2.7 为付费($0.3/$1.2) |  |

> ⚠️ **MiniMax 系列已从 NVIDIA NIM 下架**：2026-09 初曾短暂上架 GLM-4.7 与 MiniMax M2.1，2026-09-11 两者移除；2026-09-27 复测 **MiniMax M3 也不在列**（NIM 目录已无任何 minimax 条目）；✅ **2026-10-24 复测 MiniMax 回归 NIM**——`minimaxai/minimax-m3.1-flash` 已在列（见下）。

#### MiniMax M3

> 多模态 MoE,推理 / 工具调用

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [OpenCode Zen](https://opencode.ai/zen) | 限时免费(客户端内) | 优势:OpenCode 官方网关、免卡;限制:限时免费,仅客户端内使用 |  |

#### MiniMax M2.1

> 多语言编程强化版,204K 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| OpenCode Zen | ⚠️ 已弃用(2026-03-15) | 该模型在 OpenCode Zen 已下架,官方 API 为付费($0.3/$1.2) |  |

#### MiniMax M3.1 Flash

> 2026-10 上架的新款 Flash；截至 2026-11-12 **仅 NVIDIA NIM 仍提供免费调用**

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(不限 token),40 RPM | 优势:官方托管、免绑卡、无积分/无日限;限制:需短信验证手机号,40 RPM 全站共享（2026-10-24 实测在列：`minimaxai/minimax-m3.1-flash`） | 经常超时 |

> ⚠️ **2026-11-12 复核，两个免费通道同时失效**：Vercel AI Gateway 的 `minimax/minimax-m3.1-flash` 已转计费（$0.15/M 输入、$0.6/M 输出），BeatAPI 免费名单也已移除 `minimax-m3.1-flash-free`（现仅 3 款免费）。两行按本仓库口径整行删除；本节目前**仅 NVIDIA NIM 一个免费渠道**。

#### Kimi K2.6

> 1T MoE,长程编码,多模态

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(不限 token),40 RPM | 优势:官方托管、免绑卡、无积分/无日限;限制:需短信验证手机号,40 RPM 全站共享 | 经常超时 |
| [书生·端砚 墨点计划](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | 测试期每月赠送墨点，按墨点折算 tokens（1 墨点最多抵 50,000,000 tokens，以 DeepSeek-V4-Flash 为例） | 优势:上海 AI 实验室官方平台、每月自动到账、免绑卡、OpenAI + Anthropic 双协议; ⚠️ 官方从未公布每月赠送多少墨点、需注册才能查看实际余额、⚠️ 未经证实 Kimi-K2.6 是否在墨点免费池内（官方页面仅明示 V4-Flash）、科研向平台 |  |

#### Kimi K3

> 2.8T 原生多模态 Agent,1M 上下文,长程编程 / 复杂推理

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| ~~[NVIDIA NIM](https://build.nvidia.com)~~ | ⚠️ 已下架(2026-10-24) | ⚠️ 2026-10-24 实测 `integrate.api.nvidia.com/v1/models` 已无 `moonshotai/kimi-k3`（NIM 上的 Kimi 仅剩 `kimi-k2.6`）；K3 目前**无免费 API 渠道**，官方 API 为付费 |  |

#### StepFun Step 3.7 Flash

> 国产稀疏 MoE 推理模型

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [魔搭 ModelScope](https://modelscope.cn) | 共享额度内（全站 2000 次/日） | 优势:国产、国内直连、OpenAI 兼容、2026-11-12 实测 `api-inference` 目录含 `stepfun-ai/Step-3.7-Flash`;限制:与全站共享每日 2000 次总量、需阿里云实名、仅限个人非商业用途 | 质量较低 |

> ⚠️ NVIDIA NIM 侧仍无 Step 3.7 Flash（10-24 上架的是 `stepfun-ai/step-5-preview`）；原先「暂无免费 API」的说法已过时。

#### 豆包 Doubao Lite

> 字节轻量旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [火山方舟](https://console.volcengine.com/ark) | 每日 200 万 token 免费额度 | 优势:每日 200 万 token 大额免费、国产;限制:需注册火山引擎并实名,以控制台为准 |  |

#### ~~混元 Lite / Hy3~~（Lite 随旧平台 9/30 停服失效）

> 腾讯通用 / 旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| ~~[腾讯混元](https://cloud.tencent.com/product/hunyuan)~~ | ~~Lite 永久免费~~ 旧平台 2026-09-30 停服，新平台 TokenHub 无 Lite | 优势:官方永久免费(已随旧平台下线终结);限制:仅 Lite 免费(已失效),需腾讯云账号实名 |  |
| [OrcaRouter](https://www.orcarouter.ai) | 免费池限流,零加价 | 优势:200+ 模型统一网关、0% token 加价、免卡;限制:免费额度未公开、429 限流、best-effort 非生产可用 |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |

#### ERNIE-Speed / Lite

> 文心轻量免费款

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [百度千帆](https://cloud.baidu.com/product/wenxinworkshop) | 永久免费,限速 | 优势:官方永久免费;限制:QPS 限 1,需百度智能云账号实名 |  |

#### MiMo-V2.5

> 小米多模态推理

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |

### 海外模型

#### GPT-OSS 120B / 20B

> OpenAI 开源 MoE,代码 / 推理强

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Groq](https://console.groq.com) | 1000 次/日 | 优势:LPU 极速推理;限制:30 RPM / 1000 RPD,TPM 8K |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(不限 token,仅 20B) | 优势:官方托管、免绑卡、无积分/无日限;限制:需短信验证手机号,40 RPM 全站共享,仅托管 gpt-oss-20b | 经常超时 |

> ⚠️ **GPT-OSS 已不在 OpenRouter 免费名单**（2026-09-11 实测）。

#### Reflection Beam

> Reflection AI 首个开源权重模型：501B MoE（每 token 激活 23B），1M 上下文，Apache 2.0；2026-10-16 发布并公开权重。⚠️ 此前以匿名代号 `cat-jam`（OpenCode）/ `MissingNo`（Nous Portal）流通，现已揭晓，详见[匿名模型](#匿名模型stealth)

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Vercel AI Gateway](https://vercel.com/ai-gateway) | 限时免费零价路由（`reflection/beam-free` 与 `reflection/beam`，均 $0/$0） | 优势:Reflection 官方直供、1M 上下文、可调 reasoning effort、支持工具调用与结构化输出、零数据保留;限制:⚠️ 限时免费且两种 ID 行为不同——官方原文「`-free` 后缀款在免费期结束时**停止服务**，无后缀款会自动转入计费」;走免费额度需先绑支付方式 |  |
| [OpenCode Zen](https://opencode.ai/zen) | 限时免费（`beam-free`，仅客户端内） | 优势:OpenCode 官方网关、免卡;限制:⚠️ 2026-11-12 实测免 key 返 403 `RegionError`（"This model is not available in your country"）——**只能在 OpenCode 客户端内调用**，且另有地区限制 | 客户端锁定 |

> ⚠️ **2026-11-12 复核，三个通道退出本节**：BazaarLink 的 `reflection/beam` 已改按量计费（$0.25/$1 per 1M）、`beam-free` 零价路由消失；Kilo Gateway 的 `reflection/beam-free` 免 key 已返 404「模型不存在」；Ollama Cloud 从未公布 starter 免费清单、免 key 返 401，**不记为免费渠道**。三行按本仓库口径整行删除；本节目前仅 Vercel AI Gateway 与外部不可调的 OpenCode Zen。

> ⚠️ **Reflection 官方 API 是免费公测**（`https://api.reflection.ai/openai/v1`，模型 ID `Beam-1.0-501B-A23B`），但**未公布按量定价、需注册拿 key**；2026-10-24 实测无 key 请求被其边缘网关挡回 403（HTTP 层即拦截，不是鉴权响应）。按本仓库「注册赠送额度不收」的口径，官方公测额度**不列入索引**。OpenRouter 侧 `reflection/beam-1.0-501b-a23b` 为**付费**（$0.25 / $1 per 1M），别与免费路由混淆。

#### GPT-6 Astra

> OpenAI 旗舰模型（`gpt-6-astra`）

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| ~~[Onomeo](https://onomeo.com/zh)~~ | ⚠️ 机制待核实（2026-11-12） | ⚠️ 站点已改版：premium 名单从 13 增至 28 个 ID、`dailyCap` 降为 10,000 且标 `buyersOnly: true`，签到文案下线；原「3,948 额度/次、未付费约 12 次/天、13 款 premium 每日 5 万上限」全部作废，当前无付费是否仍可调用无法证实 |  |

#### Gemini 2.5 Flash / Flash-Lite

> Google 免费层主力,多模态

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Google AI Studio](https://aistudio.google.com) | 按天重置(2.5 Pro 5 RPM/50 RPD、Flash 15 RPM/1500 RPD、Flash-Lite 30 RPM/1500 RPD) | 优势:官方免费、免绑卡、多模态、1M 上下文;限制:2.5 Pro 免费档仅 5 RPM/50 RPD(trial-only)、需 Google 账号、免费层数据可能用于改进产品、高峰实际吞吐远低于标称 |  |

#### Nemotron 3 Ultra / Super / Lightning

> NVIDIA 智能体旗舰,1M 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free`（Ultra / 3.5 Lightning / 3.5 Super VL / 3 Nano Omni 等 5 款） | 优势:聚合路由;限制:免费仅 50 次/天,名单随时轮换;⚠️ 2026-11-12 实测：**`nemotron-3-super-120b-a12b:free`、`nemotron-3.5-content-safety:free` 已退出零价池**——Super 10-24 才回归，仅维持 19 天 |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [Kilo Gateway](https://kilo.ai) | 免费档 $0（`:free` 后缀款，现 5 款 Nemotron） | 优势:**免注册免 key**、官方明文支持匿名调用、200 次/小时/IP，2026-11-12 实测 `nvidia/nemotron-3.5-lightning:free` 免 key 返 200;限制:⚠️ 同批有多款非 Nemotron 免费路由已退出免费目录（详见该渠道条目），`mayTrainOnYourPrompts` 全部为 true |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(不限 token),40 RPM | 优势:官方自营旗舰、免绑卡、无积分/无日限、1M 上下文;限制:需短信验证手机号,40 RPM 全站共享,仅托管 Ultra/Lightning(Super 已下架) | 经常超时 |

#### InKling / ~~Ling 3.0 Flash~~（OpenRouter 新晋免费）

> Thinking Machines 的 InKling 与蚂蚁的 Ling 3.0 Flash,均为 1M / 262K 上下文多模态

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free`（现为 `inkling-2-small` 一款） | 优势:1M 上下文多模态、聚合路由;限制:免费仅 50 次/天,名单随时轮换;⚠️ 2026-11-12 实测：旧 `inkling` / `inkling-small` 两款均退出零价池，Ling 3.0 Flash 三款仍未回归；同期另有 2 款新模型入池，见[免费渠道一览](#免费渠道一览) |  |

#### Llama 3.3 70B

> 通用开源经典

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | 蒸馏版,1 万 Neurons/日 | 优势:边缘节点低延迟;限制:蒸馏版非原版、每日额度小 |  |

#### ~~Llama 4 Scout~~（已不在 OpenRouter 免费名单）

> 轻量高速,超长上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| — | **无免费渠道** | ⚠️ 截至 2026-09-11，OpenRouter 免费名单中已无任何 Llama 模型 |  |

#### Mistral Large / Small / Codestral

> 欧洲开源旗舰,编码 / 通用

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | Small,1 万 Neurons/日 | 优势:边缘低延迟;限制:仅 Small 版、每日额度小 |  |

#### Gemma 4 31B / 26B

> Google 开源,视觉 + 文本

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free`（31B 与 26B-A4B 两款） | 优势:聚合路由;限制:免费仅 50 次/天,名单随时轮换 |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(不限 token,仅 31B) | 优势:官方托管、免绑卡、无积分/无日限;限制:需短信验证手机号,40 RPM 全站共享,NIM 仅托管 `gemma-4-31b-it`,无 26B-A4B | 经常超时 |

#### Whisper

> 语音转写

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Groq](https://console.groq.com) | 2000 次/日 | 优势:LPU 极速转写;限制:20 RPM / 2000 RPD,音频时长限流 |  |

#### Embedding 模型

> 向量化 / 检索

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | 1 万 Neurons/日 | 优势:边缘低延迟;限制:每日额度小 |  |

#### DeepSeek R1 / V3

> 深度推理模型 / 通用旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | R1 蒸馏版,1 万 Neurons/日 | 优势:边缘节点低延迟、每日免费;限制:仅蒸馏版非原版、额度小 |  |
| [OpenRouter](https://openrouter.ai) | `:free` 名单轮换,可能不含 | 优势:一站式聚合、OpenAI 兼容;限制:免费仅 50 次/天($10 后 1000),名单随时轮换 |  |
| ~~[魔搭 ModelScope](https://modelscope.cn)~~ | ⚠️ 已不在目录（2026-11-12） | ⚠️ 2026-11-12 实测 38 款目录中已无 `deepseek-ai/DeepSeek-R1`；原「约 200 次/日」作废 | 质量较低 |

> ⚠️ **DeepSeek R1 / V3 已不在 NVIDIA NIM**：2026-09-11 起从 NIM 模型列表移除；2026-09-27 复测，NIM 上的 DeepSeek 只剩 `deepseek-ai/deepseek-v4.1-flash` 与 `deepseek-coder-6.7b-instruct`，V4 Flash 0731、V4 Pro 0813 均已下架。

#### DeepSeek R2

> 新一代通用模型

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [火山方舟](https://console.volcengine.com/ark) | 协作奖励计划免费额度内(每日 200 万 token) | 优势:每日 200 万 token 大额免费;限制:需注册火山引擎并实名,额度以控制台为准 |  |


## 免费渠道一览

### 海外官方免费层

#### NVIDIA NIM

- **官网**：https://build.nvidia.com
- **免费形式**：永久免费层（**不限 token / 无积分额度**，40 RPM 全站共享，无每日上限）
- **网页说明**：官网称「100+ 模型免费调用」——NVIDIA 托管的推理端点，注册即可用，无需信用卡。⚠️ **机制已变更：旧的「约 1,000 积分」额度制已作废**，官方账号验证弹窗现写明 *"Unlimited API requests without daily limits"*，即不再有 token 额度上限，**唯一上限是约 40 RPM / key**（免费档无官方提额通道）
- **免费模型**：**`deepseek-ai/deepseek-v4.1-flash`**、**`z-ai/glm-5.3-flash`**、`moonshotai/kimi-k2.6`、`google/gemma-4-31b-it`、`nvidia/nemotron-3-ultra-550b-a55b` / `nemotron-3-super-120b-a12b` / `nemotron-3.5-lightning-30b-a3b`、`openai/gpt-oss-20b`、`mistralai/mistral-large` / `mistral-large-2-instruct` / `mistral-large-4-1t-a52b`、`poolside/laguna-xs-2.1`、`minimaxai/minimax-m3.1-flash`、`stepfun-ai/step-5-preview` 等（以 `/v1/models` 实测为准；⚠️ 2026-11-12 复核：**`z-ai/glm-5.3` 非 flash 版已不在列**；V4 Flash 0731、V4 Pro 0813、`moonshotai/kimi-k3` 仍均已下架）
- **接入**：`https://integrate.api.nvidia.com/v1`（OpenAI 兼容）
- **注册门槛**：**必须短信验证手机号**（API Key 页会弹「We'll need to verify your phone number」，未验证不发 key），⚠️ 部分国家/地区号段不在支持列表，无法注册；NVIDIA 明确虚拟号与借用 SIM 违反条款、可能封号
- **状态**：Active — 核实于 2026-11-12（实测 `/v1/models` 返回 **84 个模型**，较 10-24 的 85 个净减 1 个）。本期变化：❌ `z-ai/glm-5.3`（非 flash）退出，GLM 侧只剩 `z-ai/glm-5.3-flash`；✅ `minimaxai/minimax-m3.1-flash`、`stepfun-ai/step-5-preview` 仍在列，`mistralai/mistral-large-4-1t-a52b`、`meta/muse-glimmer-30b` 等在列；❌ `moonshotai/kimi-k3` 仍未回归。DeepSeek 侧仍是 `deepseek-ai/deepseek-v4.1-flash` 与 `deepseek-coder-6.7b-instruct` 两款，**V4 Flash / V4 Pro 在 NIM 已无免费档**；Qwen / Ling 仍不在列，GLM 5.2 / 5.1 / 4.7 未回归。⚠️ 数量变化不代表阵容不变，务必逐款核对模型 ID

#### Google AI Studio

- **官网**：https://aistudio.google.com
- **免费形式**：永久免费层（按天重置）
- **网页说明**：Google 官方 AI 开发平台，免费层提供 Gemini 系列模型 API 调用
- **免费模型**：Gemini 2.5 Pro（免费档 **5 RPM / 50 RPD / 1M TPM**，仅够试用、trial-only）、2.5 Flash（15 RPM / 1,500 RPD）、Flash-Lite（30 RPM / 1,500 RPD）、Gemini 3.x Flash（预览，限流更严）；⚠️ **2.5 Pro 仍在免费层**（与旧文档「2026-04-01 移出」相反），只是免费档额度极低；⚠️ 2025-12 起免费配额已被大幅削减，高峰时段实际可用量远低于标称（社区实测 Flash 高峰仅约 20 次/日）
- **接入**：`https://generativelanguage.googleapis.com/v1beta`（原生 SDK 亦可）
- **状态**：Active — 核实于 2026-08-31

#### Groq

- **官网**：https://console.groq.com
- **免费形式**：永久免费层（按天重置，按模型独立计限）
- **网页说明**：官网主打「极速推理」（LPU 硬件，700+ token/秒），开发者免费层无需绑卡
- **免费模型**：GPT-OSS 120B / 20B、Qwen3.6-27B、Qwen3.8-27B、Groq Compound、Whisper 等（⚠️ Llama 3.x、Qwen3 32B、Kimi K2 已于 2026 年 6-8 月从免费层下线）
- **接入**：`https://api.groq.com/openai/v1`
- **状态**：Active — 核实于 2026-09-02

#### ~~Mistral La Plateforme~~（免费 API 层已取消）

- **官网**：https://console.mistral.ai
- **免费形式**：~~永久免费层（约 10 亿 token/月，Experiment 计划）~~ ⚠️ **免费 API 配额已取消**（2026-09-01 生效）：免费计划现仅含 Le Chat / Vibe 消息额度与 $10/月 API credits（需订阅），不再提供免费 API 调用配额
- **网页说明**：Mistral 官方平台；旧 Experiment 层（约 10 亿 token/月）已重构，免费层不再适合 API 调用
- **免费模型**：~~Mistral Large / Small、Codestral、Embedding 模型~~（API 侧已无免费配额）
- **接入**：`https://api.mistral.ai/v1`（仅付费）
- **状态**：~~Active — 核实于 2026-08-31~~ **已失效（2026-09-07）** —— 免费 API 层取消，不再符合收录标准，条目保留备查

#### Cloudflare Workers AI

- **官网**：https://developers.cloudflare.com/workers-ai
- **免费形式**：永久免费层（每日 10000 Neurons）
- **网页说明**：Cloudflare 边缘节点推理，官网称免费额度按日发放
- **免费模型**：Llama 3.3 70B（蒸馏版）、Mistral Small、Embedding、DeepSeek R1 蒸馏版等
- **接入**：REST 调用（`wrangler` 绑定亦可）
- **状态**：Active — 核实于 2026-08-31

#### Hugging Face

- **官网**：https://huggingface.co
- **免费形式**：每月 **$0.10** 免费推理额度（Inference Providers 路由计费，按上游原价零加价），超额后按量付费（免费用户到额度即停、hard stop，需购 credits 才继续）
- **网页说明**：最大的开源模型库，提供 Inference Providers 路由推理；所有用户每月获 $0.10 免费额度用于试用，超出部分按量计费
- **免费模型**：10 万+ 社区与官方模型（DeepSeek V4 Flash 等可按路由调用，但消耗的是免费额度，额度耗尽即停）
- **接入**：`https://router.huggingface.co/hf-inference`（`InferenceClient` / REST，鉴权用 HF User Access Token）
- **状态**：Active — 核实于 2026-09-14（⚠️ **免费额度已大幅缩水**：2026 年起免费用户仅 $0.10/月推理额度，不再是「永久免费共享端点」；PRO $9/月也仅 $2/月额度。免费档只够极小实验，生产请购 credits）

#### AMD Token Factory（Radeon Cloud）

- **官网**：https://developer.amd.com.cn/radeon/tokenfactory
- **免费形式**：每日约 $10 美元等值额度，每日重置（不过夜）
- **网页说明**：AMD Radeon Cloud 官方推理平台，注册登录领取每日免费额度，OpenAI 兼容
- **免费模型**：DeepSeek V4 Flash 0731（Free）、MiniCPM5-1B（Free）、GLM-5.3-Flash（限时，ZZ.ai）、Qwen3.8-Flash-Next（限时，AMD GPU Cloud）
- **接入**：`https://developer.amd.com.cn/radeon/api/v1`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-09-02（TTFT 偏高，首字延迟约 22 秒）

#### Ollama Cloud

- **官网**：[https://ollama.com](https://ollama.com)（[定价页](https://ollama.com/pricing) · [云模型目录](https://ollama.com/search?c=cloud)）
- **免费形式**：Free 档 $0，含少量 starter 用量额度（按月刷新、不结转，**具体数额未公开**），**仅覆盖「starter 模型」子集**
- **网页说明**：官网定价页 Free 档明确写 "Run models locally / Starter usage credits included / **Includes access to starter models** / Add credits to unlock **all** models"——即**免费档只能调 starter 子集，旗舰模型需购买 credits 解锁**；Pro $20/月（含 $60 credits）、Max $100/月（含 $300 credits，10 并发）
- **可用模型（需付费 credits 解锁）**：云目录 2026-11-12 实测 **23 款**：glm-5.3-flash、deepseek-v4.1-flash（含 `:1017`）、deepseek-v4-pro、gpt-oss:20b / 120b、mimo-v2.6-flash / pro、kimi-k2.6 / k2.7-code / k3 / k3.1-pro、muse-spark-open、glm-5.2 / 5.3、minimax-m3 / m3.1-flash、mistral-large-4、gemma4:31b、nemotron-3-super / ultra、clef:27b、beam（**定价页全部按量标价、无一款 $0**）
- **接入**：`https://ollama.com/api/chat`（Ollama API；API Key：[https://ollama.com/settings/keys](https://ollama.com/settings/keys)，**未带 key 返回 `{"error":"Unauthorized"}`**）
- **状态**：Active（**未列入任何模型免费索引**）— 2026-11-12 复核：云目录从 20 款增至 **23 款**，但结论不变——`/api/tags` 只是云目录、不等于免费清单；定价页 23 款全部按量标价、无一为 $0，实测无 API Key 调 `beam` 返 401 `Unauthorized`；FAQ 明示 Free 档仅含"a starter amount of usage for a smaller set of starter models"，而 **starter 清单从未公布**，故本仓库不把任何具体模型记为「Ollama Cloud 免费」。Free 档 1 并发，额度按月从注册日重置、不结转

> ℹ️ **本渠道严格说只部分符合收录标准**：免费额度存在但未公开数额，且**官方从未公布 starter 模型清单**，读者需在 [设置页](https://ollama.com/settings) 查看自己的可用模型。多数读者登录后在 Downloads 页只看到本地模型下载入口，属于正常——**云模型的免费额度不体现在下载页**。

### 中国平台


#### 美团 LongCat

- **官网**：[https://longcat.ai](https://longcat.ai)（[开放平台文档](https://longcat.chat/platform/docs/zh/)）
- **免费形式**：注册赠送免费额度（每日额度 + 一次性资源包，具体数额以控制台「资源包 / 用量信息」页为准；第三方资料显示普通账号约 50 万 token/日、可申请提额）
- **网页说明**：美团官方大模型开放平台（LongCat-2.0，1.6 万亿参数 MoE 架构）；缓存命中不消耗额度
- **免费模型**：LongCat-2.0（官方文档当前唯一列出的模型：1M 上下文 / 最大输出 128K token，支持 OpenAI / Anthropic 双格式）
- **接入**：`https://api.longcat.chat/openai`（OpenAI 兼容）或 `https://api.longcat.chat/anthropic`（Anthropic 兼容），注册后在 [API Keys 页](https://longcat.chat/platform/api_keys)创建
- **状态**：Active — 核实于 2026-09-07（限流时返回 429，官方建议指数退避重试；免费额度数额官方未明示，以控制台为准）

#### 硅基流动 SiliconFlow

- **官网**：https://cloud.siliconflow.cn
- **免费形式**：永久免费（指定模型 ¥0 列表，动态调整）
- **网页说明**：官网模型列表中标 ¥0 的即永久免费，注册即用
- **免费模型**：Qwen3-8B、GLM-4-9B 等 9B 及以下小模型（不含 DeepSeek R1/V3 等大模型）
- **接入**：`https://api.siliconflow.cn/v1`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-08-31（需实名）

#### 智谱 AI

- **官网**：https://open.bigmodel.cn
- **免费形式**：永久免费模型（GLM-4.7-Flash 完全免费，仅速率限制）
- **网页说明**：智谱官方开放平台，官网标注 GLM-4.7-Flash 永久免费
- **免费模型**：GLM-4.7-Flash（200K 上下文，中文能力突出）
- **接入**：`https://open.bigmodel.cn/api/paas/v4`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-08-31（需实名）

#### 火山引擎方舟（字节豆包）

- **官网**：https://console.volcengine.com/ark
- **免费形式**：永久免费层（协作奖励计划，每日 200 万 token，零点刷新；Doubao-Pro 等中高档模型需付费）
- **网页说明**：字节火山引擎的模型服务平台，免费额度按日发放
- **免费模型**：Doubao-Lite（免费）、DeepSeek R2 / V3 等（免费额度内，以控制台为准）
- **接入**：`https://ark.cn-beijing.volces.com/api/v3`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-08-31（需手机号实名）

#### ~~腾讯混元~~（旧平台 9/30 停服，新平台无免费模型）

- **官网**：https://cloud.tencent.com/product/hunyuan
- **免费形式**：~~永久免费模型（混元-Lite 完全免费，仅速率限制）~~ ⚠️ **免费模型随旧平台下线**：腾讯云大模型旧平台（含混元大模型旧版入口）2026-06-30 起停止售卖、无法新建 API Key，**2026-09-30 00:00 全面停服**；新平台 TokenHub 的模型列表中**无 hunyuan-lite**，官方推荐替代为 Hy3 preview（付费，新人有 90 天免费体验额度）
- **网页说明**：腾讯云混元大模型；存量老 API Key 在 9/30 前仍可调用，之后彻底失效
- **免费模型**：~~混元-Lite（256K 上下文）~~（随旧平台 2026-09-30 停服失效）
- **接入**：旧平台见官方文档；新平台 TokenHub 端点为 `https://api.hunyuan.cloud.tencent.com/v1`（需新建 API Key）
- **状态**：~~Active — 核实于 2026-08-31~~ **已失效（2026-09-30 旧平台全面停服）** —— hunyuan-lite 永久免费已终结，不再符合收录标准，条目保留备查（2026-11-12 复核维持）

#### 百度千帆

- **官网**：https://cloud.baidu.com/product/wenxinworkshop
- **免费形式**：永久免费模型（ERNIE-Speed/Lite 完全免费，有速率限制）
- **网页说明**：百度智能云千帆平台，官网标注 ERNIE-Speed / ERNIE-Lite 永久免费
- **免费模型**：ERNIE-Speed-128K、ERNIE-Lite（DeepSeek V4 是否在免费额度内**未能确认**，不收录）
- **接入**：`https://qianfan.baidubce.com/v2`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-08-31（需实名）

#### 讯飞星火

- **官网**：https://xinghuo.xfyun.cn/sparkapi
- **免费形式**：永久免费模型（Spark Lite 无限 Token，仅限速 QPS 2）
- **网页说明**：讯飞官方开放平台；Spark Lite 个人实名认证后永久免费、不限 Token
- **免费模型**：Spark Lite（轻量基础版，无限 Token，QPS 2）
- **接入**：`https://spark-api-open.xf-yun.com/v1`（OpenAI 兼容；APIKey/APISecret 鉴权，密钥在 [控制台](https://xinghuo.xfyun.cn/sparkapi) 申请）
- **状态**：Active — 核实于 2026-09-05（需实名）

#### 魔搭 ModelScope（阿里）

- **官网**：https://modelscope.cn
- **免费形式**：永久免费（所有注册用户免费推理，每日总 2000 次，单模型 100~500 次/日不等）
- **网页说明**：阿里达摩院开源模型社区，官网明确「所有注册用户均可免费推理」；DeepSeek-R1 约 200 次/日
- **免费模型**：2026-11-12 实测 `api-inference` 目录 **38 款**：`deepseek-ai/DeepSeek-V4.1-Flash` / `DeepSeek-V4.1-Flash-1017` / `DeepSeek-V4-Flash-0731` / `DeepSeek-V4-Pro`、`stepfun-ai/Step-3.7-Flash` / `Step-5-Preview`、`Qwen/Qwen3.5-122B-A10B` / `Qwen3.5-397B-A17B` / `Qwen3.8-Flash-Next`、`MiniMax/MiniMax-M3`、`ZhipuAI/GLM-4.7-Flash` / `GLM-5.2`、`moonshotai/Kimi-K3.1-Pro` 等；❌ **Qwen3 Coder 480B、Qwen3 235B、Qwen2.5 72B、DeepSeek-R1 均不在当前目录**
- **接入**：`https://api-inference.modelscope.cn/v1`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-11-12（⚠️ **本条按 `api-inference` 的 `/v1/models` 实测为准，当日返回 38 款**，较 10-24 的 37 款净增 1 款）：✅ 新进 `stepfun-ai/Step-3.7-Flash`（此前该模型被记为「无免费 API」，现已更正）、`ZhipuAI/GLM-4.7-Flash`、`moonshotai/Kimi-K3.1-Pro` 等；❌ `Qwen3 Coder 480B`、`Qwen3 235B`、`Qwen2.5 72B`、`DeepSeek-R1` 仍不在目录。需阿里云账号 + 实名
- **⚠️ 免费质量较低**：单模型仅 100~500 次/日，与全站共享每日 2000 次总量（高峰可能被挤占）；仅限个人学习与非商业用途；共享算力排队，无 SLA

#### 书生·端砚 墨点计划（Intern InkStone Token Plan）

- **官网**：https://discovery.intern-ai.org.cn · Token Plan：https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0
- **免费形式**：测试期每月自动赠送「墨点」额度，按墨点折算 tokens（**1 墨点最多可抵 50,000,000 tokens，以 DeepSeek-V4-Flash 为例**——官网原文写作 `5000,0000`，有排版笔误，正确值为 5,000 万）
- **网页说明**：上海人工智能实验室 2026 浦江创新论坛发布的科研模型计划，官方新闻称「测试期间，每位用户每月可获免费 Token」；⚠️ **官方从未公布每月赠送多少墨点**，实际余额需注册后在 Token Plan 页查看（未登录时全部渲染为 `--`）
- **免费模型**：⚠️ 官方页面仅明示 DeepSeek-V4-Flash 一个换算基准；完整模型清单需登录后在「模型列表」页查看
- **接入**：`https://discovery-api.intern-ai.org.cn/v1`（OpenAI 兼容）；同时支持 Anthropic 协议，Base URL 为 `https://discovery-api.intern-ai.org.cn`（不带 `/v1`）——**这一点在同类免费渠道里少见**
- **状态**：Active（测试期免费，规则可能调整）— 核实于 2026-09-30（`discovery-api.intern-ai.org.cn/v1/models` 无 key 返 401 `invalid_api_key`，端点确认存在；需手机号注册，免绑卡）
- **⚠️ 额度不可提现**：墨点仅站内消耗，不能兑换现金或转出；「1 墨点抵 50,000,000」是**上限**而非固定值，调用更贵的模型消耗更快
- **限流**：RPM + TPM + 墨点余额**三重限制**，且**全部 API Key 共享账户额度**（非每个 Key 独立配额）；单账号最多 10 个 API Key，Key 默认 6 个月有效期
- **⚠️ 定位差异**：科研向平台（生命科学、材料、半导体、核聚变、气象），非通用聊天 API 网关；提额联系 `tokenplan@pjlab.org.cn`

### 聚合与网关

#### Vercel AI Gateway

- **官网**：[https://vercel.com/ai-gateway](https://vercel.com/ai-gateway)（[定价页](https://vercel.com/docs/ai-gateway/pricing) · [入门文档](https://vercel.com/docs/ai-gateway/getting-started)）
- **免费形式**：免费档含 **每月 $5 额度**（首次发出 AI Gateway 请求时开始计时），可用范围限 **Free Tier eligible 模型子集**，每模型限流低于付费档；⚠️ **Jev 的限时促销已于 2026-09-25 结束，现按量计费**
- **网页说明**：Vercel 官方托管网关，官网称「no markup and no platform fee on tokens」——按上游原价转发、零加价；免费档原文「**To use free AI Gateway Credits, add a valid payment method to your team.**」（用免费额度**必须先绑定有效支付方式**）
- **免费模型**：~~`typesafe-ai/jev`（限时促销已结束）~~ + **零价路由（不消耗 $5 额度）**——2026-11-12 实测目录 507 款中定价 input/output 双端为 $0 的 **11 款**：`reflection/beam` / `reflection/beam-free`、`nvidia/nemotron-3.5-lightning-free`、`stealth/glyph-cluster`（匿名模型，详见[匿名模型](#匿名模型stealth)）、`humansand/ampersand-v0.1`，以及 6 款**语音转写**模型（`elevenlabs/scribe-v2`、`microsoft/mai-transcribe-2`、`mistral/voxtral-mini-transcribe-3` / `voxtral-small-transcribe-3`、`openai/gpt-transcribe`、`spacexai/grok-stt`）。⚠️ **`minimax/minimax-m3.1-flash` 已转计费**（$0.15/$0.6 per 1M）、`convaiinnovations/laya` 输入已非 $0、`poolside/laguna-s-2.1-free` 已下架；官方仍未公布完整白名单，零价路由与「$5 免费额度」是两套并行机制
- **接入**：`https://ai-gateway.vercel.sh/v1`（OpenAI 兼容）；⚠️ **Jev 必须走 Evaluation 端点 `POST /v1/evaluate`**，请求体为 `{model, state, questions}`，**不能用 `chat/completions`**（2026-09-20 实测：`/v1/evaluate` 带 Jev 模型返回 `Authentication failed` 即端点正确、缺鉴权，而 `/v1/evaluations`、`/v1/decisions` 均返回 404 不存在）
- **状态**：Active（免费档 $5/月 + 零价路由）— 核实于 2026-11-12（①**Jev 促销已于 2026-09-25 结束**，恢复 TypeSafe 原价，Jev 已移出免费索引；②免费额度需先绑支付方式，但不充值就不扣费；③**一旦主动购买 credits，账号转入付费档、每月 $5 免费额度永久失效**；④免费档限流低于付费档，超限 429；⑤**零价路由不占用 $5 额度**，但同样限时——活动结束即转计费或停服，本期 MiniMax M3.1 Flash 就是实例）

#### OpenRouter

- **官网**：https://openrouter.ai
- **免费形式**：永久免费（`:free` 模型 50 次/天，20 次/分钟；累计充值 $10 后升至 1000 次/天）
- **网页说明**：多模型聚合路由，官网提供 `:free` 免费模型清单，`openrouter/free` 可自动路由（⚠️ 网传「200 次/天」为过时信息，官方限速页现行标准为 50/1000）
- **免费模型**：2026-11-12 实测 **16 个定价为 0 的路由**（其中 2 个是 Google Lyria 音乐生成、`openrouter/free` 是自动路由，**实际可免费用文本 `:free` 模型 13 个**）：`baidu/ernie-5.5-flash-preview:free`、`thinkingmachines/inkling-2-small:free`、`liquid/lfm-3-1.7b:free`、`recursive/flint-v1.0:free`、`nvidia/nemotron-3-ultra-550b-a55b:free` / `nemotron-3.5-lightning:free` / `nemotron-3.5-super-vl:free` / `nemotron-3-nano-omni-30b-a3b-reasoning:free`、`cohere/north-mini-code:free`、`dots-studio/dots-3-note-preview:free`、`liquid/lfm-2.5-2.6b:free`、`google/gemma-4-26b-a4b-it:free` / `gemma-4-31b-it:free`（**名单随时轮换**——DeepSeek / GLM / Qwen / MiniMax / Kimi / Ling 均不在免费名单，用前先查 `openrouter.ai/models?max_price=0`）
- **接入**：`https://openrouter.ai/api/v1`（绝大多数模型名需带 `:free` 后缀；⚠️ 例外是 `stealth/space-bunny-alpha`，它没有后缀且定价已为 0，加了后缀反而 404，详见[匿名模型](#匿名模型stealth)）
- **状态**：Active — 核实于 2026-11-12（目录 **468 个模型**、定价为 0 的 **16 个路由**，较 10-24 的 20 个再缩 4 个）：✅ 新增 `baidu/ernie-5.5-flash-preview:free`、`thinkingmachines/inkling-2-small:free`、`liquid/lfm-3-1.7b:free`；❌ 退出 `thinkingmachines/inkling` / `inkling-small`、`nvidia/nemotron-3-super-120b-a12b:free`（回归仅 19 天）、`nvidia/nemotron-3.5-content-safety:free`、`xingchen-agi/xing4.0-29b-a4b:free`、`poolside/laguna-s-2.1` / `laguna-xs-2.1`。每日额度 50 次，充值 $10 后 1000 次。⚠️ 免费池一周可换 4 款，「发布当天进免费池」是冷启动信号而非长期承诺，务必留 fallback

#### Kilo Gateway

- **官网**：https://kilo.ai（Kilo Code 官方网关；[文档](https://kilo.ai/docs)）
- **免费形式**：✅ **官方明确支持匿名调用**——文档原文「The gateway allows unauthenticated access for free models only. Anonymous requests are identified by IP address and are subject to rate limiting (**200 requests per hour per IP**)」，即**不注册、不拿 key 也能调所有 `:free` 模型**
- **网页说明**：代理 OpenRouter / NVIDIA / Poolside / Recursive 等上游的免费池，一个端点覆盖多家；付费模型必须登录（实测返 401 `PAID_MODEL_AUTH_REQUIRED`），免费模型免鉴权
- **免费模型**：2026-11-12 实测 `/v1/models` **383 个模型**、目录字段 `isFree: true` 的 **12 款**：`nvidia/nemotron-3-ultra-550b-a55b:free`、`nvidia/nemotron-3.5-lightning:free`、`nvidia/nemotron-3.5-super-vl:free`、`nvidia/nemotron-3-nano-omni-30b-a3b-reasoning:free`、`baidu/ernie-5.5-flash-preview:free`、`thinkingmachines/inkling-2-small:free`、`liquid/lfm-3-1.7b:free`、`dots-studio/dots-3-note-preview:free`、`cohere/north-mini-code:free`、`stealth/glyph-cluster`（匿名模型，详见[匿名模型](#匿名模型stealth)）、`openrouter/free`、`kilo-auto/free`
- **接入**：`https://api.kilo.ai/api/gateway/v1`（OpenAI 兼容；`https://api.kilo.ai/api/gateway` 同样 200）
- **状态**：Active — 核实于 2026-11-12（✅ **仍是本仓库唯一「免注册、免 key 实测 200」的渠道**：`baidu/ernie-5.5-flash-preview:free`、`nvidia/nemotron-3.5-lightning:free`、`stealth/glyph-cluster` 免 key POST 均返 200；付费款返 401 `PAID_MODEL_AUTH_REQUIRED`；官方文档仍明文写 200 次/小时/IP 匿名限额）。⚠️ 免费池大幅换血：`reflection/beam-free`（**已 404 模型不存在**）、`recursive/flint-v1.0:free`、`poolside/laguna-*:free`、`liquid/lfm-2.5-2.6b:free`、`nvidia/nemotron-3-super-120b-a12b:free` 均已退出；`thinkingmachines/inkling-2-small:free` 实测返 403「not available in your region」。⚠️ **12 款免费款的 `mayTrainOnYourPrompts` 全部为 `true`**，别传敏感数据；限流按出口 IP 计，共用出口会互相挤占

#### AIHubMix

- **官网**：[https://aihubmix.com](https://aihubmix.com)（[免费模型专页](https://aihubmix.com/models/free)）
- **免费形式**：免费模型档（注册送 10 次试用、不过期；一次性充值 $1 起即永久转每日配额：100 次/日 · 1M token/日，每日重置）
- **网页说明**：官网标注「56 free models — no credit card required」——平台补贴推理成本，免费模型输入输出均 $0
- **免费模型**：glm-4.7-flash-free、hy3-free、minimax-m3-free、k2.6-code-preview-free、gpt-oss-20b-free、nemotron-3-ultra/super-free、gemma-4-31b-it-free、mimo-v2.5(-pro)-free、coding-glm-5.3-free、gpt-5.5-free、gemini-3.8-flash-free 等 56 个
- **接入**：`https://aihubmix.com/v1`（兼容 Chat Completions / Messages / Responses 三协议）
- **状态**：Active — 核实于 2026-09-05（充值 $1 才转每日配额；全免费模型共享额度池）

#### OpenCode Zen

- **官网**：[https://opencode.ai/zen](https://opencode.ai/zen)（[定价页](https://opencode.ai/docs/zen/)）
- **免费形式**：限时免费模型（Beam、Flint 40B、MiMo-V2.6-Flash、Nemotron 3.5 Super VL / Lightning、DeepSeek V4.1 Flash、GLM-5.3 Flash、MiniMax M3.1 Flash、LongCat 2.5、Iceman、Inkling 2 Small —— 输入/输出/缓存读写全 $0；名单每两周就换一批）
- **网页说明**：OpenCode 官方模型网关，官网定价页将上述免费款明确标注为 Free，并说明"限时免费、用于收集反馈改进模型"；**并非整个平台免费**——DeepSeek / GLM / Kimi / Qwen 的正式版均为按量付费
- **免费模型**：2026-11-12 `/v1/models` 实测仍共 **85 个模型**、但 `-free` 款已增至 **11 款**（另保留 `big-pickle` 免后缀免费款）：`beam-free`、`flint-40b-free`、`mimo-v2.6-flash-free`、`nemotron-3.5-super-vl-free`、`nemotron-3.5-lightning-free`、`deepseek-v4.1-flash-free`、`glm-5.3-flash-free`、`minimax-m3.1-flash-free`、`longcat-2.5-free`、`iceman-free`、`inkling-2-small-free`。⚠️ **本期换血 4 进 1 出**：新增 minimax-m3.1-flash / longcat-2.5 / iceman / inkling-2-small，退出 `jev-1.13-free`；`space-bunny-free` 仍不在目录
- **接入**：`https://opencode.ai/zen/v1`（OpenAI 兼容；部分模型走 `/messages` Anthropic 协议或 `/responses`）
- **状态**：Active（限时免费，但**外部不可调**）— 核实于 2026-11-12（✅ 目录 85 个模型、`-free` 款 11 个；⚠️ **外部 endpoint 依旧调不通**：`beam-free` 免 key 返 403 `RegionError`、`iceman-free` 返 429 `FreeUsageLimitError`（"Free models work in OpenCode"），与此前 403 `FreeTierError` 属同一客户端绑定机制、只是错误码换了一层；带有效 key 同样 403。实务上 Zen 免费层只对 OpenCode 客户端用户有意义）

#### OrcaRouter

- **官网**：[https://www.orcarouter.ai](https://www.orcarouter.ai)（[文档](https://docs.orcarouter.ai)）
- **免费形式**：免费池按 workspace 限流（额度不公开）；**付费侧 0% token 加价**（按上游官方价转发）
- **网页说明**：OpenAI 兼容的 LLM 路由网关，200+ 模型统一端点；免费模型是「目录模型套一层 free ID」，权重能力与付费版一致，但跑在独立限流池里——**免费池打满不会自动降级到付费版**
- **免费模型**：2026-11-12 复测 `/v1/models` **215 个模型**，免费款 **6 个**：`orcarouter/free`（智能路由免费池）、`z-ai/glm-5.3-flash-free`、`deepseek/deepseek-v4-flash-free`、`deepseek/deepseek-v4.1-flash-free`、`tencent/hy3-free`、`tencent/hy4-preview-free`（其中 `deepseek-v4.1-flash-free` 的 pricing 四端皆为 0，其余多数只标 `request` 为 0）；❌ `orca/orcaverify-text1.0-free` 已退出目录
- **接入**：`https://api.orcarouter.ai/v1`（OpenAI 兼容，注册免卡）
- **状态**：Active（限流）— 核实于 2026-11-12（目录 215 款 / 6 个免费路由；2026-09-07 免费默认模型由 Qwen3.8-27B 换成 GLM-5.3 Flash：质量分 4→8、上下文 262K→1M，但 TTFT 1.96s→7.66s、吞吐 196→74 tok/s；⚠️ 未充值账号日额度更小，`429 + Retry-After` = 限流、无 header 的 429 = prompt 超长；官方明示为 best-effort，非生产容量）

#### Onomeo

- **官网**：https://onomeo.com/zh（[模型页](https://onomeo.com/zh/models)）
- **免费形式**：⚠️ **机制已变、待核实（2026-11-12）**：原「签到领额度 + 问卷收入覆盖成本」的说法已无法在官网复现——`/zh/models` 与首页均无「签到 / 免费额度」文案，内嵌配置 `survey: false`、`invite.days: 0`、`invite.calls: 0`。本条目下方 2026-09-27 的额度与成本数据**全部按历史快照处理，不要据此估算可调次数**
- **付费档**：2026-11-12 从 `/zh/models` 内嵌配置读出的现行规则：`premium.models` 扩到 **28 个 ID**（含别名，新增 `gpt-6.1-terra` / `gpt-6.1-sol`、`claude-fable-5.2`、`kimi-k3.1-pro`、`glm-5.3-flash`、`gemini-3.8-flash`、`mimo-v2.6-*`、`deepseek-v4.1-flash-1017`、`hy4-preview` 等），`premium.dailyCap: 10000`、`premium.buyersOnly: true`、`trialCalls: 0`；购买档 `$5 / 3,000,000 credits 每月`。⚠️ 与旧规则「未购买账号仍可每天消耗 5 万额度」相比是**收紧**：premium 款现在标为仅购买者可用
- **网页说明**：中文聚合网关，OpenAI 兼容；2026-11-12 实测 `/zh/models` 已改版为「模型排行榜」（展示每百万输出 token 参考价与可用率），内嵌 `rows` 含 71 条记录（去重约 28 款模型），模型 ID 大幅换新
- **模型成本（2026-11-12 内嵌 `rows` 实测，仅供相对比较）**：`deepseek-flash` 2,368、`hy4-preview` 705、`glm-5.3` 845、`kimi-k3` 1,560、`claude-haiku-5.5` 1,770、`gpt-6.1-sol` 3,348、`gemini-3.8-flash` 3,755、`deepseek-v4.1-flash-1017` 5,609、`gpt-6-luna` 7,168、`glm-5.3-flash` 7,701、`gpt-6.1-terra` 18,859、`claude-sonnet-5.5` 45,615、`claude-opus-5.5` 57,811、`grok-4.7` 140,810、`qwen3.8-max` 396,776（额度/次，`null` = 暂无采样）。⚠️ 旧表里的 `deepseek-v4.1-flash` 8,409、`z-ai/glm-5.3-flash-free` 3,149、`gpt-6-astra` 3,948 等 ID 已不存在于当前目录
- **接入**：`https://onomeo.com/v1`（OpenAI 兼容；2026-09-22 实测无 key 调用返回 401 `bad_key`，国内直连可通；2026-11-12 复核端点未变）
- **状态**：⚠️ **机制待核实（2026-11-12）** — 站点改版后签到/问卷文案下线、premium 改为 `buyersOnly`，**当前是否仍存在无需付费的调用额度，本仓库无法证实**；2026-11-12 抓到的其他配置：`perMinute: 60`、`perAccountWindowMax: 30`、`perIpWindowMax: 60`、`windowMinutes: 300`（均较 9-27 记录的 60 / 120 收紧）、`training` 大量标 `trains`。在官方重新明示免费方式前，**建议不要把 Onomeo 当作稳定免费渠道**，索引中引用它的行请一并留意

#### Chutes ~~（已失效）~~

~~已失效（2026-11-12 再复核：**目录 19 款、全部标价、无一为 $0**；其中 11 款为 `-TEE` 变体，另有 `deepseek-ai/DeepSeek-V4.1-Flash-1017`、`Qwen/Qwen3.8-Max-0902`、`zai-org/GLM-5.3`、`tencent/Hy4` 等非 TEE 款，同样按量计费——DeepSeek V4 Flash 0731 $0.039/$1.25、Kimi K3 见目录）：`llm.chutes.ai/v1/models` 未发现任何免费端点；内容保留备查。~~

- ~~**官网**：https://chutes.ai~~
- ~~**免费形式**：社区 GPU 免费端点（新模型发布后常短期免费）~~
- ~~**网页说明**：社区 GPU 市场，热门新模型上架初期提供免费调用~~
- ~~**免费模型**：新发布开源模型（DeepSeek V4 Flash 当前是否在免费名单**未确认**，未列入索引）~~
- ~~**接入**：见官方文档~~
- ~~**状态**：Active（额度随时可能下架）— 核实于 2026-09-02~~

### 限时免费

#### B.AI

- **官网**：https://b.ai · API 文档：https://b.ai/docs
- **免费形式**：~~限时免费（0 Credits）~~ **已结束** — 2026-09-16 17:00（新加坡时间）起全部模型转为最低 10% 折扣，平台已无任何 0 Credits 模型
- **网页说明**：AI Agent 基础设施平台；API 兼容 OpenAI / Anthropic 协议。免费档时间线（据官方公告页）：8/17 DeepSeek V4 Flash 免费 → 9/3 转阶梯折扣（高峰 5 折、空闲 2.5 折）；8/21 Hy3、8/24 MiMo-V2.5、8/29 GLM-5.3-Flash / Qwen3.8-Flash 免费 → 9/12 GLM-5.3-Flash 与 V4.1 Flash 转 10% 折扣 → **9/16 17:00 起 Qwen3.8-Flash / Hy3 / MiMo-V2.5 也转 10% 折扣，免费档彻底结束**
- **免费模型**：~~GLM-5.3-Flash（Ox Alpha）、Qwen3.8 Flash、Hy3、MiMo-V2.5~~（均已结束免费，现最低 10% 折扣）
- **接入**：`https://api.b.ai/v1`（国内访问不畅时用备用域名 `api.bankofai.io`，OpenAI 兼容）
- **状态**：**已失效（免费档 2026-09-16 结束）** — 核实于 2026-09-20（⚠️ 本仓库不再将其列为免费渠道；如未来重新开放免费档再评估收录）

#### Experiential Labs

- **官网**：[https://platform.experientiallabs.ai](https://platform.experientiallabs.ai)（YC 背景，自称「开源版 OpenRouter」）
- **免费形式**：限时免费（Promotional 档标 $0 输入/输出的模型仍在，但 Free plan 改为**每月有限 credits 额度，约 500 credits/月**，1 credit = 1 美分；超额即停、无自动转付费；新组织另送 welcome credits）
- **网页说明**：商业模式是「用免费流量换训练数据」——官方提供上传 traces 作为遥测的流程；免费层即获客投资，**额度随时可能收缩**
- **免费模型**：`Qwen3.8 27B free`（1M 上下文、192 tok/s、80.2% uptime）、`DeepSeek V4 Flash free`（1.05M、141 tok/s、100% uptime）、`GPT-5.6 Luna free`（1.05M、154 tok/s、97.5%）、`Claude Fable 5.1 free`（1M、86.9 tok/s、**72.5% uptime**）、`GPT-6 Astra free`（1.05M、88 tok/s、89%）——后两款原价均为 $10/$50（模型标 $0 但受每月约 500 credits 总额约束）
- **接入**：`https://api.experientiallabs.ai/v1`（OpenAI 兼容，需注册生成 key）
- **状态**：Active（限时）— 核实于 2026-09-14（⚠️ **免费层 uptime 偏低**：Claude Fable 5.1 仅 72.5%、TTFT 约 4.5 秒；**免费额度已收紧至约 500 credits/月**，额度耗尽返回错误且明确说明重试无效**；仅适合尝鲜，勿放入生产链路）

### 小型网关（谨慎）

> 以下新晋网关验证有限、免费额度随时可能关停或收费，**只适合原型验证，别托付生产负载**。

#### Token Harbor

- **官网**：https://tokenharbor.ai（[定价页](https://tokenharbor.ai/pricing)）
- **免费形式**：Free 档 $0/月，含每月免费额度（按 **4 周滚动**刷新，不过期结转）；另有 Agent Pass $1.99/月（首月 $0.99）
- **网页说明**：小型网关；官网定价页列 Free 档含 **DeepSeek V4 Flash、DeepSeek V4.1 Flash、MiMo V2.5** 三款，并称「Promotional models added over time」（免费名单会轮换）；注意免费请求可能被平台保存
- **免费模型**：DeepSeek V4 Flash、DeepSeek V4.1 Flash、MiMo V2.5
- **接入**：`https://tokenharbor.ai/v1`（OpenAI 兼容，注册后生成 API Key）
- **状态**：Active（小型网关，**⚠️ 中国大陆/香港/澳门不可用**）— 核实于 2026-09-12（⚠️ 实测该端点返回 `{"type":"region_blocked"}`，原文写明「Cannot serve requests from … **Mainland China, Hong Kong and Macau**」，故**国内读者需自备境外网络环境**，且官方要求关闭 VPN 重试——它只能看到连接出口国；⚠️ 免费额度**具体数额未公开**；免费档与付费 Pass 的额度**合并为一个池子**，订阅不会替换已有免费额度）

#### TokenRouter

- **官网**：[https://tokenrouter.com](https://tokenrouter.com)（[免费模型页](https://www.tokenrouter.com/models/qwen/qwen3.8-max-free/)）
- **免费形式**：qwen3.8-max-free 输入 / 输出均 $0；另有 deepseek-v4-pro-0813-free、nemotron-3-nano-omni-free 等（免费算力有限）
- **网页说明**：OpenAI 兼容的模型路由；官方模型页标注 qwen3.8-max-free 为 $0 in / $0 out；新模型上架初期常设免费档
- **免费模型**：Qwen3.8 Max、DeepSeek V4 Pro（0813-free）、Nemotron-3-Nano-Omni（以官网当前 $0 标注为准）
- **接入**：`https://api.tokenrouter.com/v1`（OpenAI 兼容，注册后生成 API Key）
- **状态**：Active（小型网关）— 核实于 2026-09-05（官方提示免费算力有限、不保证稳定性与并发；"旗舰白嫖"名额随时消失）

#### Empero

- **官网**：https://free.empero.org
- **免费形式**：完全免费、无需注册（API Key 任意填写，一般填 `free`）
- **网页说明**：德国独立 AI 实验室 EmperoAI 的社区免费端点；prompt 与响应会被记录（IP 哈希化）用于训练其开源模型，勿传隐私内容
- **免费模型**：glm-5.3-flash、qwen3.8-flash（即 Flash-Next）、Qwen3.8-27B-FP8 等（模型轮换频繁，以官网为准）
- **接入**：`https://free.empero.org/v1`（OpenAI 兼容，Key 任意）
- **状态**：⚠️ **端点维护中（2026-11-12）** — 官网首页现挂 "MAINTENANCE / We are preparing the free endpoint for Free API. Quick restart in progress"，`/v1/models` 与 `/v1/chat/completions` 均返 503 `maintenance`（"The endpoint is offline for now and will be back soon"），**当前完全不可调用**；官方让关注 X 账号等重开，未给恢复时间。此前列的「经常 `upstream_down`」已升级为整站停机，暂按不可用对待

#### BazaarLink

- **官网**：https://bazaarlink.ai（[免费模型规则](https://bazaarlink.ai/docs/api#free-models)）
- **免费形式**：免费模型档（`auto:free` 智能路由免费池 + `qwen/qwen3.7-flash:free` + `deepseek/deepseek-v4-flash-0731free:free`，输入/输出均 $0，限流使用、免绑卡注册）
- **网页说明**：台湾 LLM 网关，官网列「免費模型 1」并说明「免費額度，超出後自動轉為付費計價」；`auto:free` 会自动路由到当前最合适的免费模型
- **免费模型**：2026-11-12 实测 `/v1/models` **125 个模型**、定价双端为 0 的路由 **7 条**：`qwen/qwen3.7-flash:free`、`nvidia/nemotron-3.5-lightning-free:free`、`nemotron-3.5-lightning-free`、`glyph-cluster`、`stealth/glyph-cluster:free`（匿名模型，详见[匿名模型](#匿名模型stealth)）、`deepseek/deepseek-v4-flash-0731free:free`、`auto:free`（智能路由免费池）。⚠️ **`reflection/beam` 与 `reflection/beam-free` 已退出免费池**（目录里 `beam` 改按量计费 $0.25/$1 per 1M）
- **接入**：`https://api.bazaarlink.ai/v1`（OpenAI 兼容）
- **状态**：Active（小型网关）— 核实于 2026-11-12（✅ `/v1/models` **125 个模型**、7 个零价路由，免费层持续有效；✅ 免费额度规则不变：未充值账号 **10 RPM / 每日 60 加权单位**，已充值 **20 RPM / 每日 120 加权单位**，全站免费上限 20 RPM、单账号并发 2，每日 UTC 00:00 重置；⚠️ 免费成员换血，Reflection Beam 两款已转计费；⚠️ 2026-09-05 起停用 agent 自助注册端点以防滥用，需正常注册账号后在面板建 key）
#### xKiro AI

- **官网**：https://xkiro.com（[文档](https://docs.xkiro.com)）
- **免费形式**：免费档（目录字段 `access_tier: free` 的款不消耗额度），第三方目录记 **5M tokens/日，仅限免费款**；同时支持 OpenAI `/v1/chat/completions` 与 Anthropic `/v1/messages` 两种协议
- **网页说明**：聚合 Qwen / Cohere / Mistral / MiniMax / 美团等多家；模型 ID 带 `:free` 后缀的多为 Qwen 系，不带后缀的也有大量 `free` 档（Cohere、Mistral 全家桶）；免费额度只覆盖 `access_tier: free`，另有 paid / premium 档需付费
- **免费模型**：⚠️ 2026-11-12 实测 `/v1/models` **从 97 款缩至 69 款**，`access_tier: free` **从 47 款缩至 26 款**，且**Qwen 全家桶全部退出**：现存的 26 款免费模型只有 Mistral（`mistral-large-2512` / `medium-3.5` / `small-2603` / `devstral-medium` / `codestral-2508` / `ministral-*`）、Cohere（`command-a` / `command-a-plus` / `command-a-reasoning` / `command-a-vision` / `command-r*` / `north-mini-code` / `north-small-translate` / `aya-*` / `tiny-aya-*`）、`sensenova/sensenova-6.8-flash-lite` 与 `stealth/big-pickle`。❌ `qwen3.8-max` / `qwen3.7-max` / `qwen3-coder-plus` / 其余 Qwen 款均已不在目录
- **接入**：`https://api.xkiro.com/v1`（OpenAI 兼容；也接受 `Authorization` 或 `x-api-key` 头）
- **状态**：Active（小型网关，**但免费阵容大幅缩水**）— 核实于 2026-11-12（⚠️ 仍需注册拿 key：免 key POST 返 401 `Missing ClientApiKey`，端到端调用未经本仓库实测；⚠️ **本仓库此前把 xKiro 写成「Qwen Max / Coder Plus 唯一免费入口」已作废**——Qwen 免费款在两周内全部消失，只剩 Mistral / Cohere 系；目录从 97 → 69、免费款 47 → 26，收缩速度比 OpenRouter 免费池还快，5M tokens/日 的第三方记录也需重新验证）

#### BeatAPI

- **官网**：[https://beatapi.io](https://beatapi.io)（[定价页](https://beatapi.io/zh/pricing)、[文档](https://docs.beatapi.io/zh)）
- **免费形式**：限时免费模型——`-free` 后缀的 Free 类模型输入/输出均 $0/M tokens；**免卡、免充值、零余额即可调用**。每账户限额：每日 **2000 次成功请求**，首充前 **1 次成功请求/分钟**、任意充值后 **10 次/分钟**（充多少都一样）；该额度与付费档位**分开计算**，免费调用不占用付费额度
- **网页说明**：折扣转售网关（文本/图像/视频模型 + 1000+ 数据 API），官网首页写明「4 个模型限时免费」并注明「每个账户首次充值前每分钟可成功免费调用 1 次，充值后最多 10 次，每日额度会调整。免费访问限时提供，可能限流或停止。充值不会自动切换到付费模型。」；文档 FAQ 进一步说明免费模型「sit outside these tiers」、由独立额度池计数
- **免费模型**：⚠️ **2026-11-12 复核只剩 3 款 $0**（官方免 key 的 `POST /v1/capabilities/search` 带 `{"query":"free","kind":"model"}` 返回 `total: 3`）：`deepseek-v4.1-flash-free`、`glm-5.3-flash-free`、`hy4-free`。❌ 11-02 记录的 `gemini-3.8-flash-free`、`minimax-m3.1-flash-free`、`jev-1.13-free`、`jev-1.14-free` **全部退出**；官方 `skill-refs/free-models.md` 明示「免费名单随时变，不要硬编码 id」，首页「4 个模型限时免费」文案同样滞后
- **接入**：`https://api.beatapi.io/v1`（OpenAI 兼容：`/v1/chat/completions`、`/v1/responses`；另支持 Anthropic `/v1/messages` 与 Gemini 原生格式；文本也可走 `https://direct.beatapi.io`）。注册后在 dashboard 建 key，免费模型零余额可调
- **状态**：Active（限时免费，**端到端未经本仓库实测**）— 核实于 2026-11-12（✅ 端点真实：`/v1/models` 无 key 返 `missing_api_key`；✅ 官方 `free-models.md` 确认免卡零余额可调、免费款每分钟 1 次成功请求（充值后 10 次）、429 带 `retry_after_seconds`；✅ 国内直连可通，无 `region_blocked`；⚠️ 免费名单 10 天内从 6 款砍到 3 款，稳定性差；⚠️ 2026-10 才上线的小型折扣转售商，无 SLA；⚠️ 隐私政策称不用客户内容训练通用模型，但明示「不承诺每个上游零保留」）

#### Zro (MoonMath)

- **官网**：[https://zro.moonmath.ai](https://zro.moonmath.ai)（[定价](https://zro.moonmath.ai/pricing)、[模型目录](https://zro.moonmath.ai/model-catalog)、[文档](https://zro.moonmath.ai/docs)）
- **免费形式**：免费档（Free plan，**$0/月**）——**每日免费用量、每日重置**，覆盖 `deepseek-v4.1-flash` 与 `glm-5.3-flash` 两款 Flash；无需付费即可使用（「免卡」为 $0 档推断，注册未实测）；每日额度具体数值未公开
- **网页说明**：MoonMath.ai 的一手私有推理服务（面向 coding agent），自称「Private / Uncensored models」。定价页原文："Free plan for Flash models. $0 per month. included daily usage. Free daily usage on GLM-5.3 Flash and DeepSeek V4.1 Flash. Resets every day."，并标 OpenAI-compatible API、Zero request retention、No training on requests。付费档 Pro $20/月（含 $40 用量）、Max $60/月（含 $120 用量）；用量包 $5 起、90 天过期
- **免费模型**：免费档覆盖 `deepseek-v4.1-flash`、`glm-5.3-flash` 两款 Flash；同站付费模型 `glm-5.3`、`dolly1-security`、`dolly2-security`（后两者为「无审查」安全模型）不在免费档
- **接入**：`https://zro.moonmath.ai/v1`（OpenAI 兼容 `/v1/chat/completions`、`/v1/responses`）；Anthropic Messages 用 base `https://zro.moonmath.ai`；`Authorization: Bearer sk-...`；每请求经 EU 网关鉴权路由，推理可选 EU/US
- **状态**：Active（免费档，**端到端未经本仓库实测**）— 核实于 2026-11-12 复核维持（✅ `/v1/models` 无 key 仍返 401 `auth_error`、端点真实；✅ 国内直连可通；✅ 定价页仍写 Free plan $0/月、每日额度覆盖 `deepseek-v4.1-flash` 与 `glm-5.3-flash` 两款、零请求保留不用于训练；⚠️ **每日免费额度具体数值仍未公开**；⚠️ 一人一号、新站无 SLA；⚠️ 官网首页本次抓取超时，条款未逐字复核）

#### cheapllm.shop

- **官网**：https://cheapllm.shop（[定价](https://cheapllm.shop/zh/#stall)、[文档](https://cheapllm.shop/zh/docs/)、[服务条款](https://cheapllm.shop/zh/terms/)、[隐私政策](https://cheapllm.shop/zh/privacy/)、[法律信息](https://cheapllm.shop/zh/legal/)）
- **免费形式**：限时免费（beta 期）——测试期间输入 / 输出 / 缓存输入均 $0，宣称无速率限制（请求体 4 MB、每账户最多 25 个 key；繁忙时排队最多 30 秒，之后返回带 `Retry-After` 的 503）；**ToS 与文档都承诺 beta 结束后保留「永久免费额度」：每小时至少 5,000 输入 / 1,000 输出 token（按账户滚动一小时、所有 key 合计），免绑卡、数额只升不降**；超额按 $0.005 / $0.001 / $0.14 per 1M 计费，且只有主动添加支付方式后才会产生费用。beta 结束前会发邮件通知，但未公布截止日期
- **网页说明**：单模型小型网关。首页写「免费，无速率限制」「测试期间免费，无需信用卡」，定价区（`#stall`）把 $0.005 / $0.001 / $0.14 划掉改标 $0.00，FAQ 明确「是的，只要测试期持续」。注册只需邮箱+密码——无卡、无手机号、无邮箱验证，`/api/signup` 直接下发 `sk-cheap-` 开头的 key
- **免费模型**：仅 `deepseek-v4.1-flash-1017` 一款；文档称含 `deepseek` 字样的模型名也会路由到它，便于硬编码模型名的工具直接接入
- **接入**：`https://cheapllm.shop/v1`（OpenAI 兼容 `POST /v1/chat/completions`、`GET /v1/models`；`Authorization: Bearer sk-cheap-...`）。⚠️ 首页引导 `curl -fsSL https://cheapllm.shop/setup.sh | sh`，该脚本会改写本机 40 个工具（Claude Code / Codex CLI / Cursor 等）的 base URL，建议手改配置、不要在生产机执行
- **状态**：Active（限时免费 / 小型网关，**端到端未经本仓库实测**）— 核实于 2026-11-14（✅ `GET /v1/models` 返 200、目录仅 `deepseek-v4.1-flash-1017`；✅ `POST /v1/chat/completions` 免 key 返 401 `invalid_api_key`、假 key 返 401 `not valid`，端点与鉴权层真实；✅ 国内直连可通；⚠️ **法律信息页按法国 LCEN 应披露的运营者名称、法律形式、注册号、地址、电话、主机商全部是 "not provided yet"**，主体不透明；⚠️ 域名 2026-03-28 注册、博客首篇 2026-11-08、条款 2026-11-12 更新，服务上线约一周且全网无第三方评测；⚠️ ToS 写「免费访问是恩惠，不是权利」，可无理由封号 / 撤 key / 停服、无 SLA，首页已挂「需求高于预期，可能出现 slowdowns」；⚠️ 提示词不落盘，但主容量不足时会转备用推理商，其条款可能保留提示与回答并用于改进模型，且 ToS 允许随时无通知更换上游推理商——后端是否真为该模型无法核实）

### 客户端内免费（无公开 API）

> 下面这些产品把免费额度锁在自家客户端里：**没有公开 endpoint，也没有可以拿来做第三方调用的 API Key**。收录它们只为让读者知道「这些模型确实能白嫖，但只能在该产品内用」，**不是**能接进自己程序的渠道。列进本节不等于允许外部调用——Freebuff 的条款甚至明令禁止。

#### Freebuff

- **官网**：[https://freebuff.com](https://freebuff.com)（[定价页](https://freebuff.com/plans)）
- **免费形式**：Free 档「每天补满 30 小时」的会话时长（按模型折算，各模型额度不通用）；广告资助，不绑卡、不按 token 计
- **网页说明**：Codebuff 团队的免费 coding agent（Codebuff Pro 为付费档），提供 CLI（`npm install -g freebuff`）、桌面、Web 三种客户端；官方口径是「the free coding agent」「funded by ads」，定价页写明 Free 档 `30 hours refilled daily`
- **免费模型**：Free 档明列 MiMo v2.6 Flash（Slow / Fast）、DeepSeek V4.1 Flash 10/17、Claude Haiku 5.5（100k 上下文）；同页另有 GLM 5.3 Flash、GPT-6 Luna、MiMo 2.6 Pro、Muse Spark 1.3、Nemotron 3.5 Lightning、Solar Mini 4 / Pro 4、Glyph Cluster 的每小时折算表，但未标注各自归属哪一档
- **接入**：**无公开 endpoint、无 API Key**——`/docs`、`/api/models`、`/api/v1/models` 打开都是站点的 `Page not found` 页（2026-10-29 核实）；官网只有首页、`/plans`、`/cli`、`/app` 等产品页；登录凭证只是客户端本地的 `~/.config/manicode/credentials.json` 里的 `authToken`
- **状态**：Active（客户端锁定，**不可当上游**）— 核实于 2026-10-29（⚠️ **条款明文禁止外部调用**：ToS「Free Access and Human Use」禁止 "call the underlying servers or endpoints directly or through scripts, custom clients, wrappers, integrations, or third-party software"，同时禁止 resell / rent / proxy / relay 与共享账号——社区反代（Freebuff2API、freebuff2api-workers）属违约，本仓库不推荐；⚠️ **区域限制**：full 模式仅覆盖 25+ 国家，其余地区或挂 VPN 时降级为 limited mode，只剩 DeepSeek V4 Flash、每天 6 个 1 小时会话，而用 VPN 伪装地区本身也违反条款；⚠️ **隐私代价高**：为投放个性化广告会扫描项目内的配置/文档文件、采集发送前的输入与交互行为，标了「May use data for AI training」的模型其提交内容可能被授权或出售给第三方用于训练；⚠️ **免费口径自相矛盾**：10-09 发布文写 limited mode 为「DeepSeek V4 Flash + 6 × 1 小时」，现定价页写「30 小时/天」而同页折算表又给出 52 小时，条款另保留随时调整模型与额度的权利）

#### AtomCode（CodingPlan）

- **官网**：https://ai.atomgit.com/serverless-api
- **免费形式**：CodingPlan Lite 体验版——限时免费、每日限量 500 人领取、7 天有效、约 200 次调用 / 5 小时
- **网页说明**：AtomGit（智谱生态）终端 AI 编程工具的免费额度；**非标准 API 渠道**——额度仅限 AtomCode 客户端内使用，不支持第三方 endpoint 调用
- **免费模型**：mimo-v2.5、qwen3.8-27b、deepseek-v4-flash（以客户端内列表为准）
- **接入**：安装 AtomCode 客户端，AtomGit 账号登录后自动领取（无公开 endpoint）
- **状态**：Active（限时）— 核实于 2026-09-05（严格说不符合本仓库"API Key + endpoint"收录标准，收录仅供了解）


## 参与贡献

发现新的永久免费或限时免费渠道？额度变了？贡献让这份列表活下来。

- **收录门槛**：只收**永久免费**（周期性免费层 / 永久免费模型）和**限时免费**（明确标注活动期）的 **API** 渠道，判断标准是"能不能拿到 API Key、通过 endpoint 持续免费调用"。网页对话免费不算。
- 新增渠道时按[免费渠道一览](#免费渠道一览)的格式添加：名称 + 官网 + 免费形式 + 网页说明 + 免费模型，并在[模型免费渠道索引](#模型免费渠道索引)同步。
- 某渠道整体失去免费资格时，把对应条目标注 **Archived**（附日期），不要默默删掉。

完整模板和规则见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 免责声明

> **本页收录的额度、限速和条款随时可能变动且不另行通知。**
> 本列表只是一个快照。上线任何生产项目前，请务必到对应官方定价页二次确认。

以下是常见的信息偏差，我们会在条目中显式标注：

- **"免费层"不等于"永久免费"。** Google 在 2025 年 12 月将 Gemini 免费额度砍掉约 80%，其他家随时可能跟进。
- **免费名单的流动性比想象中大。** OpenRouter 的 `:free` 名单在 2026-09-11 / 09-20 / 09-27 / 10-24 / **11-12** 五次实测为 **19 → 21 → 17 → 20 → 16 款**，`nemotron-3-super-120b` 回归仅 19 天又退出，`inkling` / `inkling-small` 被换成 `inkling-2-small`；NVIDIA NIM 从 82 → 80 → 85 → **84**，成员每批都换；OpenCode Zen 的 `-free` 名单两周内从 8 款换到 11 款（`jev-1.13` 退出、4 款新进）；**xKiro AI 两周内目录 97 → 69、免费款 47 → 26，Qwen 全家桶一次性清零**；**BeatAPI 10 天内免费款 6 → 3**；**Vercel 的 MiniMax M3.1 Flash 零价路由直接转计费**。收录的模型可能在你看到时已经下架，用前务必跑一次 `curl` 确认。
- **"限时免费"随时可能结束。** 活动期 API（如曾经的 B.AI 限时免费档）没有公开的截止日期，消失也不会提前通知。
- **部分"免费"需要绑信用卡**才能开通，或需要手机号/实名验证。例：Vercel AI Gateway 的每月 $5 免费额度，官方明确要求**先绑定有效支付方式**才可启用（`To use free AI Gateway Credits, add a valid payment method to your team.`，2026-09-20 核实）——绑卡不等于扣费，但门槛确实存在。
- **不是所有"免费模型"都在生成文本。** Jev 这类**结构化决策模型**（输入状态 + 带类型的问题，输出选项/评分/概率）走的是 Evaluation 或 Decisions 类接口，**不能当聊天模型用**，OpenAI 兼容的 chat/completions 调用方式往往不适用。
- **你的数据可能被用于训练。** Google（免费层）、Mistral（Experiment 计划）、Groq 以及 OpenRouter 的 `:free` 上游普遍会在免费流量上做训练，部分支持关闭。
- **匿名模型的身份风险被低估。** [匿名模型](#匿名模型stealth)节里的模型没有可查的开发者，长期定价与数据处理承诺都悬空，且可能随时消失——只当评测端点，别进生产链路；敏感数据务必按你实际用的那家网关的条款判断，同一模型在不同网关可能一个零保留、一个会留存。
- **小型网关的免费额度最不稳定。** Token Harbor / BazaarLink 这类新晋网关验证有限、随时可能关停或收费，只适合原型验证，别托付生产负载。
- **「客户端内免费」不是渠道，反代也不是解法。** Freebuff / OpenCode Zen / AtomCode 这类把额度锁在自家客户端的服务，社区常有一键反代成 OpenAI 兼容 API 的开源项目，但条款多明文禁止直连 endpoint、禁止 proxy / relay——用了就是违约，封号与额度清零风险自负，本列表只把它们记在[客户端内免费](#客户端内免费无公开-api)一节备查。
- **「有额度」≠「能随意调用」。** 签到/额度制平台常对旗舰模型另设每日消耗上限——Onomeo 2026-09-27 曾记 13 款 premium 模型限 5 万额度/日（购买后 30 万），`gpt-6-astra` 只能调约 12 次/天；⚠️ **但 2026-11-12 该站已改版**：premium 扩到 28 个 ID、`dailyCap` 降到 10,000 且标 `buyersOnly: true`，签到文案下线，原换算表全部作废。**判断能调几次仍要看单次成本 × 每日上限取小，但前提是先确认这个机制还在。**
- **「签到领额度」不是「免费档模型」。** Onomeo 曾以签到/问卷换每日额度，全目录都能调但消耗差异极大（2026-09-27 实测同平台 `gemini-3.1-flash-lite` 一次 9 额度、`Qwen3.8-Flash-Next` 41,457，**相差四千倍**），且 `deepseek-v4.1-flash` 5 天内从 1,473 涨到 8,409；⚠️ 2026-11-12 复核：站点改版为排行榜，模型 ID 全换（`deepseek-flash` 2,368、`qwen3.8-max` 396,776），签到与问卷开关 `survey: false` 均已下线，**当前免费入口无法证实**，切勿再引用旧的成本数字估算次数。
- **部分境外网关对国内做区域封锁。** Token Harbor 实测直接返回 `region_blocked`，明文拒绝中国大陆/香港/澳门（2026-09-12）；此类端点即使有免费额度，国内也需自备境外网络，且官方通常要求关闭 VPN——它只能看到连接出口国。
- **"官方注册送额度"不等于免费。** 例如 DeepSeek 官方 API 的试用赠送已确认取消（2026-08-31 实测余额为 0），官方渠道现在是"低价"而非"免费"。

## 许可证

[MIT](LICENSE)——随便 fork、改写、发布，保留版权声明即可。
