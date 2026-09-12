# Awesome Free LLM API（免费大模型 API 导航）

**简体中文** | [English](README.en.md)

> 以**渠道**为主体：下面每个渠道都给出官网、免费形式和官网上的免费说明。
> 想按模型找免费渠道：重点模型见[模型免费渠道索引](#模型免费渠道索引)。

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

本列表只收录你能**持续调用**的**永久免费** API，以及**明确标注限时免费**的 API。**只认 API**——必须能拿到 API Key、通过 endpoint 调用才算数；模型官网的网页对话（Chat 界面）免费开放，**不属于本列表范畴**。


---

## 目录

- [收录范围](#收录范围)
- [模型免费渠道索引](#模型免费渠道索引)
- [免费渠道一览](#免费渠道一览)
  - [海外官方免费层](#海外官方免费层)
  - [中国平台](#中国平台)
  - [聚合与网关](#聚合与网关)
  - [限时免费](#限时免费)
  - [小型网关（谨慎）](#小型网关谨慎)
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

## 模型免费渠道索引

### DeepSeek 系列

#### DeepSeek V4.1 Flash

> 552B 新架构 MoE（8B/16B 激活）,原生多模态,1M 上下文；2026-09-10 发布

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:目前已上架官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [Token Harbor](https://tokenharbor.ai) | 免费层月额度内(4 周滚动刷新) | 优势:小型网关、免卡注册、含 V4.1 Flash;限制:免费额度未公开、按 4 周滚动刷新,网关资历浅 |  |

> ⚠️ **官方无免费层**：DeepSeek 官方仅付费（闲时 $0.15/$0.60 per 1M）；上表为第三方渠道，免费额度随时可能调整。

#### ~~DeepSeek V4 Pro~~（2026-09-14 起官方路由退役）

> 旗舰 MoE,1M 上下文,编程与智能体场景最强。⚠️ 官方 API 自 2026-09-14 12:00 起将 `deepseek-v4-pro` 请求全部转发到 V4.1 Flash 并按 Flash 价计费，直至 V4.1 Pro 上线

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM 无每日上限 | 优势:官方托管、免绑卡、无每日上限;限制:40 RPM 全站共享,高峰期需排队 | 经常超时 |
| [商汤 SenseNova](https://platform.sensenova.cn) | 公测免费,滚动 5h 60k 积分 | 优势:国产官方、公测期免费用量大、1M 上下文;限制:限时公测,付费档即将上线 |  |

#### DeepSeek V4 Flash

> 284B MoE,1M 上下文,代码 / 推理性价比首选。⚠️ 官方模型名 `deepseek-v4-flash` 已自动路由到 V4.1 Flash,旧 ID 仍可用

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [商汤 SenseNova](https://platform.sensenova.cn) | 公测免费,滚动 5h 60k 积分 | 优势:国产官方、公测期免费用量大;限制:限时公测,付费档即将上线 |  |
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管最稳、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |
| [OrcaRouter](https://www.orcarouter.ai) | 免费池限流,零加价 | 优势:200+ 模型统一网关、0% token 加价、免卡;限制:免费额度未公开、429 限流、best-effort 非生产可用 |  |
| [Hugging Face](https://huggingface.co) | 共享端点限流 | 优势:免费、社区模型全;限制:共享端点限流严重、无 SLA | 限流严重 |
| [魔搭 ModelScope](https://modelscope.cn) | 约 200 次/日 | 优势:国产、OpenAI 兼容、模型全;限制:免费质量较低——单模型仅约 200 次/日,与全站共享 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管最稳、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### DeepSeek R1 / V3

> 深度推理模型 / 通用旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | R1 蒸馏版,1 万 Neurons/日 | 优势:边缘节点低延迟、每日免费;限制:仅蒸馏版非原版、额度小 |  |
| [OpenRouter](https://openrouter.ai) | `:free` 名单轮换,可能不含 | 优势:一站式聚合、OpenAI 兼容;限制:免费仅 50 次/天($10 后 1000),名单随时轮换 |  |
| [魔搭 ModelScope](https://modelscope.cn) | R1 约 200 次/日 | 优势:国产、模型全;限制:免费质量较低——R1 仅约 200 次/日,与全站共享 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |

> ⚠️ **DeepSeek R1 / V3 已不在 NVIDIA NIM**：截至 2026-09-11 已从 NIM 模型列表移除（仅剩 V4 Flash 0731 与 V4 Pro 0813）。

#### DeepSeek R2

> 新一代通用模型

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [火山方舟](https://console.volcengine.com/ark) | 协作奖励计划免费额度内(每日 200 万 token) | 优势:每日 200 万 token 大额免费;限制:需注册火山引擎并实名,额度以控制台为准 |  |

### GLM 系列

#### GLM-5.3 Flash

> 原生多模态,320B,1M 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管、免绑卡、1.3M 上下文多模态、无每日上限;限制:40 RPM 全站共享,高峰期需排队 | 经常超时 |
| [OrcaRouter](https://www.orcarouter.ai) | 免费池限流,零加价 | 优势:200+ 模型统一网关、0% token 加价、免卡;限制:免费额度未公开、2026-09-07 起替换 Qwen3.8-27B 成为免费默认,TTFT 偏高(约 7.66 秒) | 限流 |
| [B.AI](https://b.ai) | 限时免费(0 Credits) | 优势:匿名免注册、输出 $0;限制:限时免费无截止日期,随时可能结束 |  |
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | 限时免费(ZZ.ai) | 优势:AMD 官方托管、每日 $10 等值额度;限制:限时免费、TTFT 偏高、并发限流 | TTFT 偏高 |

#### GLM 5.2 / 5.1

> 智能体工作流旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [商汤 SenseNova](https://platform.sensenova.cn) | 公测免费(实测可调,滚动 5h 60k 积分) | 优势:国产官方、公测免费且实测可调;限制:限时公测,付费档即将上线 |  |
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [OpenCode Zen](https://opencode.ai/zen) | 限时免费模型(GLM 5.3 Flash 等) | 优势:OpenCode 官方网关、免卡;限制:仅限时免费的 Flash 款,正式版 GLM 5.3 为付费($1.4/$4.4) |  |

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

#### Qwen3 Coder 480B

> 代码专项 SOTA,Agent 编码

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [魔搭 ModelScope](https://modelscope.cn) | 约 500 次/日 | 优势:国产、模型全;限制:免费质量较低——单模型约 500 次/日,与全站共享 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |

> ⚠️ **Qwen3 Coder 480B 已不在 OpenRouter 免费名单**（2026-09-11 实测）。

#### Qwen3 235B

> 通用 MoE 旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [魔搭 ModelScope](https://modelscope.cn) | 约 500 次/日 | 优势:国产、模型全;限制:免费质量较低——单模型约 500 次/日,与全站共享 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |

> ⚠️ **Qwen3 235B 已不在 OpenRouter 免费名单**（2026-09-11 实测）。

#### Qwen3.8 Flash

> 轻量多模态,中文写作强

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [B.AI](https://b.ai) | 限时免费 | 优势:匿名免注册、输出 $0;限制:限时免费无截止日期 |  |
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
| [魔搭 ModelScope](https://modelscope.cn) | 共享额度内 | 优势:国产、模型全家桶;限制:免费质量较低——与全站共享每日 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |

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

> ⚠️ **MiniMax 系列已从 NVIDIA NIM 下架**：2026-09 初曾短暂上架 GLM-4.7 与 MiniMax M2.1，但截至 2026-09-11 两者均已从 NIM 模型列表移除。

#### MiniMax M3

> 多模态 MoE,推理 / 工具调用

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [OpenCode Zen](https://opencode.ai/zen) | 限时免费(客户端内) | 优势:OpenCode 官方网关、免卡;限制:限时免费,仅客户端内使用 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(官方标注即将弃用) | 优势:官方托管、免绑卡;限制:官网标注即将弃用,慎用 | 经常超时 |

#### MiniMax M2.1

> 多语言编程强化版,204K 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| OpenCode Zen | ⚠️ 已弃用(2026-03-15) | 该模型在 OpenCode Zen 已下架,官方 API 为付费($0.3/$1.2) |  |

#### Kimi K2.6

> 1T MoE,长程编码,多模态

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### Kimi K3

> 2.8T 原生多模态 Agent,1M 上下文,长程编程 / 复杂推理

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [商汤 SenseNova](https://platform.sensenova.cn) | 公测免费,滚动 5h 60k 积分(额度/RPM 有限) | 优势:国产官方、公测免费、1M 上下文、原生视觉;限制:限时公测,付费档即将上线,额度/RPM 有限(实测偶发限流) |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### StepFun Step 3.7 Flash

> 国产稀疏 MoE 推理模型

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| — | **不在 NVIDIA NIM** | ⚠️ 截至 2026-09-11 已从 NIM 模型列表移除，暂无免费 API 渠道 |  |

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
| [B.AI](https://b.ai) | Hy3 限时免费 | 优势:匿名免注册;限制:限时免费无截止日期 |  |
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
| [B.AI](https://b.ai) | 限时免费 | 优势:匿名免注册、输出 $0;限制:限时免费无截止日期 |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |

#### SenseNova 6.8 Flash-Lite

> 商汤原生多模态智能体（6.7 已并入，旧 ID 8/31 前自动重定向）

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [商汤](https://platform.sensenova.cn) | 公测免费,滚动 5h 60k 积分 | 优势:官方自营、公测期免费额度大、Flash-Lite 消费返赠等效半价;限制:限时公测,付费档即将上线 |  |

### 海外模型

#### GPT-OSS 120B / 20B

> OpenAI 开源 MoE,代码 / 推理强

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Groq](https://console.groq.com) | 1000 次/日 | 优势:LPU 极速推理;限制:30 RPM / 1000 RPD,TPM 8K |  |
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(仅 20B) | 优势:官方托管、免绑卡;限制:40 RPM 全站共享,仅托管 gpt-oss-20b | 经常超时 |

> ⚠️ **GPT-OSS 已不在 OpenRouter 免费名单**（2026-09-11 实测）。

#### Gemini 2.5 Flash / Flash-Lite

> Google 免费层主力,多模态

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Google AI Studio](https://aistudio.google.com) | 按天重置(Flash 约 1500 次/日、Flash-Lite 约 1000 次/日) | 优势:官方大额免费、免绑卡、多模态;限制:需 Google 账号,免费层数据可能用于改进产品 |  |

#### Nemotron 3 Ultra / Super / Lightning

> NVIDIA 智能体旗舰,1M 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free`（Ultra / Super / 3.5 Lightning） | 优势:聚合路由;限制:免费仅 50 次/天,名单随时轮换 |  |
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方自营旗舰、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### InKling / Ling 3.0 Flash（OpenRouter 新晋免费）

> Thinking Machines 的 InKling 与蚂蚁的 Ling 3.0 Flash,均为 1M / 262K 上下文多模态

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free`（`inkling` / `inkling-small`、`ling-3.0-flash-sante` / `-fin` / `-vl`） | 优势:1M 上下文多模态、聚合路由;限制:免费仅 50 次/天,名单随时轮换 |  |

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
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费 | 优势:官方托管、免绑卡;限制:40 RPM 全站共享 | 经常超时 |

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


## 免费渠道一览

### 海外官方免费层

#### NVIDIA NIM

- **官网**：https://build.nvidia.com
- **免费形式**：永久免费层（40 RPM 全站共享，无每日上限）
- **网页说明**：官网称「100+ 模型免费调用」——NVIDIA 托管的推理端点，注册即可用，无需信用卡
- **免费模型**：DeepSeek V4 Flash 0731 / V4 Pro 0813、Kimi K2.6 / K3、**z-ai/glm-5.3-flash**、Gemma 4 31B、Nemotron 3 Ultra / Super / Nano、GPT-OSS、Mistral Large 等（以 `/v1/models` 实测为准）
- **接入**：`https://integrate.api.nvidia.com/v1`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-09-12（实测 `/v1/models` 返回 **82 个模型**；✅ **新上架 `z-ai/glm-5.3-flash`**（1.3M 上下文、多模态）；⚠️ MiniMax / Qwen / StepFun / Ling 仍不在列，GLM 5.2 / 5.1 / 4.7 亦未回归，DeepSeek V4.1 Flash 尚未上架）

#### Google AI Studio

- **官网**：https://aistudio.google.com
- **免费形式**：永久免费层（按天重置）
- **网页说明**：Google 官方 AI 开发平台，免费层提供 Gemini 系列模型 API 调用
- **免费模型**：Gemini 2.5 Flash（约 1500 次/天）、Flash-Lite（约 1000 次/天）、Gemini 3.x Flash（预览，限流更严）；2.5 Pro 已移出免费层（2026-04-01 起）
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
- **免费形式**：永久免费（共享推理端点，限流）
- **网页说明**：最大的开源模型库，提供免费推理 token（Inference API）
- **免费模型**：数千个社区与官方模型（DeepSeek V4 Flash 等也在列）
- **接入**：`https://router.huggingface.co/hf-inference`（`InferenceClient` / REST）
- **状态**：Active — 核实于 2026-08-31

#### AMD Token Factory（Radeon Cloud）

- **官网**：https://developer.amd.com.cn/radeon/tokenfactory
- **免费形式**：每日约 $10 美元等值额度，每日重置（不过夜）
- **网页说明**：AMD Radeon Cloud 官方推理平台，注册登录领取每日免费额度，OpenAI 兼容
- **免费模型**：DeepSeek V4 Flash 0731（Free）、MiniCPM5-1B（Free）、GLM-5.3-Flash（限时，ZZ.ai）、Qwen3.8-Flash-Next（限时，AMD GPU Cloud）
- **接入**：`https://developer.amd.com.cn/radeon/api/v1`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-09-02（TTFT 偏高，首字延迟约 22 秒）

#### Ollama Cloud

- **官网**：[https://ollama.com](https://ollama.com)（[云模型目录](https://ollama.com/search?c=cloud)）
- **免费形式**：永久免费层（Free 档注册即含 starter 用量额度，按月刷新不过期；具体数额未公开）
- **网页说明**：官网定价页 Free 档 $0 —— "Starter usage credits included / Access to starter models"；云模型按 token 计价从额度扣除，加 credits 可解锁全部模型
- **免费模型**：**deepseek-v4.1-flash**、deepseek-v4-pro:0813、deepseek-v4-flash:0731、glm-5.1 / 5.2 / 5.3 / 5.3-flash、kimi-k2.6 / k2.7-code / k3、minimax-m2.7 / m3、qwen3.5:397b、gpt-oss:20b / 120b、gemma4:31b、nemotron-3-super / ultra / nano:30b、mistral-large-3:675b（共 20 个，starter 子集以官网为准）
- **接入**：`https://ollama.com/api/chat`（Ollama API；API Key：[https://ollama.com/settings/keys](https://ollama.com/settings/keys)）
- **状态**：Active — 核实于 2026-09-12（实测 `/api/tags` 返回 20 个云模型，✅ **新上架 `deepseek-v4.1-flash`**——这是 V4.1 Flash 目前可确认的免费入口之一；免费额度为月度 starter 用量、数额未公开；仅 1 并发）

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
- **状态**：~~Active — 核实于 2026-08-31~~ **即将失效（2026-09-08）** —— hunyuan-lite 永久免费已终结，不再符合收录标准，条目保留备查

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
- **接入**：[https://xinghuo.xfyun.cn/sparkapi](https://xinghuo.xfyun.cn/sparkapi)（讯飞 APIKey/APISecret 鉴权；OpenAI 兼容端点见官方文档）
- **状态**：Active — 核实于 2026-09-05（需实名）

#### 商汤 SenseNova（日日新）

- **官网**：https://platform.sensenova.cn · Token Plan：https://www.sensenova.cn/token-plan
- **免费形式**：限时免费（公测期完全免费，付费档位 Lite/Pro 即将上线）；TokenPlan 积分体系——通用积分池与 Flash-Lite 专属积分池**各自**享有 **60,000 积分 / 滚动 5 小时** + **600,000 积分 / 滚动周**
- **网页说明**：官网称"公测期完全免费开放，付费档位即将上线"；公测 Free 档含 SenseNova 6.8 Flash Lite 与 SenseNova U1 Fast，最多 20 个 API Key；Flash-Lite 消费返赠——每消耗 1 专属积分返 1 通用积分（返赠 30 天有效且**不占用滚动额度**，等效半价）；第三方模型额度低于自营
- **免费模型**：SenseNova 6.8 Flash-Lite（多模态智能体）、SenseNova U1 Fast（信息图生成）、SenseNova U1.5 Lite（图片创作）、DeepSeek V4 Flash / V4 Pro、GLM-5.2、Kimi K3（8 个模型定价均为 0，2026-09-08 API 实测）
- **接入**：`https://token.sensenova.cn/v1`（OpenAI 兼容，亦支持 Anthropic 兼容端点）
- **状态**：Active（限时公测）— 核实于 2026-09-12（手机号注册，免绑卡、免实名；✅ 官方文档确认公测期 Free 档 **¥0/月** 且**未公布结束日期**；✅ 实测 `token.sensenova.cn/v1` 正常响应 401/需鉴权，而网传的 `api.sensenova.cn/v1` 返回 404，**请以 `token.sensenova.cn/v1` 为准**；实测延迟偏高，Kimi K3 消耗积分最快）

#### 魔搭 ModelScope（阿里）

- **官网**：https://modelscope.cn
- **免费形式**：永久免费（所有注册用户免费推理，每日总 2000 次，单模型 100~500 次/日不等）
- **网页说明**：阿里达摩院开源模型社区，官网明确「所有注册用户均可免费推理」；DeepSeek-R1 约 200 次/日
- **免费模型**：DeepSeek V4 Flash / R1、Qwen3 Coder 480B、Qwen3 235B、Qwen2.5 72B、GLM-4.5、MiniMax-M1 等近 3000 个开源模型
- **接入**：`https://api-inference.modelscope.cn/v1`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-09-02（需阿里云账号 + 实名）
- **⚠️ 免费质量较低**：单模型仅 100~500 次/日，与全站共享每日 2000 次总量（高峰可能被挤占）；仅限个人学习与非商业用途；共享算力排队，无 SLA

### 聚合与网关

#### OpenRouter

- **官网**：https://openrouter.ai
- **免费形式**：永久免费（`:free` 模型 50 次/天，20 次/分钟；累计充值 $10 后升至 1000 次/天）
- **网页说明**：多模型聚合路由，官网提供 `:free` 免费模型清单，`openrouter/free` 可自动路由（⚠️ 网传「200 次/天」为过时信息，官方限速页现行标准为 50/1000）
- **免费模型**：`thinkingmachines/inkling(-small)`（1M 上下文多模态）、`nvidia/nemotron-3-ultra-550b`、`nemotron-3-super-120b`、`nemotron-3.5-lightning`、`gemma-4-26b-a4b`、`gemma-4-31b`、`inclusionai/ling-3.0-flash-sante/-fin/-vl`、`nex-agi/nex-n2.5-pro/-mini`、`cohere/north-mini-code`、`poolside/laguna-s-2.1/-xs-2.1`、`dots-studio/dots-3-note-preview`（512K）、`liquid/lfm-2.5-2.6b` 等 **19 个**（**名单随时轮换**——**DeepSeek / GLM / Qwen / MiniMax / Kimi 均不在免费名单**，用前先查 `openrouter.ai/models?max_price=0`）
- **接入**：`https://openrouter.ai/api/v1`（模型名务必带 `:free` 后缀）
- **状态**：Active — 核实于 2026-09-12（免费名单已实测刷新：19 个 `:free` 模型；每日额度 50 次，充值 $10 后 1000 次。⚠️ 免费池一天一进一出——9/8 MiniMax 两款退出、Nex AGI N2.5 两款进入；「发布当天进免费池」是冷启动信号而非长期承诺，务必留 fallback）

#### AIHubMix

- **官网**：[https://aihubmix.com](https://aihubmix.com)（[免费模型专页](https://aihubmix.com/models/free)）
- **免费形式**：免费模型档（注册送 10 次试用、不过期；一次性充值 $1 起即永久转每日配额：100 次/日 · 1M token/日，每日重置）
- **网页说明**：官网标注「56 free models — no credit card required」——平台补贴推理成本，免费模型输入输出均 $0
- **免费模型**：glm-4.7-flash-free、hy3-free、minimax-m3-free、k2.6-code-preview-free、gpt-oss-20b-free、nemotron-3-ultra/super-free、gemma-4-31b-it-free、mimo-v2.5(-pro)-free、coding-glm-5.3-free、gpt-5.5-free、gemini-3.8-flash-free 等 56 个
- **接入**：`https://aihubmix.com/v1`（兼容 Chat Completions / Messages / Responses 三协议）
- **状态**：Active — 核实于 2026-09-05（充值 $1 才转每日配额；全免费模型共享额度池）

#### OpenCode Zen

- **官网**：[https://opencode.ai/zen](https://opencode.ai/zen)（[定价页](https://opencode.ai/docs/zen/)）
- **免费形式**：限时免费模型（Big Pickle、MiMo-V2.5 Free、Ling 3.0 Flash Fin Free、Nemotron 3 Ultra Free、Nemotron 3.5 Lightning Free、Muse Spark 1.3 Contributor Free —— 输入/输出/缓存读写全 $0）
- **网页说明**：OpenCode 官方模型网关，官网定价页将上述 6 款明确标注为 Free，并说明"限时免费、用于收集反馈改进模型"；**并非整个平台免费**——DeepSeek / GLM / Kimi / Qwen 等主流模型均为按量付费
- **免费模型**：Big Pickle（隐身模型）、MiMo-V2.5 Free、Ling 3.0 Flash Fin Free、Nemotron 3 Ultra Free、Nemotron 3.5 Lightning Free、Muse Spark 1.3 Contributor Free
- **接入**：`https://opencode.ai/zen/v1`（OpenAI 兼容；部分模型走 `/messages` Anthropic 协议或 `/responses`）
- **状态**：Active（限时免费）— 核实于 2026-09-11（⚠️ 网传的 `deepseek-v4-flash-free` **实为付费**（$0.14/$0.28），不在免费名单）

#### OrcaRouter

- **官网**：[https://www.orcarouter.ai](https://www.orcarouter.ai)（[文档](https://docs.orcarouter.ai)）
- **免费形式**：免费池按 workspace 限流（额度不公开）；**付费侧 0% token 加价**（按上游官方价转发）
- **网页说明**：OpenAI 兼容的 LLM 路由网关，200+ 模型统一端点；免费模型是「目录模型套一层 free ID」，权重能力与付费版一致，但跑在独立限流池里——**免费池打满不会自动降级到付费版**
- **免费模型**：`orcarouter/free`（按难度智能路由免费池）、`z-ai/glm-5.3-flash-free`、`deepseek/deepseek-v4-flash-free`、`tencent/hy3-free`（2026-09-12 实测 `/v1/models` 195 个中的免费 4 款）
- **接入**：`https://api.orcarouter.ai/v1`（OpenAI 兼容，注册免卡）
- **状态**：Active（限流）— 核实于 2026-09-12（2026-09-07 免费默认模型由 Qwen3.8-27B 换成 GLM-5.3 Flash：质量分 4→8、上下文 262K→1M，但 TTFT 1.96s→7.66s、吞吐 196→74 tok/s；⚠️ 未充值账号日额度更小，`429 + Retry-After` = 限流、无 header 的 429 = prompt 超长；官方明示为 best-effort，非生产容量）

#### Chutes ~~（已失效）~~

~~已失效（2026-09-12 复核维持）：`llm.chutes.ai/v1/models` 虽有 30+ 模型在列，但官网定价页**全部标价**（DeepSeek V4 Flash 0731 $0.44/$1.32、Kimi K3 $3.00/$15.00），未发现任何免费端点；内容保留备查。~~

- ~~**官网**：https://chutes.ai~~
- ~~**免费形式**：社区 GPU 免费端点（新模型发布后常短期免费）~~
- ~~**网页说明**：社区 GPU 市场，热门新模型上架初期提供免费调用~~
- ~~**免费模型**：新发布开源模型（DeepSeek V4 Flash 当前是否在免费名单**未确认**，未列入索引）~~
- ~~**接入**：见官方文档~~
- ~~**状态**：Active（额度随时可能下架）— 核实于 2026-09-02~~

### 限时免费

#### B.AI

- **官网**：https://b.ai · API 文档：https://b.ai/docs
- **免费形式**：限时免费（4 个模型 0 Credits；**无公开截止日期，随时可能结束**）
- **网页说明**：AI Agent 基础设施平台；API 兼容 OpenAI / Anthropic 协议。**2026-09-03 起 DeepSeek V4 Flash 与 Vision Exp 已结束免费**，改为阶梯折扣（高峰 5 折、空闲低至官方价 2.5 折），其余 4 个模型仍为 0 Credits
- **免费模型**：GLM-5.3-Flash（Ox Alpha）、Qwen3.8 Flash、Hy3、MiMo-V2.5
- **接入**：`https://api.b.ai/v1`（国内访问不畅时用备用域名 `api.bankofai.io`，OpenAI 兼容）
- **状态**：Active（限时）— 核实于 2026-09-04

#### Experiential Labs

- **官网**：[https://platform.experientiallabs.ai](https://platform.experientiallabs.ai)（YC 背景，自称「开源版 OpenRouter」）
- **免费形式**：限时免费（Promotional 档，输入/输出全 $0；Free plan 月度配额刷新，新组织另送 welcome credits）
- **网页说明**：商业模式是「用免费流量换训练数据」——官方提供上传 traces 作为遥测的流程；免费层即获客投资，**额度随时可能收缩**
- **免费模型**：`Qwen3.8 27B free`（1M 上下文、192 tok/s、80.2% uptime）、`DeepSeek V4 Flash free`（1.05M、141 tok/s、100% uptime）、`GPT-5.6 Luna free`（1.05M、154 tok/s、97.5%）、`Claude Fable 5.1 free`（1M、86.9 tok/s、**72.5% uptime**）、`GPT-6 Astra free`（1.05M、88 tok/s、89%）——后两款原价均为 $10/$50
- **接入**：`https://api.experientiallabs.ai/v1`（OpenAI 兼容，需注册生成 key）
- **状态**：Active（限时）— 核实于 2026-09-12（⚠️ **免费层 uptime 偏低**：Claude Fable 5.1 仅 72.5%、TTFT 约 4.5 秒；1 credit = 1 美分，额度耗尽返回错误且**明确说明重试无效**；仅适合尝鲜，勿放入生产链路）

### 小型网关（谨慎）

> 以下新晋网关验证有限、免费额度随时可能关停或收费，**只适合原型验证，别托付生产负载**。

#### Token Harbor

- **官网**：https://tokenharbor.ai（[定价页](https://tokenharbor.ai/pricing)）
- **免费形式**：Free 档 $0/月，含每月免费额度（按 **4 周滚动**刷新，不过期结转）；另有 Agent Pass $1.99/月（首月 $0.99）
- **网页说明**：小型网关；官网定价页列 Free 档含 **DeepSeek V4 Flash、DeepSeek V4.1 Flash、MiMo V2.5** 三款，并称「Promotional models added over time」（免费名单会轮换）；注意免费请求可能被平台保存
- **免费模型**：DeepSeek V4 Flash、DeepSeek V4.1 Flash、MiMo V2.5
- **状态**：Active（小型网关）— 核实于 2026-09-12（⚠️ 免费额度**具体数额未公开**；免费档与付费 Pass 的额度**合并为一个池子**，订阅不会替换已有免费额度）

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
- **状态**：Active（小型网关）— 核实于 2026-09-05（⚠️ 实测经常调不通 `upstream_down`、繁忙时 503，仅适合原型调试）

#### AtomCode（CodingPlan）

- **官网**：https://ai.atomgit.com/serverless-api
- **免费形式**：CodingPlan Lite 体验版——限时免费、每日限量 500 人领取、7 天有效、约 200 次调用 / 5 小时
- **网页说明**：AtomGit（智谱生态）终端 AI 编程工具的免费额度；**非标准 API 渠道**——额度仅限 AtomCode 客户端内使用，不支持第三方 endpoint 调用
- **免费模型**：mimo-v2.5、qwen3.8-27b、deepseek-v4-flash（以客户端内列表为准）
- **接入**：安装 AtomCode 客户端，AtomGit 账号登录后自动领取（无公开 endpoint）
- **状态**：Active（限时）— 核实于 2026-09-05（严格说不符合本仓库"API Key + endpoint"收录标准，收录仅供了解）

#### BazaarLink

- **官网**：https://bazaarlink.ai（[免费模型规则](https://bazaarlink.ai/docs/api#free-models)）
- **免费形式**：免费模型档（`auto:free` 智能路由免费池 + `qwen/qwen3.7-flash:free`，输入/输出均 $0，限流使用、免绑卡注册）
- **网页说明**：台湾 LLM 网关，官网列「免費模型 1」并说明「免費額度，超出後自動轉為付費計價」；`auto:free` 会自动路由到当前最合适的免费模型
- **免费模型**：`auto:free`（智能路由免费池）、`qwen/qwen3.7-flash:free`（视觉语言推理模型）
- **接入**：`https://api.bazaarlink.ai/v1`（OpenAI 兼容）
- **状态**：Active（小型网关）— 核实于 2026-09-12（✅ 实测 `/v1/models` 171 个模型中 `auto:free` 与 `qwen/qwen3.7-flash:free` 的 pricing 均为 0，**免费层已恢复**，此前 2026-09-05 的「已失效」判断有误；⚠️ 2026-09-05 起停用 agent 自助注册端点（`/api/agents/register` 返回 410）以防免费层被滥用，需正常注册账号后在面板建 key）

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
- **免费名单的流动性比想象中大。** 2026-09-11 实测：OpenRouter 的 19 个 `:free` 模型中**已不含任何 DeepSeek / GLM / Qwen / MiniMax / Kimi / Llama 模型**；NVIDIA NIM 的 80 个模型中也**已移除 GLM、MiniMax、Qwen3.5、DeepSeek R1/V3、StepFun**——收录的模型可能在你看到时已经下架，用前务必跑一次 `curl` 确认。
- **"限时免费"随时可能结束。** 活动期 API（如 B.AI 的限时免费模型）没有公开的截止日期，消失也不会提前通知。
- **部分"免费"需要绑信用卡**才能开通，或需要手机号/实名验证。
- **你的数据可能被用于训练。** Google（免费层）、Mistral（Experiment 计划）、Groq 以及 OpenRouter 的 `:free` 上游普遍会在免费流量上做训练，部分支持关闭。
- **小型网关的免费额度最不稳定。** Token Harbor / BazaarLink 这类新晋网关验证有限、随时可能关停或收费，只适合原型验证，别托付生产负载。
- **"官方注册送额度"不等于免费。** 例如 DeepSeek 官方 API 的试用赠送已确认取消（2026-08-31 实测余额为 0），官方渠道现在是"低价"而非"免费"。

## 许可证

[MIT](LICENSE)——随便 fork、改写、发布，保留版权声明即可。
