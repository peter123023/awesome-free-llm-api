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

- [免责声明](#免责声明)
- [收录范围](#收录范围)
- [模型免费渠道索引](#模型免费渠道索引)
- [免费渠道一览](#免费渠道一览)
  - [海外官方免费层](#海外官方免费层)
  - [中国平台](#中国平台)
  - [聚合与网关](#聚合与网关)
  - [限时免费](#限时免费)
  - [小型网关（谨慎）](#小型网关谨慎)
- [参与贡献](#参与贡献)
- [许可证](#许可证)

---

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

## 收录范围

本列表只收录**两类**：

| 类型 | 含义 | 标签 |
|------|------|------|
| **永久免费层** | 周期性额度（按天/月重置），不会过期 | `permanent-free` |
| **永久免费模型** | 指定模型完全免费，只有速率限制 | `permanent-free` |
| **限时/限量免费** | 明确标注"限时免费 / Limited-Time Free / 限量免费"的模型或渠道 | `limited-free` |

以上都限定为 **API 层面的免费**：能申请 API Key、能通过 HTTP endpoint / SDK 程序化调用。仅网页对话免费（如各家官网的 Chat 页面）不在此列。

## 模型免费渠道索引

> 想用哪个模型？每个模型一个表格：第一列是模型名称和官网地址，第二列是相关描述，第三列是它当前**所有免费渠道及免费形式**。
> **排序规则：国产模型在前、免费额度高且稳定的在前，同级别中能力强的在前。**
> 免费名单变动频繁，本索引为 **2026-09-02** 核实的快照；正式使用前请到对应官网二次确认。渠道详情（速率限制、接入地址、坑）见[免费渠道一览](#免费渠道一览)。

### DeepSeek 系列

#### DeepSeek V4 Pro

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [DeepSeek V4 Pro](https://deepseek.com) | 旗舰 MoE，1M 上下文，编程与智能体场景最强 | [NVIDIA NIM](https://build.nvidia.com)：永久免费，40 RPM 无每日上限 |

#### DeepSeek V4 Flash

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [DeepSeek V4 Flash](https://deepseek.com) | 284B MoE，1M 上下文，代码 / 推理性价比首选 | [NVIDIA NIM](https://build.nvidia.com)：永久免费，40 RPM；[魔搭 ModelScope](https://modelscope.cn)：约 200 次/日；[商汤 SenseNova](https://platform.sensenova.cn)：公测免费，每 5 小时 1500 次；[B.AI](https://b.ai)：限时免费（0 Credits）；[Hugging Face](https://huggingface.co)：共享端点限流 |

#### DeepSeek R1 / V3

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [DeepSeek R1 / V3](https://deepseek.com) | 深度推理模型 / 通用旗舰 | [NVIDIA NIM](https://build.nvidia.com)：永久免费，40 RPM；[魔搭 ModelScope](https://modelscope.cn)：R1 约 200 次/日；[SambaNova](https://cloud.sambanova.ai)：30 RPM；[Cloudflare](https://developers.cloudflare.com/workers-ai)：R1 蒸馏版，1 万 Neurons/日；[OpenRouter](https://openrouter.ai)：`:free` 名单轮换，可能不含 |

#### DeepSeek R2

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [DeepSeek R2](https://deepseek.com) | 新一代通用模型 | [火山方舟](https://console.volcengine.com/ark)：协作奖励计划免费额度内（每日 200 万 token，以控制台为准） |

### Qwen 系列

#### Qwen3.5 122B / 397B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Qwen3.5 122B / 397B](https://qwen.ai) | 阿里旗舰 MoE，多模态，智能体就绪 | [NVIDIA NIM](https://build.nvidia.com)：永久免费，40 RPM；[魔搭 ModelScope](https://modelscope.cn)：共享额度内 |

#### Qwen3 Coder 480B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Qwen3 Coder 480B](https://qwen.ai) | 代码专项 SOTA，Agent 编码 | [魔搭 ModelScope](https://modelscope.cn)：约 500 次/日；[OpenRouter](https://openrouter.ai)：`:free` 名单轮换 |

#### Qwen3 235B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Qwen3 235B](https://qwen.ai) | 通用 MoE 旗舰 | [魔搭 ModelScope](https://modelscope.cn)：约 500 次/日；[OpenRouter](https://openrouter.ai)：`:free` 名单轮换 |

#### Qwen3.8 Flash

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Qwen3.8 Flash](https://qwen.ai) | 轻量多模态，中文写作强 | [B.AI](https://b.ai)：限时免费；[Groq](https://console.groq.com)：1000 次/日 |

#### Qwen3.6 27B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Qwen3.6 27B](https://qwen.ai) | 轻量通用，多语言 | [Groq](https://console.groq.com)：1000 次/日 |

#### Qwen2.5 72B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Qwen2.5 72B](https://qwen.ai) | 通用大杯 | [SambaNova](https://cloud.sambanova.ai)：30 RPM；[魔搭 ModelScope](https://modelscope.cn)：共享额度内 |

#### Qwen3-8B / GLM-4-9B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Qwen3-8B / GLM-4-9B](https://qwen.ai) | 9B 级轻量模型 | [硅基流动](https://cloud.siliconflow.cn)：9B 及以下永久免费 |

### GLM 系列

#### GLM-5.3 Flash

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [GLM-5.3 Flash](https://z.ai) | 原生多模态，320B，1M 上下文 | [B.AI](https://b.ai)：限时免费（0 Credits） |

#### GLM 5.2 / 5.1

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [GLM 5.2 / 5.1](https://z.ai) | 智能体工作流旗舰 | [NVIDIA NIM](https://build.nvidia.com)：永久免费，40 RPM；[商汤 SenseNova](https://platform.sensenova.cn)：公测免费（实测可调） |

#### GLM-4.7-Flash / GLM-4-Flash

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [GLM-4.7-Flash / GLM-4-Flash](https://open.bigmodel.cn) | 智谱免费引流款，200K 上下文 | [智谱 BigModel](https://open.bigmodel.cn)：永久免费，仅限速 |

### 其他国产模型

#### MiniMax M2.7

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [MiniMax M2.7](https://minimax.io) | 230B，代码 / 推理 / 办公 | [NVIDIA NIM](https://build.nvidia.com)：永久免费，40 RPM |

#### MiniMax M3

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [MiniMax M3](https://minimax.io) | 多模态 MoE，推理 / 工具调用 | [NVIDIA NIM](https://build.nvidia.com)：永久免费（官方标注即将弃用，慎用） |

#### Kimi K2.6

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Kimi K2.6](https://www.moonshot.cn) | 1T MoE，长程编码，多模态 | [NVIDIA NIM](https://build.nvidia.com)：永久免费，40 RPM |

#### StepFun Step 3.7 Flash

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [StepFun Step 3.7 Flash](https://www.stepfun.com) | 国产稀疏 MoE 推理模型 | [NVIDIA NIM](https://build.nvidia.com)：永久免费 |

#### 豆包 Doubao Lite

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [豆包 Doubao Lite](https://www.volcengine.com/product/doubao) | 字节轻量旗舰 | [火山方舟](https://console.volcengine.com/ark)：每日 200 万 token 免费额度 |

#### 混元 Lite / Hy3

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [混元 Lite / Hy3](https://cloud.tencent.com/product/hunyuan) | 腾讯通用 / 旗舰 | [腾讯混元](https://cloud.tencent.com/product/hunyuan)：Lite 永久免费；[B.AI](https://b.ai)：Hy3 限时免费 |

#### ERNIE-Speed / Lite

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [ERNIE-Speed / Lite](https://cloud.baidu.com/product/wenxinworkshop) | 文心轻量免费款 | [百度千帆](https://cloud.baidu.com/product/wenxinworkshop)：永久免费，限速 |

#### MiMo-V2.5

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [MiMo-V2.5](https://github.com/XiaomiMiMo) | 小米多模态推理 | [B.AI](https://b.ai)：限时免费 |

#### SenseNova 6.7 Flash-Lite

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [SenseNova 6.7 Flash-Lite](https://platform.sensenova.cn) | 商汤原生多模态智能体 | [商汤](https://platform.sensenova.cn)：公测免费，每 5 小时 1500 次 |

### 海外模型

#### GPT-OSS 120B / 20B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [GPT-OSS 120B / 20B](https://openai.com) | OpenAI 开源 MoE，代码 / 推理强 | [Groq](https://console.groq.com)：1000 次/日；[NVIDIA NIM](https://build.nvidia.com)：永久免费；[OpenRouter](https://openrouter.ai)：`:free` |

#### Gemini 2.5 Flash / Flash-Lite

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Gemini 2.5 Flash / Flash-Lite](https://aistudio.google.com) | Google 免费层主力，多模态 | [Google AI Studio](https://aistudio.google.com)：按天重置（Flash 约 1500 次/日、Flash-Lite 约 1000 次/日） |

#### Nemotron 3 Ultra / Super

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Nemotron 3 Ultra / Super](https://build.nvidia.com) | NVIDIA 智能体旗舰，1M 上下文 | [NVIDIA NIM](https://build.nvidia.com)：永久免费，40 RPM；[OpenRouter](https://openrouter.ai)：`:free` |

#### Llama 3.1 405B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Llama 3.1 405B](https://llama.com) | 最大的开源模型 | [SambaNova](https://cloud.sambanova.ai)：30 RPM |

#### Llama 3.3 70B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Llama 3.3 70B](https://llama.com) | 通用开源经典 | [SambaNova](https://cloud.sambanova.ai)：30 RPM；[Cloudflare](https://developers.cloudflare.com/workers-ai)：蒸馏版，1 万 Neurons/日 |

#### Llama 4 Scout

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Llama 4 Scout](https://llama.com) | 轻量高速，超长上下文 | [SambaNova](https://cloud.sambanova.ai)：30 RPM；[OpenRouter](https://openrouter.ai)：`:free` |

#### Mistral Large / Small / Codestral

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Mistral Large / Small / Codestral](https://mistral.ai) | 欧洲开源旗舰，编码 / 通用 | [Mistral](https://console.mistral.ai)：Experiment 免费层（约 10 亿 token/月）；[Cloudflare](https://developers.cloudflare.com/workers-ai)：Small，1 万 Neurons/日 |

#### Gemma 4 31B

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Gemma 4 31B](https://deepmind.google) | Google 开源，视觉 + 文本 | [NVIDIA NIM](https://build.nvidia.com)：永久免费；[OpenRouter](https://openrouter.ai)：`:free` |

#### Whisper

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Whisper](https://openai.com) | 语音转写 | [Groq](https://console.groq.com)：2000 次/日 |

#### Embedding 模型

| 模型（官网） | 相关描述 | 免费渠道（免费形式） |
|------|------|------|
| [Embedding 模型](https://mistral.ai) | 向量化 / 检索 | [Mistral](https://console.mistral.ai)：Experiment 免费层；[Cloudflare](https://developers.cloudflare.com/workers-ai)：1 万 Neurons/日 |

## 免费渠道一览

> 渠道是主角。每个渠道一条：**官网 + 免费形式 + 官网上的免费说明 + 免费模型**。
> **排序规则：稳定的官方免费层在前，小型网关殿后；组内国内平台靠前。**

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

#### Mistral La Plateforme

- **官网**：https://console.mistral.ai
- **免费形式**：永久免费层（约 10 亿 token/月，Experiment 计划）
- **网页说明**：Mistral 官方平台免费层（Experiment），额度大但数据默认用于训练（可关闭）
- **免费模型**：Mistral Large / Small、Codestral、Embedding 模型
- **接入**：`https://api.mistral.ai/v1`
- **状态**：Active — 核实于 2026-08-31

#### SambaNova

- **官网**：https://cloud.sambanova.ai
- **免费形式**：永久免费层（30 RPM，每日约 20 万 token，不限总量）
- **网页说明**：RDU 自研芯片推理，官网提供永久免费层，是少数能免费摸到 405B 级模型的地方
- **免费模型**：Llama 3.1 405B、Llama 3.3 70B、Llama 4 Scout、Qwen 2.5 72B、DeepSeek R1 / V3 等
- **接入**：`https://api.sambanova.ai/v1`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-09-02

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

### 中国平台

#### 魔搭 ModelScope（阿里）

- **官网**：https://modelscope.cn
- **免费形式**：永久免费（所有注册用户免费推理，每日总 2000 次，单模型 100~500 次/日不等）
- **网页说明**：阿里达摩院开源模型社区，官网明确「所有注册用户均可免费推理」；DeepSeek-R1 约 200 次/日
- **免费模型**：DeepSeek V4 Flash / R1、Qwen3 Coder 480B、Qwen3 235B、Qwen2.5 72B、GLM-4.5、MiniMax-M1 等近 3000 个开源模型
- **接入**：`https://api-inference.modelscope.cn/v1`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-08-31（需阿里云账号 + 实名）

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

#### 腾讯混元

- **官网**：https://cloud.tencent.com/product/hunyuan
- **免费形式**：永久免费模型（混元-Lite 完全免费，仅速率限制）
- **网页说明**：腾讯云混元大模型，官网标注 Hunyuan-Lite 永久免费
- **免费模型**：混元-Lite（256K 上下文）
- **接入**：见官方文档
- **状态**：Active — 核实于 2026-08-31（QQ/微信登录）

#### 百度千帆

- **官网**：https://cloud.baidu.com/product/wenxinworkshop
- **免费形式**：永久免费模型（ERNIE-Speed/Lite 完全免费，有速率限制）
- **网页说明**：百度智能云千帆平台，官网标注 ERNIE-Speed / ERNIE-Lite 永久免费
- **免费模型**：ERNIE-Speed-128K、ERNIE-Lite（DeepSeek V4 是否在免费额度内**未能确认**，不收录）
- **接入**：`https://qianfan.baidubce.com/v2`（OpenAI 兼容）
- **状态**：Active — 核实于 2026-08-31（需实名）

#### 商汤 SenseNova（日日新）

- **官网**：https://platform.sensenova.cn · Token Plan：https://www.sensenova.cn/token-plan
- **免费形式**：限时免费（公测期完全免费，付费档位 Lite/Pro 即将上线）
- **网页说明**：官网称"公测期完全免费开放，付费档位即将上线"；每模型每 5 小时 1500 次调用，到点自动重置
- **免费模型**：DeepSeek V4 Flash、GLM-5.2（实测可调）、SenseNova 6.7 Flash-Lite（多模态智能体）、SenseNova U1 Fast（信息图生成）、SenseNova U1.5 Lite（图片创作）
- **接入**：`https://token.sensenova.cn/v1`（OpenAI 兼容，亦支持 Anthropic 兼容端点）
- **状态**：Active（限时公测）— 核实于 2026-08-31（手机号注册，免绑卡、免实名）

### 聚合与网关

#### OpenRouter

- **官网**：https://openrouter.ai
- **免费形式**：永久免费（`:free` 模型 50 次/天；累计充值 $10 后 1000 次/天）
- **网页说明**：多模型聚合路由，官网标注 20+ 个免费模型，`openrouter/free` 可自动路由
- **免费模型**：GPT-OSS 120B / 20B、Nemotron 3 Ultra / Super、Gemma 4 31B、Qwen3 235B、Llama 4 Scout 等（**名单按月轮换**，DeepSeek / Mistral 曾整段下架，用前先查 `openrouter.ai/models?max_price=0`）
- **接入**：`https://openrouter.ai/api/v1`（模型名务必带 `:free` 后缀）
- **状态**：Active — 核实于 2026-08-31

#### Chutes

- **官网**：https://chutes.ai
- **免费形式**：社区 GPU 免费端点（新模型发布后常短期免费）
- **网页说明**：社区 GPU 市场，热门新模型上架初期提供免费调用
- **免费模型**：新发布开源模型（DeepSeek V4 Flash 当前是否在免费名单**未确认**，未列入索引）
- **接入**：见官方文档
- **状态**：Active（额度随时可能下架）— 核实于 2026-09-02

### 限时免费

#### B.AI

- **官网**：https://b.ai · API 文档：https://b.ai/docs
- **免费形式**：限时免费（6 个模型活动期 0 Credits，官方公告页标注，**无公开截止日期，随时可能结束**）
- **网页说明**：AI Agent 基础设施平台；官网「活动与调整公告」明确 6 个模型按 0 Credits 结算；API 兼容 OpenAI / Anthropic 协议
- **免费模型**：DeepSeek V4 Flash、DeepSeek V4 Flash Vision Exp（仅 API）、GLM-5.3-Flash、Qwen3.8 Flash、Hy3、MiMo-V2.5
- **接入**：`https://api.b.ai/v1`（国内访问不畅时用备用域名 `api.bankofai.io`，OpenAI 兼容）
- **状态**：Active（限时）— 核实于 2026-09-02

### 小型网关（谨慎）

> 以下新晋网关验证有限、免费额度随时可能关停或收费，**只适合原型验证，别托付生产负载**。

#### Token Harbor

- **官网**：https://tokenharbor.ai
- **免费形式**：`deepseek-v4-flash:free` / `mimo-v2.5:free`
- **网页说明**：小型网关；注意免费请求可能被平台保存
- **免费模型**：DeepSeek V4 Flash、Mimo2.5
- **状态**：Active（小型网关）— 核实于 2026-08-31

#### OpenModel

- **官网**：https://console.openmodel.ai
- **免费形式**：DeepSeek V4 Flash 免费
- **网页说明**：小型网关，提供 Anthropic 兼容端点
- **免费模型**：DeepSeek V4 Flash
- **状态**：Active（小型网关）— 核实于 2026-08-31

#### BazaarLink

- **官网**：https://bazaarlink.ai
- **免费形式**：Qwen3.7 Flash 免费（全站目前仅此一个免费模型）
- **网页说明**：小型网关，免绑卡；GPT / Gemini 等模型为折扣价而非免费
- **免费模型**：Qwen3.7 Flash
- **状态**：Active（小型网关）— 核实于 2026-08-31

## 参与贡献

发现新的永久免费或限时免费渠道？额度变了？贡献让这份列表活下来。

- **收录门槛**：只收**永久免费**（周期性免费层 / 永久免费模型）和**限时免费**（明确标注活动期）的 **API** 渠道，判断标准是"能不能拿到 API Key、通过 endpoint 持续免费调用"。网页对话免费不算。
- 新增渠道时按[免费渠道一览](#免费渠道一览)的格式添加：名称 + 官网 + 免费形式 + 网页说明 + 免费模型，并在[模型免费渠道索引](#模型免费渠道索引)同步。
- 某渠道整体失去免费资格时，把对应条目标注 **Archived**（附日期），不要默默删掉。

完整模板和规则见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 许可证

[MIT](LICENSE)——随便 fork、改写、发布，保留版权声明即可。
