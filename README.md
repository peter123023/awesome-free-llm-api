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

#### DeepSeek V4 Pro

> 旗舰 MoE,1M 上下文,编程与智能体场景最强

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM 无每日上限 | 优势:官方托管、免绑卡、无每日上限;限制:40 RPM 全站共享,高峰期需排队 | 经常超时 |

#### DeepSeek V4 Flash

> 284B MoE,1M 上下文,代码 / 推理性价比首选

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [商汤 SenseNova](https://platform.sensenova.cn) | 公测免费,滚动 5h 60k 积分 | 优势:国产官方、公测期免费用量大;限制:限时公测,付费档即将上线 |  |
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | 每日 $10 等值额度 | 优势:AMD 官方 GPU 托管、OpenAI 兼容、免绑卡;限制:每日重置不过夜、TTFT 偏高(首字约 22 秒)、并发限流 | TTFT 偏高 |
| [Hugging Face](https://huggingface.co) | 共享端点限流 | 优势:免费、社区模型全;限制:共享端点限流严重、无 SLA | 限流严重 |
| [魔搭 ModelScope](https://modelscope.cn) | 约 200 次/日 | 优势:国产、OpenAI 兼容、模型全;限制:免费质量较低——单模型仅约 200 次/日,与全站共享 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管最稳、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### DeepSeek R1 / V3

> 深度推理模型 / 通用旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | R1 蒸馏版,1 万 Neurons/日 | 优势:边缘节点低延迟、每日免费;限制:仅蒸馏版非原版、额度小 |  |
| [OpenRouter](https://openrouter.ai) | `:free` 名单轮换,可能不含 | 优势:一站式聚合、OpenAI 兼容;限制:免费仅 50 次/天($10 后 1000),名单按月轮换 |  |
| [魔搭 ModelScope](https://modelscope.cn) | R1 约 200 次/日 | 优势:国产、模型全;限制:免费质量较低——R1 仅约 200 次/日,与全站共享 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

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
| [B.AI](https://b.ai) | 限时免费(0 Credits) | 优势:匿名免注册、输出 $0;限制:限时免费无截止日期,随时可能结束 |  |
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | 限时免费(ZZ.ai) | 优势:AMD 官方托管、每日 $10 等值额度;限制:限时免费、TTFT 偏高、并发限流 | TTFT 偏高 |

#### GLM 5.2 / 5.1

> 智能体工作流旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [商汤 SenseNova](https://platform.sensenova.cn) | 公测免费(实测可调,滚动 5h 60k 积分) | 优势:国产官方、公测免费且实测可调;限制:限时公测,付费档即将上线 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### GLM-4.7-Flash / GLM-4-Flash

> 智谱免费引流款,200K 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [智谱 BigModel](https://open.bigmodel.cn) | 永久免费,仅限速 | 优势:官方永久免费、200K 上下文、无需付费;限制:仅 Flash 小模型,有速率限制 |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |

### Qwen 系列

#### Qwen3.5 122B / 397B

> 阿里旗舰 MoE,多模态,智能体就绪

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [魔搭 ModelScope](https://modelscope.cn) | 共享额度内 | 优势:国产、模型全家桶;限制:免费质量较低——与全站共享每日 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### Qwen3 Coder 480B

> 代码专项 SOTA,Agent 编码

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` 名单轮换 | 优势:聚合路由、兼容多端;限制:免费仅 50 次/天,名单按月轮换 |  |
| [魔搭 ModelScope](https://modelscope.cn) | 约 500 次/日 | 优势:国产、模型全;限制:免费质量较低——单模型约 500 次/日,与全站共享 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |

#### Qwen3 235B

> 通用 MoE 旗舰

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` 名单轮换 | 优势:聚合路由、兼容多端;限制:免费仅 50 次/天,名单按月轮换 |  |
| [魔搭 ModelScope](https://modelscope.cn) | 约 500 次/日 | 优势:国产、模型全;限制:免费质量较低——单模型约 500 次/日,与全站共享 2000 次总量,需阿里云实名,仅限个人非商业用途 | 质量较低 |

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
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### MiniMax M3

> 多模态 MoE,推理 / 工具调用

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费(官方标注即将弃用) | 优势:官方托管、免绑卡;限制:官网标注即将弃用,慎用 | 经常超时 |

#### Kimi K2.6

> 1T MoE,长程编码,多模态

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方托管、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### StepFun Step 3.7 Flash

> 国产稀疏 MoE 推理模型

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费 | 优势:官方托管、免绑卡;限制:40 RPM 全站共享 | 经常超时 |

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
| [OpenRouter](https://openrouter.ai) | `:free` | 优势:聚合路由、兼容多端;限制:免费仅 50 次/天,名单按月轮换 |  |
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费 | 优势:官方托管、免绑卡;限制:40 RPM 全站共享 | 经常超时 |

#### Gemini 2.5 Flash / Flash-Lite

> Google 免费层主力,多模态

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Google AI Studio](https://aistudio.google.com) | 按天重置(Flash 约 1500 次/日、Flash-Lite 约 1000 次/日) | 优势:官方大额免费、免绑卡、多模态;限制:需 Google 账号,免费层数据可能用于改进产品 |  |

#### Nemotron 3 Ultra / Super

> NVIDIA 智能体旗舰,1M 上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` | 优势:聚合路由;限制:免费仅 50 次/天,名单按月轮换 |  |
| [Ollama Cloud](https://ollama.com) | 每月 starter 额度内(数额未公开) | 优势:Ollama 官方云托管、注册即用、无卡;限制:免费额度小且未公开、仅 1 并发,超额需购 credits |  |
| [AIHubMix](https://aihubmix.com/models/free) | $1 开通:每日 100 次/1M token | 优势:平台补贴免费、OpenAI 兼容、免卡注册;限制:未充值仅 10 次试用;全免费模型共享额度,部分模型配额更低 |  |
| [NVIDIA NIM](https://build.nvidia.com) | 永久免费,40 RPM | 优势:官方自营旗舰、免绑卡、无每日上限;限制:40 RPM 全站共享 | 经常超时 |

#### Llama 3.3 70B

> 通用开源经典

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | 蒸馏版,1 万 Neurons/日 | 优势:边缘节点低延迟;限制:蒸馏版非原版、每日额度小 |  |

#### Llama 4 Scout

> 轻量高速,超长上下文

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` | 优势:聚合路由;限制:免费仅 50 次/天,名单按月轮换 |  |

#### Mistral Large / Small / Codestral

> 欧洲开源旗舰,编码 / 通用

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | Small,1 万 Neurons/日 | 优势:边缘低延迟;限制:仅 Small 版、每日额度小 |  |

#### Gemma 4 31B

> Google 开源,视觉 + 文本

| 免费渠道 | 免费形式 | 优势 / 限制 | API 质量 |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` | 优势:聚合路由;限制:免费仅 50 次/天,名单按月轮换 |  |
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
- **免费模型**：DeepSeek V4 Flash / V4 Pro / R1、Qwen3.5 122B / 397B、GLM 5.2 / 5.1、MiniMax M2.7 / M3、Kimi K2.6、GPT-OSS、Gemma 4 31B、StepFun 3.7 Flash、Nemotron 3 Ultra / Super 等 100+
- **接入**：`https://integrate.api.nvidia.com/v1`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-09-02

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
- **免费模型**：deepseek-v4-flash、gemma4、glm-5.3-flash、gpt-oss:20b/120b、kimi-k2.6、minimax-m3、nemotron-3-super/ultra 等（starter 模型集合以官网为准）
- **接入**：`https://ollama.com/api/chat`（Ollama API；API Key：[https://ollama.com/settings/keys](https://ollama.com/settings/keys)）
- **状态**：Active — 核实于 2026-09-05（免费额度为月度 starter 用量、数额未公开；仅 1 并发）

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
- **免费形式**：限时免费（公测期完全免费，付费档位 Lite/Pro 即将上线）；TokenPlan 积分体系，通用积分池 + Flash-Lite 专属积分池各「滚动 5 小时 60,000 积分 / 滚动周 600,000 积分」
- **网页说明**：官网称"公测期完全免费开放，付费档位即将上线"；Flash-Lite 消费返赠——每消耗 1 专属积分返 1 通用积分（等效半价，返赠 30 天有效）；第三方模型额度低于自营
- **免费模型**：SenseNova 6.8 Flash-Lite（多模态智能体）、SenseNova U1 Fast（信息图生成）、SenseNova U1.5 Lite（图片创作）、DeepSeek V4 Flash / V4 Pro、GLM-5.2、Kimi K3（8 个模型定价均为 0，2026-09-08 API 实测）
- **接入**：`https://token.sensenova.cn/v1`（OpenAI 兼容，亦支持 Anthropic 兼容端点）
- **状态**：Active（限时公测）— 核实于 2026-09-08（手机号注册，免绑卡、免实名；8/31 前 6.7 请求自动重定向至 6.8；U1 系列去水印公测免费、转付费后需传 `watermark: false`）

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
- **免费形式**：永久免费（`:free` 模型 50 次/天；累计充值 $10 后 1000 次/天）
- **网页说明**：多模型聚合路由，官网标注 20+ 个免费模型，`openrouter/free` 可自动路由
- **免费模型**：GPT-OSS 120B / 20B、Nemotron 3 Ultra / Super、Gemma 4 31B、Qwen3 235B、Llama 4 Scout 等（**名单按月轮换**，DeepSeek / Mistral 曾整段下架，用前先查 `openrouter.ai/models?max_price=0`）
- **接入**：`https://openrouter.ai/api/v1`（模型名务必带 `:free` 后缀）
- **状态**：Active — 核实于 2026-08-31

#### AIHubMix

- **官网**：[https://aihubmix.com](https://aihubmix.com)（[免费模型专页](https://aihubmix.com/models/free)）
- **免费形式**：免费模型档（注册送 10 次试用、不过期；一次性充值 $1 起即永久转每日配额：100 次/日 · 1M token/日，每日重置）
- **网页说明**：官网标注「56 free models — no credit card required」——平台补贴推理成本，免费模型输入输出均 $0
- **免费模型**：glm-4.7-flash-free、hy3-free、minimax-m3-free、k2.6-code-preview-free、gpt-oss-20b-free、nemotron-3-ultra/super-free、gemma-4-31b-it-free、mimo-v2.5(-pro)-free、coding-glm-5.3-free、gpt-5.5-free、gemini-3.8-flash-free 等 56 个
- **接入**：`https://aihubmix.com/v1`（兼容 Chat Completions / Messages / Responses 三协议）
- **状态**：Active — 核实于 2026-09-05（充值 $1 才转每日配额；全免费模型共享额度池）

#### ~~Chutes~~（已失效）

~~已失效（2026-09-05 核实）：定价页 14 个模型全部标价（DeepSeek V4 Flash 0731 $0.44/$1.32），未发现免费端点；内容保留备查。~~

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

### 小型网关（谨慎）

> 以下新晋网关验证有限、免费额度随时可能关停或收费，**只适合原型验证，别托付生产负载**。

#### Token Harbor

- **官网**：https://tokenharbor.ai
- **免费形式**：`deepseek-v4-flash:free` / `mimo-v2.5:free`
- **网页说明**：小型网关；注意免费请求可能被平台保存
- **免费模型**：DeepSeek V4 Flash、Mimo2.5
- **状态**：Active（小型网关）— 核实于 2026-08-31

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

- **官网**：https://bazaarlink.ai
- **免费形式**：~~Qwen3.7 Flash 免费（全站目前仅此一个免费模型）~~ ⚠️ **已转付费**（定价页 2026-08-06 更新：$0.03 入 / $0.13 出 per 1M）
- **网页说明**：小型网关，免绑卡；GPT / Gemini 等模型为折扣价而非免费
- **免费模型**：Qwen3.7 Flash（已转付费）
- **状态**：~~Active（小型网关）— 核实于 2026-08-31~~ **已失效（2026-09-05）** —— 不再符合免费收录标准，条目保留备查

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
- **"限时免费"随时可能结束。** 活动期 API（如 B.AI 的限时免费模型）没有公开的截止日期，消失也不会提前通知。
- **部分"免费"需要绑信用卡**才能开通，或需要手机号/实名验证。
- **你的数据可能被用于训练。** Google（免费层）、Mistral（Experiment 计划）、Groq 以及 OpenRouter 的 `:free` 上游普遍会在免费流量上做训练，部分支持关闭。
- **小型网关的免费额度最不稳定。** Token Harbor / BazaarLink 这类新晋网关验证有限、随时可能关停或收费，只适合原型验证，别托付生产负载。
- **"官方注册送额度"不等于免费。** 例如 DeepSeek 官方 API 的试用赠送已确认取消（2026-08-31 实测余额为 0），官方渠道现在是"低价"而非"免费"。

## 许可证

[MIT](LICENSE)——随便 fork、改写、发布，保留版权声明即可。
