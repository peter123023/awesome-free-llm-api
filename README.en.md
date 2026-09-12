# Awesome Free LLM API

**English** | [Chinese](README.md)

> Channel-first: every channel below lists its official site, free tier, and what the site itself says about free access. Looking for the free channels of a specific model? See the [Model Index](#model-index) for flagship models.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

This list covers only APIs you can **keep calling** for free — **permanently free** tiers and models, plus APIs **explicitly labeled limited-time free**. **API access only**: it must be programmable via an API key and an HTTP endpoint. A free web chat UI (e.g. a provider's chat page) does **not** count.


---

## Table of Contents

- [Scope](#scope)
- [Model Index](#model-index)
- [Free Channels](#free-channels)
  - [Official free tiers (global)](#official-free-tiers-global)
  - [China platforms](#china-platforms)
  - [Aggregators & gateways](#aggregators--gateways)
  - [Limited-time free](#limited-time-free)
  - [Small gateways (use with care)](#small-gateways-use-with-care)
- [Contributing](#contributing)
- [Disclaimer](#disclaimer)
- [License](#license)

---

## Scope

Only **two** categories:

| Type | Meaning | Tag |
|------|---------|-----|
| **Permanent free tier** | Recurring quota that resets (per day / per month), no expiry | `permanent-free` |
| **Permanently free models** | Specific models free with no quota (only rate-limited) | `permanent-free` |
| **Limited / time-limited free** | Models or channels explicitly labeled "Limited-Time Free / Limited Free" | `limited-free` |

All of the above is **API-level free**: you get an API key and call it over an HTTP endpoint / SDK. A free web chat UI (e.g. a provider's chat page) does **not** count.

## Model Index

### DeepSeek family

#### DeepSeek V4.1 Flash

> 552B new-architecture MoE (8B/16B active), native multimodal, 1M context; released 2026-09-10

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Token Harbor](https://tokenharbor.ai) | Within the free monthly allowance (renews on a 4-week rolling cycle) | Pros: small gateway, no card required, **the Free plan explicitly includes V4.1 Flash**; Cons: allowance undisclosed, renews every 4 weeks, gateway is young |  |

> ⚠️ **No official free tier, and third-party free entry points are scarce**: DeepSeek itself is paid only (off-peak $0.15/$0.60 per 1M). ⚠️ **Ollama Cloud is not a free entry point** — V4.1 Flash is in its cloud catalog, but it is a flagship model unlocked with purchased credits, while the free plan covers only the starter subset (verified 2026-09-12). ⚠️ **OrcaRouter does not offer free V4.1 either** — `deepseek/deepseek-v4.1-flash` is billed at $0.15/$0.60 on its price list, and its free pool holds only V4 Flash (`deepseek-v4-flash-free`) plus Hy3 and GLM-5.3-Flash (verified 2026-09-12). The only confirmed free entry point is the Token Harbor free plan.

#### ~~DeepSeek V4 Pro~~ (official routing retired from 2026-09-14)

> Flagship MoE, 1M context, strongest for coding & agents. ⚠️ From 2026-09-14 12:00 the official API routes all `deepseek-v4-pro` requests to V4.1 Flash at Flash rates, until V4.1 Pro ships

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM, no daily cap | Pros: official, no credit card, no daily cap; Cons: 40 RPM shared across all models | Frequent timeouts |
| [SenseNova](https://platform.sensenova.cn) | free public beta, rolling 5h 60k credits | Pros: official China platform, generous beta quota, 1M context; Cons: limited-time beta, paid tiers coming |  |

#### DeepSeek V4 Flash

> 284B MoE, 1M context, best value for code / reasoning. ⚠️ The official model id `deepseek-v4-flash` now auto-routes to V4.1 Flash; the legacy id still works

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [SenseNova](https://platform.sensenova.cn) | free public beta, rolling 5h 60k credits | Pros: official China platform, generous beta quota; Cons: limited-time beta, paid tiers coming |  |
| [Ollama Cloud](https://ollama.com) | Free plan includes a small starter allowance (amount unpublished, starter models only) | Pros: official cloud hosting, sign up & go, no card; Cons: ⚠️ the Free plan is **limited to the "starter models" subset — flagship models are not included**; calling V4.1 Flash requires buying credits (pay-per-token, off-peak $0.15/$0.60); allowance unpublished, 1 concurrent request | Paid to unlock |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official & most stable, no credit card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |
| [OrcaRouter](https://www.orcarouter.ai) | free pool, rate-limited, zero markup | Pros: 200+ models behind one gateway, 0% token markup, no card; Cons: free allowance unpublished, 429 rate limits, best-effort not production |  |
| [Hugging Face](https://huggingface.co) | shared endpoint, rate-limited | Pros: free, huge model catalog; Cons: heavily rate-limited shared endpoint, no SLA | Heavy rate limits |
| [ModelScope](https://modelscope.cn) | ~200 req/day | Pros: China-native, OpenAI-compatible, huge catalog; Cons: low-quality free tier — only ~200 req/day per model, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official & most stable, no credit card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### DeepSeek R1 / V3

> Deep-reasoning model / general flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | R1 distilled, 10K Neurons/day | Pros: low-latency edge inference; Cons: distilled not original, small daily quota |  |
| [OpenRouter](https://openrouter.ai) | `:free` rotates, may be absent | Pros: one API for many models; Cons: 50 free req/day (1,000 after $10), lineup rotates anytime |  |
| [ModelScope](https://modelscope.cn) | R1 ~200 req/day | Pros: China-native, huge catalog; Cons: low-quality free tier — R1 ~200/day, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |

> ⚠️ **DeepSeek R1 / V3 are no longer on NVIDIA NIM**: removed from the NIM model list as of 2026-09-11 (only V4 Flash 0731 and V4 Pro 0813 remain).

#### DeepSeek R2

> Next-gen general model

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Volcano Ark](https://console.volcengine.com/ark) | within collaboration-plan free quota (2M tokens/day) | Pros: large 2M tokens/day free quota; Cons: needs Volcengine account + real-name, check console |  |

### GLM family

#### GLM-5.3 Flash

> Native multimodal, 320B, 1M context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official hosting, no card, 1.3M context & multimodal, no daily cap; Cons: 40 RPM shared, queues at peak | Frequent timeouts |
| [OrcaRouter](https://www.orcarouter.ai) | free pool, rate-limited, zero markup | Pros: 200+ models behind one gateway, 0% token markup, no card; Cons: allowance unpublished, became the free default on 2026-09-07 replacing Qwen3.8-27B, high TTFT (~7.66s) | Rate-limited |
| [B.AI](https://b.ai) | limited-time free (0 Credits) | Pros: anonymous, $0 output; Cons: no end date published, could end anytime |  |
| [Ollama Cloud](https://ollama.com) | Free plan includes a small starter allowance (amount unpublished, starter models only) | Pros: official cloud hosting, sign up & go, no card; Cons: ⚠️ the Free plan is **limited to the "starter models" subset — flagship models are not included**; calling V4.1 Flash requires buying credits (pay-per-token, off-peak $0.15/$0.60); allowance unpublished, 1 concurrent request | Paid to unlock |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | limited-time free (ZZ.ai) | Pros: official AMD hosting, ~$10/day; Cons: limited-time, high TTFT, rate-limited | High TTFT |

#### GLM 5.2 / 5.1

> Agentic-workflow flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [SenseNova](https://platform.sensenova.cn) | free public beta (verified working, rolling 5h 60k credits) | Pros: official China platform, verified working; Cons: limited-time beta, paid tiers coming |  |
| [Ollama Cloud](https://ollama.com) | Free plan includes a small starter allowance (amount unpublished, starter models only) | Pros: official cloud hosting, sign up & go, no card; Cons: ⚠️ the Free plan is **limited to the "starter models" subset — flagship models are not included**; calling V4.1 Flash requires buying credits (pay-per-token, off-peak $0.15/$0.60); allowance unpublished, 1 concurrent request | Paid to unlock |
| [OpenCode Zen](https://opencode.ai/zen) | limited-time free models (GLM 5.3 Flash etc.) | Pros: official OpenCode gateway, no card; Cons: only the limited-time Flash tier is free, full GLM 5.3 is paid ($1.4/$4.4) |  |

> ✅ **GLM-5.3-Flash is now on NVIDIA NIM**: as of 2026-09-12, `integrate.api.nvidia.com/v1/models` returns 82 models including `z-ai/glm-5.3-flash` (1.3M context, multimodal, 40 RPM). Note this is not "the whole GLM family is back" — GLM 5.2 / 5.1 / 4.7 are still absent.

#### GLM-4.7-Flash / GLM-4-Flash

> Zhipu's free lead-gen models, 200K context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Zhipu BigModel](https://open.bigmodel.cn) | permanently free, rate-limited only | Pros: official, permanently free, 200K context; Cons: small Flash models only, rate-limited |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [OpenCode Zen](https://opencode.ai/zen) | limited-time free (in-client) | Pros: official OpenCode gateway, no card; Cons: limited-time, client-only, free lineup changes anytime |  |

> ⚠️ **GLM-4.7 is NOT in the NVIDIA NIM free lineup**: it appeared briefly in early September 2026 and was then removed; as of 2026-09-12 the only GLM newly added on NIM is `z-ai/glm-5.3-flash` — GLM-4.7 is still absent, so do not rely on it.

### Qwen family

#### Qwen3.5 122B / 397B

> Alibaba flagship MoE, multimodal, agent-ready

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [ModelScope](https://modelscope.cn) | within shared quota | Pros: China-native, full Qwen family; Cons: low-quality free tier — shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |

> ⚠️ **Qwen3.5 122B / 397B are no longer on NVIDIA NIM**: removed from the NIM model list as of 2026-09-11.

#### Qwen3 Coder 480B

> SOTA coding model, agentic coding

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [ModelScope](https://modelscope.cn) | ~500 req/day | Pros: China-native, huge catalog; Cons: low-quality free tier — ~500/day, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |

> ⚠️ **Qwen3 Coder 480B is no longer in the OpenRouter free lineup** (verified 2026-09-11).

#### Qwen3 235B

> General-purpose MoE flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [ModelScope](https://modelscope.cn) | ~500 req/day | Pros: China-native, huge catalog; Cons: low-quality free tier — ~500/day, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |

> ⚠️ **Qwen3 235B is no longer in the OpenRouter free lineup** (verified 2026-09-11).

#### Qwen3.8 Flash

> Lightweight multimodal, strong Chinese writing

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [B.AI](https://b.ai) | limited-time free | Pros: anonymous, $0 output; Cons: no end date published |  |
| [Groq](https://console.groq.com) | 1,000 req/day | Pros: LPU ultra-fast inference (700+ tok/s); Cons: 30 RPM / 1,000 RPD, 8K TPM |  |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | limited-time free (Qwen3.8-Flash-Next) | Pros: official AMD hosting, ~$10/day; Cons: limited-time, high TTFT, rate-limited | High TTFT |

#### Qwen3.6 27B

> Lightweight general, multilingual

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Groq](https://console.groq.com) | 1,000 req/day | Pros: LPU ultra-fast; Cons: 30 RPM / 1,000 RPD, 8K TPM |  |

#### Qwen2.5 72B

> General large model

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [ModelScope](https://modelscope.cn) | within shared quota | Pros: China-native, full Qwen family; Cons: low-quality free tier — shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |

#### Qwen3-8B / GLM-4-9B

> 9B-class lightweight models

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [SiliconFlow](https://cloud.siliconflow.cn) | 9B-and-under permanently free | Pros: China-native, all 9B-and-under free; Cons: only small models free |  |


### Other China-native models

#### MiniMax M2.7

> 230B, coding / reasoning / office

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenCode Zen](https://opencode.ai/zen) | MiniMax M3 limited-time free (in-client) | Pros: official OpenCode gateway; Cons: client-only, M2.7 itself is paid ($0.3/$1.2) |  |

> ⚠️ **MiniMax models have been pulled from NVIDIA NIM**: GLM-4.7 and MiniMax M2.1 were briefly listed in early September 2026, but both had been removed from the NIM model list as of 2026-09-11.

#### MiniMax M3

> Multimodal MoE, reasoning / tool use

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Ollama Cloud](https://ollama.com) | Free plan includes a small starter allowance (amount unpublished, starter models only) | Pros: official cloud hosting, sign up & go, no card; Cons: ⚠️ the Free plan is **limited to the "starter models" subset — flagship models are not included**; calling V4.1 Flash requires buying credits (pay-per-token, off-peak $0.15/$0.60); allowance unpublished, 1 concurrent request | Paid to unlock |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [OpenCode Zen](https://opencode.ai/zen) | limited-time free (in-client) | Pros: official OpenCode gateway, no card; Cons: limited-time, client-only |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent (deprecation notice on site) | Pros: official, no card; Cons: deprecation notice on site, use with care | Frequent timeouts |

#### MiniMax M2.1

> Enhanced multilingual coding, 204K context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| OpenCode Zen | ⚠️ deprecated (2026-03-15) | Pulled from OpenCode Zen; the official API is paid ($0.3/$1.2) |  |

#### Kimi K2.6

> 1T MoE, long-horizon coding, multimodal

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Ollama Cloud](https://ollama.com) | Free plan includes a small starter allowance (amount unpublished, starter models only) | Pros: official cloud hosting, sign up & go, no card; Cons: ⚠️ the Free plan is **limited to the "starter models" subset — flagship models are not included**; calling V4.1 Flash requires buying credits (pay-per-token, off-peak $0.15/$0.60); allowance unpublished, 1 concurrent request | Paid to unlock |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### Kimi K3

> 2.8T native multimodal agent, 1M context, long-horizon coding / complex reasoning

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [SenseNova](https://platform.sensenova.cn) | free public beta, rolling 5h 60k credits (quota/RPM limited) | Pros: official China platform, free beta, 1M context, native vision; Cons: limited-time beta, paid tiers coming, quota/RPM limited (occasional rate-limit in practice) |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### StepFun Step 3.7 Flash

> China-native sparse-MoE reasoning model

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| — | **not on NVIDIA NIM** | ⚠️ Removed from the NIM model list as of 2026-09-11; no free API channel at present |  |

#### Doubao Lite

> ByteDance lightweight flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Volcano Ark](https://console.volcengine.com/ark) | 2M tokens/day free | Pros: large 2M tokens/day quota, China-native; Cons: needs account + real-name, check console |  |

#### ~~Hunyuan Lite / Hy3~~ (Lite dies with the legacy platform on 9/30)

> Tencent general / flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| ~~[Tencent Hunyuan](https://cloud.tencent.com/product/hunyuan)~~ | ~~Lite permanently free~~ legacy platform shuts down 2026-09-30, TokenHub has no Lite | Pros: official, permanently free (ended with the legacy platform); Cons: Lite only (now defunct), needs Tencent Cloud account |  |
| [B.AI](https://b.ai) | Hy3 limited-time free | Pros: anonymous; Cons: limited-time, no end date |  |
| [OrcaRouter](https://www.orcarouter.ai) | free pool, rate-limited, zero markup | Pros: 200+ models behind one gateway, 0% token markup, no card; Cons: allowance unpublished, 429 rate limits, best-effort not production |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |

#### ERNIE-Speed / Lite

> Baidu's free lightweight line

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Baidu Qianfan](https://cloud.baidu.com/product/wenxinworkshop) | permanently free, rate-limited | Pros: official, permanently free; Cons: QPS 1, needs Baidu Cloud account |  |

#### MiMo-V2.5

> Xiaomi multimodal reasoning

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [B.AI](https://b.ai) | limited-time free | Pros: anonymous, $0 output; Cons: limited-time, no end date |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |

#### SenseNova 6.8 Flash-Lite

> SenseTime native multimodal agent (6.7 merged in; old ID auto-redirects until 8/31)

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [SenseNova](https://platform.sensenova.cn) | free public beta, rolling 5h 60k credits | Pros: official, generous beta quota, Flash-Lite rebate ~half price; Cons: limited-time beta, paid tiers coming |  |

### Global models

#### GPT-OSS 120B / 20B

> OpenAI open-weight MoE, coding / reasoning

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Groq](https://console.groq.com) | 1,000 req/day | Pros: LPU ultra-fast; Cons: 30 RPM / 1,000 RPD, 8K TPM |  |
| [Ollama Cloud](https://ollama.com) | Free plan includes a small starter allowance (amount unpublished, starter models only) | Pros: official cloud hosting, sign up & go, no card; Cons: ⚠️ the Free plan is **limited to the "starter models" subset — flagship models are not included**; calling V4.1 Flash requires buying credits (pay-per-token, off-peak $0.15/$0.60); allowance unpublished, 1 concurrent request | Paid to unlock |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent (20B only) | Pros: official, no card; Cons: 40 RPM shared, only hosts gpt-oss-20b | Frequent timeouts |

> ⚠️ **GPT-OSS is no longer in the OpenRouter free lineup** (verified 2026-09-11).

#### Gemini 2.5 Flash / Flash-Lite

> Google's free-tier workhorse, multimodal

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Google AI Studio](https://aistudio.google.com) | daily reset (Flash ~1,500 req/day, Flash-Lite ~1,000 req/day) | Pros: official, large free quota, no card, multimodal; Cons: needs Google account, free-tier data may be used for product improvement |  |

#### Nemotron 3 Ultra / Super / Lightning

> NVIDIA agentic flagship, 1M context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` (Ultra / Super / 3.5 Lightning) | Pros: aggregated routing; Cons: 50 free req/day, lineup rotates anytime |  |
| [Ollama Cloud](https://ollama.com) | Free plan includes a small starter allowance (amount unpublished, starter models only) | Pros: official cloud hosting, sign up & go, no card; Cons: ⚠️ the Free plan is **limited to the "starter models" subset — flagship models are not included**; calling V4.1 Flash requires buying credits (pay-per-token, off-peak $0.15/$0.60); allowance unpublished, 1 concurrent request | Paid to unlock |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: NVIDIA's own flagship, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### InKling / Ling 3.0 Flash (new OpenRouter free entries)

> Thinking Machines' InKling and Ant's Ling 3.0 Flash, both multimodal with 1M / 262K context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` (`inkling` / `inkling-small`, `ling-3.0-flash-sante` / `-fin` / `-vl`) | Pros: 1M-context multimodal, aggregated routing; Cons: 50 free req/day, lineup rotates anytime |  |

#### Llama 3.3 70B

> Classic general-purpose open model

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | distilled, 10K Neurons/day | Pros: low-latency edge; Cons: distilled not original, small daily quota |  |

#### ~~Llama 4 Scout~~ (no longer in the OpenRouter free lineup)

> Fast & light, huge context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| — | **no free channel** | ⚠️ As of 2026-09-11 no Llama model remains in the OpenRouter free lineup |  |

#### Mistral Large / Small / Codestral

> European open flagships, coding / general

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | Small, 10K Neurons/day | Pros: low-latency edge; Cons: Small only, small daily quota |  |

#### Gemma 4 31B / 26B

> Google open model, vision + text

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` (both 31B and 26B-A4B) | Pros: aggregated routing; Cons: 50 free req/day, lineup rotates anytime |  |
| [Ollama Cloud](https://ollama.com) | Free plan includes a small starter allowance (amount unpublished, starter models only) | Pros: official cloud hosting, sign up & go, no card; Cons: ⚠️ the Free plan is **limited to the "starter models" subset — flagship models are not included**; calling V4.1 Flash requires buying credits (pay-per-token, off-peak $0.15/$0.60); allowance unpublished, 1 concurrent request | Paid to unlock |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent | Pros: official, no card; Cons: 40 RPM shared | Frequent timeouts |

#### Whisper

> Speech-to-text

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Groq](https://console.groq.com) | 2,000 req/day | Pros: LPU ultra-fast transcription; Cons: 20 RPM / 2,000 RPD, audio-hours limited |  |

#### Embedding models

> Vectorization / retrieval

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | 10K Neurons/day | Pros: low-latency edge; Cons: small daily quota |  |


## Free Channels

### Official free tiers (global)

#### NVIDIA NIM

- **Official site**: https://build.nvidia.com
- **Free tier**: permanent (40 RPM shared site-wide, no daily cap)
- **What the site says**: "100+ models free to call" — NVIDIA-hosted inference endpoints, sign up and go, no credit card
- **Free models**: DeepSeek V4 Flash 0731 / V4 Pro 0813, Kimi K2.6 / K3, **z-ai/glm-5.3-flash**, Gemma 4 31B, Nemotron 3 Ultra / Super / Nano, GPT-OSS, Mistral Large and more (check the live `/v1/models`)
- **Endpoint**: `https://integrate.api.nvidia.com/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-09-12 (in practice `/v1/models` returns **82 models**; ✅ **`z-ai/glm-5.3-flash` newly added** (1.3M context, multimodal); ⚠️ MiniMax / Qwen / StepFun / Ling still absent, GLM 5.2 / 5.1 / 4.7 have not returned, and DeepSeek V4.1 Flash is not on NIM yet)

#### Google AI Studio

- **Official site**: https://aistudio.google.com
- **Free tier**: permanent (daily reset)
- **What the site says**: Google's official AI dev platform; the free tier exposes Gemini models over the API
- **Free models**: Gemini 2.5 Flash (~1,500 req/day), Flash-Lite (~1,000 req/day), Gemini 3.x Flash (preview, stricter limits); 2.5 Pro removed from the free tier (since 2026-04-01)
- **Endpoint**: `https://generativelanguage.googleapis.com/v1beta` (native SDK also available)
- **Status**: Active — verified 2026-08-31

#### Groq

- **Official site**: https://console.groq.com
- **Free tier**: permanent (daily reset, per-model limits)
- **What the site says**: "Blazing-fast inference" (LPU hardware, 700+ tok/s); developer free tier, no credit card
- **Free models**: GPT-OSS 120B / 20B, Qwen3.6-27B, Qwen3.8-27B, Groq Compound, Whisper and more (⚠️ Llama 3.x, Qwen3 32B and Kimi K2 left the free tier between June-August 2026)
- **Endpoint**: `https://api.groq.com/openai/v1`
- **Status**: Active — verified 2026-09-02

#### ~~Mistral La Plateforme~~ (free API tier discontinued)

- **Official site**: https://console.mistral.ai
- **Free tier**: ~~permanent (~1B tokens/month, Experiment plan)~~ ⚠️ **free API quota discontinued** (effective 2026-09-01): the free plan now only includes Le Chat / Vibe message allowances and $10/month API credits (subscription-gated) — no free API call quota anymore
- **What the site says**: Mistral's official platform; the old Experiment tier (~1B tokens/month) has been restructured and the free tier no longer works for API calls
- **Free models**: ~~Mistral Large / Small, Codestral, Embedding~~ (no free API quota left)
- **Endpoint**: `https://api.mistral.ai/v1` (paid only)
- **Status**: ~~Active — verified 2026-08-31~~ **retired (2026-09-07)** — free API tier discontinued; entry kept for reference

#### Cloudflare Workers AI

- **Official site**: https://developers.cloudflare.com/workers-ai
- **Free tier**: permanent (10,000 Neurons/day)
- **What the site says**: inference at Cloudflare's edge; free quota granted daily
- **Free models**: Llama 3.3 70B (distilled), Mistral Small, Embedding, DeepSeek R1 (distilled) and more
- **Endpoint**: REST (or `wrangler` bindings)
- **Status**: Active — verified 2026-08-31

#### Hugging Face

- **Official site**: https://huggingface.co
- **Free tier**: permanent (shared inference endpoints, rate-limited)
- **What the site says**: the largest open model hub, with free inference tokens (Inference API)
- **Free models**: thousands of community & official models (incl. DeepSeek V4 Flash)
- **Endpoint**: `https://router.huggingface.co/hf-inference` (`InferenceClient` / REST)
- **Status**: Active — verified 2026-08-31

#### AMD Token Factory (Radeon Cloud)

- **Official site**: https://developer.amd.com.cn/radeon/tokenfactory
- **Free tier**: ~$10 worth of credits daily, resets each day
- **What the site says**: AMD Radeon Cloud's official inference platform; log in to claim a daily free quota, OpenAI-compatible
- **Free models**: DeepSeek V4 Flash 0731 (Free), MiniCPM5-1B (Free), GLM-5.3-Flash (limited, ZZ.ai), Qwen3.8-Flash-Next (limited, AMD GPU Cloud)
- **Endpoint**: `https://developer.amd.com.cn/radeon/api/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-09-02 (high TTFT, ~22s first-token latency)

#### Ollama Cloud

- **Official site**: https://ollama.com ([pricing](https://ollama.com/pricing) · cloud model catalog: https://ollama.com/search?c=cloud)
- **Free tier**: Free plan at $0, including a small starter allowance (refreshes monthly, does not roll over, **exact amount unpublished**) that **covers only the "starter models" subset**
- **What the site says**: the pricing page states plainly — "Run models locally / Starter usage credits included / **Includes access to starter models** / Add credits to unlock **all** models". In other words, **the Free plan reaches only the starter subset; flagship models must be unlocked with purchased credits**. Pro is $20/mo ($60 credits included), Max $100/mo ($300 credits, 10 concurrent)
- **Available models (require purchased credits)**: deepseek-v4.1-flash ($0.15/$0.60 off-peak), deepseek-v4-pro, deepseek-v4-flash, glm-5.1 / 5.2 / 5.3 / 5.3-flash, kimi-k2.6 / k2.7-code / k3, minimax-m2.7 / m3, qwen3.5:397b, gpt-oss:20b / 120b, gemma4, nemotron-3-nano / super / ultra, mistral-large-3 (19 models in the cloud catalog)
- **Endpoint**: `https://ollama.com/api/chat` (Ollama API; API key: https://ollama.com/settings/keys — **calling without a key returns `{"error":"Unauthorized"}`**)
- **Status**: Active (**limited free scope**) — verified 2026-09-12 (⚠️ **important correction**: this entry previously claimed "V4.1 Flash is a free entry point", which was a misreading — the 19-20 models returned by `/api/tags` are merely the **cloud catalog**, not a free list. Calling `deepseek-v4.1-flash` without an API key returns Unauthorized, and **V4.1 Flash is a flagship model requiring purchased credits, not part of the free starter subset**. The Free plan's real value is a small undisclosed allowance on starter-size models; 1 concurrent request, allowance resets monthly from your signup date and does not roll over)

> ℹ️ **Strictly speaking this channel only partly meets the inclusion bar**: a free allowance exists but its size is unpublished, and **the official starter model list has never been published** — readers must check their own available models on the [settings page](https://ollama.com/settings). Most people signing in see only the local-model download entry on the Downloads page, which is expected — **cloud free allowances are not surfaced there**.

### China platforms


#### Meituan LongCat

- **Official site**: https://longcat.ai (platform docs: https://longcat.chat/platform/docs/zh/)
- **Free tier**: free credits on signup (daily allowance + one-time packs; exact amounts per the console's resource/usage page — third-party sources report ~500K tokens/day for regular accounts, raiseable on application)
- **What the site says**: Meituan's official LLM platform (LongCat-2.0, a 1.6T-parameter MoE); cache hits don't consume quota
- **Free models**: LongCat-2.0 (the only model in the official docs: 1M context / 128K max output, OpenAI & Anthropic formats)
- **Endpoint**: `https://api.longcat.chat/openai` (OpenAI-compatible) or `https://api.longcat.chat/anthropic` (Anthropic-compatible); create a key on the [API Keys page](https://longcat.chat/platform/api_keys)
- **Status**: Active — verified 2026-09-07 (429 with retry advice when rate-limited; official quota amount unpublished, check the console)

#### SiliconFlow

- **Official site**: https://cloud.siliconflow.cn
- **Free tier**: permanent (designated models at ¥0, list changes)
- **What the site says**: any model marked ¥0 in the model list is free forever; sign up and use
- **Free models**: Qwen3-8B, GLM-4-9B and other 9B-and-under models (not DeepSeek R1/V3 or other large models)
- **Endpoint**: `https://api.siliconflow.cn/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-08-31 (real-name verification required)

#### Zhipu AI

- **Official site**: https://open.bigmodel.cn
- **Free tier**: permanent free model (GLM-4.7-Flash fully free, rate-limited only)
- **What the site says**: Zhipu's official open platform marks GLM-4.7-Flash as free forever
- **Free models**: GLM-4.7-Flash (200K context, strong Chinese)
- **Endpoint**: `https://open.bigmodel.cn/api/paas/v4` (OpenAI-compatible)
- **Status**: Active — verified 2026-08-31 (real-name verification required)

#### Volcano Ark (ByteDance Doubao)

- **Official site**: https://console.volcengine.com/ark
- **Free tier**: permanent (collaboration-plan quota: 2M tokens/day, resets at midnight; mid/high-tier models like Doubao-Pro are paid)
- **What the site says**: ByteDance's model platform grants free quota daily
- **Free models**: Doubao-Lite (free), DeepSeek R2 / V3 (within free quota, check console)
- **Endpoint**: `https://ark.cn-beijing.volces.com/api/v3` (OpenAI-compatible)
- **Status**: Active — verified 2026-08-31 (phone + real-name required)

#### ~~Tencent Hunyuan~~ (legacy platform shuts down 9/30, no free model on the new one)

- **Official site**: https://cloud.tencent.com/product/hunyuan
- **Free tier**: ~~permanent free model (Hunyuan-Lite fully free, rate-limited only)~~ ⚠️ **free model discontinued with the legacy platform**: the Tencent Cloud legacy LLM platform (including the old Hunyuan entry) stopped selling and issuing new API keys on 2026-06-30, and **shuts down completely at 2026-09-30 00:00**; **hunyuan-lite is NOT in the model list of the new TokenHub platform**, officially recommended replacement is Hy3 preview (paid, new users get a 90-day free trial quota)
- **What the site says**: Tencent Cloud Hunyuan; existing legacy API keys keep working until 9/30, then stop for good
- **Free models**: ~~Hunyuan-Lite (256K context)~~ (dies with the legacy platform on 2026-09-30)
- **Endpoint**: legacy platform — see official docs; new TokenHub endpoint is `https://api.hunyuan.cloud.tencent.com/v1` (requires a new API key)
- **Status**: ~~Active — verified 2026-08-31~~ **expiring (2026-09-08)** — Hunyuan-Lite's "free forever" is over, no longer qualifies for inclusion, entry kept for reference

#### Baidu Qianfan

- **Official site**: https://cloud.baidu.com/product/wenxinworkshop
- **Free tier**: permanent free models (ERNIE-Speed / ERNIE-Lite fully free, rate-limited)
- **What the site says**: Baidu AI Cloud marks ERNIE-Speed / ERNIE-Lite as free forever
- **Free models**: ERNIE-Speed-128K, ERNIE-Lite (DeepSeek V4 within the free quota is **unconfirmed** — not listed)
- **Endpoint**: `https://qianfan.baidubce.com/v2` (OpenAI-compatible)
- **Status**: Active — verified 2026-08-31 (real-name verification required)

#### iFlytek Spark (Xinghuo)

- **Official site**: https://xinghuo.xfyun.cn/sparkapi
- **Free tier**: permanent free model (Spark Lite, unlimited tokens, rate-limited to QPS 2)
- **What the site says**: iFlytek's official platform; Spark Lite is permanently free for real-name-verified individual accounts, no token cap
- **Free models**: Spark Lite (lightweight, unlimited tokens, QPS 2)
- **Endpoint**: https://xinghuo.xfyun.cn/sparkapi (APIKey/APISecret auth; OpenAI-compatible endpoint per official docs)
- **Status**: Active — verified 2026-09-05 (real-name verification required)

#### SenseNova (SenseTime)

- **Official site**: https://platform.sensenova.cn · Token Plan: https://www.sensenova.cn/token-plan
- **Free tier**: limited-time (open beta, fully free; paid Lite/Pro tiers coming soon); TokenPlan credit system — the general pool and the Flash-Lite-specific pool **each** get **60,000 credits / rolling 5h** plus **600,000 credits / rolling week**
- **What the site says**: "fully free during public beta, paid tiers launching soon"; the Free tier covers SenseNova 6.8 Flash Lite and SenseNova U1 Fast, up to 20 API keys; Flash-Lite spend rebate — every 1 dedicated credit spent returns 1 general credit (rebate valid 30 days and **does not consume the rolling quota**, effectively half price); third-party models have lower quotas than first-party
- **Free models**: SenseNova 6.8 Flash-Lite (multimodal agent), SenseNova U1 Fast (infographics), SenseNova U1.5 Lite (image generation), DeepSeek V4 Flash / V4 Pro, GLM-5.2, Kimi K3 (all 8 models priced at 0, API-verified 2026-09-08)
- **Endpoint**: `https://token.sensenova.cn/v1` (OpenAI-compatible; Anthropic-compatible endpoint also available)
- **Status**: Active (limited-time beta) — verified 2026-09-12 (phone signup; no card, no real-name; ✅ the official docs confirm the beta Free tier is **¥0/month** with **no published end date**; ✅ `token.sensenova.cn/v1` responds correctly (401 without auth), while the widely-circulated `api.sensenova.cn/v1` returns 404 — **use `token.sensenova.cn/v1`**; measured latency is on the high side, and Kimi K3 burns credits fastest)

#### ModelScope (Alibaba)

- **Official site**: https://modelscope.cn
- **Free tier**: permanent (free inference for all registered users, ~2,000 req/day total, 100~500 req/day per model)
- **What the site says**: Alibaba DAMO's open model community — "free inference for all registered users"; DeepSeek-R1 ~200 req/day
- **Free models**: DeepSeek V4 Flash / R1, Qwen3 Coder 480B, Qwen3 235B, Qwen2.5 72B, GLM-4.5, MiniMax-M1 and ~3,000 open models
- **Endpoint**: `https://api-inference.modelscope.cn/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-09-02 (Alibaba Cloud account + real-name verification required)
- **⚠️ Low-quality free tier**: only ~100–500 req/day per model, shares the 2,000 req/day total pool (busy days can be crowded out); personal / non-commercial use only; shared GPUs may queue, no SLA

### Aggregators & gateways

#### OpenRouter

- **Official site**: https://openrouter.ai
- **Free tier**: permanent (`:free` models, 50 req/day and 20 req/min; 1000/day after a $10 lifetime top-up)
- **What the site says**: multi-model router exposing a `:free` lineup; `openrouter/free` auto-routes between them (⚠️ the widely-quoted "200 req/day" is outdated — the official limits page states 50/1000)
- **Free models**: `thinkingmachines/inkling(-small)` (1M-context multimodal), `nvidia/nemotron-3-ultra-550b`, `nemotron-3-super-120b`, `nemotron-3.5-lightning`, `gemma-4-26b-a4b`, `gemma-4-31b`, `inclusionai/ling-3.0-flash-sante/-fin/-vl`, `nex-agi/nex-n2.5-pro/-mini`, `cohere/north-mini-code`, `poolside/laguna-s-2.1/-xs-2.1`, `dots-studio/dots-3-note-preview` (512K), `liquid/lfm-2.5-2.6b` — **19 in total** (⚠️ **DeepSeek / GLM / Qwen / MiniMax / Kimi / Llama are all absent**; check `openrouter.ai/models?max_price=0` first)
- **Endpoint**: `https://openrouter.ai/api/v1` (append `:free` to the model name)
- **Status**: Active — verified 2026-09-12 (free lineup re-verified live: 19 `:free` models; 50 req/day, 1,000 after $10. ⚠️ the free pool churns daily — on 9/8 two MiniMax models left and two Nex AGI N2.5 models entered; "lands in the free pool on launch day" is a cold-start signal, not a long-term commitment, so always keep a fallback)

#### AIHubMix

- **Official site**: https://aihubmix.com (free model list: https://aihubmix.com/models/free)
- **Free tier**: free models (10 trial calls on signup, no expiry; a one-time $1+ top-up permanently switches to daily quotas: 100 req/day and 1M tokens/day, reset daily)
- **What the site says**: "56 free models — no credit card required"; the platform subsidizes inference cost — every free model bills $0 in & out
- **Free models**: glm-4.7-flash-free, hy3-free, minimax-m3-free, k2.6-code-preview-free, gpt-oss-20b-free, nemotron-3-ultra/super-free, gemma-4-31b-it-free, xiaomi-mimo-v2.5(-pro)-free, coding-glm-5.3-free, gpt-5.5-free, gemini-3.8-flash-free and 50+ more
- **Endpoint**: `https://aihubmix.com/v1` (Chat Completions / Messages / Responses compatible)
- **Status**: Active — verified 2026-09-05 ($1 top-up required for daily quotas; shared free pool)

#### OpenCode Zen

- **Official site**: [https://opencode.ai/zen](https://opencode.ai/zen) ([pricing](https://opencode.ai/docs/zen/))
- **Free tier**: limited-time free models (Big Pickle, MiMo-V2.5 Free, Ling 3.0 Flash Fin Free, Nemotron 3 Ultra Free, Nemotron 3.5 Lightning Free, Muse Spark 1.3 Contributor Free — $0 for input, output and cache read/write)
- **What the site says**: OpenCode's official model gateway; the pricing page explicitly marks those 6 models as Free and notes they are "available for a limited time while the team collects feedback"; **the platform itself is not free** — DeepSeek / GLM / Kimi / Qwen and the rest are pay-per-token
- **Free models**: Big Pickle (stealth model), MiMo-V2.5 Free, Ling 3.0 Flash Fin Free, Nemotron 3 Ultra Free, Nemotron 3.5 Lightning Free, Muse Spark 1.3 Contributor Free
- **Endpoint**: `https://opencode.ai/zen/v1` (OpenAI-compatible; some models use `/messages` Anthropic or `/responses`)
- **Status**: Active (limited-time) — verified 2026-09-11 (⚠️ the widely-cited `deepseek-v4-flash-free` is actually **paid** ($0.14/$0.28) and not on the free list)

#### OrcaRouter

- **Official site**: [https://www.orcarouter.ai](https://www.orcarouter.ai) ([docs](https://docs.orcarouter.ai))
- **Free tier**: free pool rate-limited per workspace (allowance unpublished); **0% token markup** on the paid side (pass-through at upstream list price)
- **What the site says**: an OpenAI-compatible LLM routing gateway with 200+ models behind one endpoint; free models are catalog models exposed under separate free IDs with identical weights/capabilities, running in an isolated rate-limited pool — **a saturated free model will not silently fall back to its paid counterpart**
- **Free models**: `orcarouter/free` (difficulty-aware routing across the free pool), `z-ai/glm-5.3-flash-free`, `deepseek/deepseek-v4-flash-free`, `tencent/hy3-free` (4 free of 195 models in the live `/v1/models` on 2026-09-12)
- **Endpoint**: `https://api.orcarouter.ai/v1` (OpenAI-compatible, no card required)
- **Status**: Active (rate-limited) — verified 2026-09-12 (on 2026-09-07 the free default switched from Qwen3.8-27B to GLM-5.3 Flash: quality score 4→8, context 262K→1M, but TTFT 1.96s→7.66s and throughput 196→74 tok/s; ⚠️ accounts that never purchased credit get a smaller daily allowance, `429 + Retry-After` means the window is full while a 429 without the header means the prompt is too long; the vendor explicitly calls it best-effort, not production capacity)

#### Chutes ~~(retired)~~

~~Retired (re-confirmed 2026-09-12): `llm.chutes.ai/v1/models` does list 30+ models, but the official pricing page **prices every one of them** (DeepSeek V4 Flash 0731 at $0.44/$1.32, Kimi K3 at $3.00/$15.00) — no free endpoint found. Entry kept for reference.~~

- ~~**Official site**: https://chutes.ai~~
- ~~**Free tier**: community GPU free endpoints (often free when a hot new model launches)~~
- ~~**What the site says**: community GPU marketplace; new releases get free calls early on~~
- ~~**Free models**: newly released open models (whether DeepSeek V4 Flash is currently free here is **unconfirmed** — not listed in the index)~~
- ~~**Endpoint**: see official docs~~
- ~~**Status**: Active (quota can disappear anytime) — verified 2026-09-02~~

### Limited-time free

#### B.AI

- **Official site**: https://b.ai · API docs: https://b.ai/docs
- **Free tier**: limited-time (4 models at 0 Credits; **no published end date, can end anytime**)
- **What the site says**: AI-agent infrastructure platform; API is OpenAI- and Anthropic-compatible. **Since 2026-09-03 DeepSeek V4 Flash and Vision Exp are no longer free** — they moved to tiered discounts (50% off at peak, down to 25% of list price off-peak); the other 4 models remain at 0 Credits
- **Free models**: GLM-5.3-Flash (Ox Alpha), Qwen3.8 Flash, Hy3, MiMo-V2.5
- **Endpoint**: `https://api.b.ai/v1` (use `api.bankofai.io` if the main domain is unreachable from China; OpenAI-compatible)
- **Status**: Active (limited-time) — verified 2026-09-04

#### Experiential Labs

- **Official site**: [https://platform.experientiallabs.ai](https://platform.experientiallabs.ai) (YC-backed; calls itself "the open-source OpenRouter")
- **Free tier**: limited-time (Promotional tier, $0 in / $0 out; the Free plan quota refreshes monthly and new organizations get welcome credits)
- **What the site says**: the business model is "free traffic in exchange for training data" — the platform documents a flow for uploading traces as telemetry, so the free tier is a customer-acquisition investment and **the allowance can shrink at any time**
- **Free models**: `Qwen3.8 27B free` (1M context, 192 tok/s, 80.2% uptime), `DeepSeek V4 Flash free` (1.05M, 141 tok/s, 100% uptime), `GPT-5.6 Luna free` (1.05M, 154 tok/s, 97.5%), `Claude Fable 5.1 free` (1M, 86.9 tok/s, **72.5% uptime**), `GPT-6 Astra free` (1.05M, 88 tok/s, 89%) — the latter two list at $10/$50
- **Endpoint**: `https://api.experientiallabs.ai/v1` (OpenAI-compatible, register for a key)
- **Status**: Active (limited-time) — verified 2026-09-12 (⚠️ **low uptime on the free tier**: Claude Fable 5.1 only 72.5%, TTFT ~4.5s; 1 credit = 1 cent, and once depleted it returns an error that **explicitly says retrying will not help**; for tasting only, do not put it in a production path)

### Small gateways (use with care)

> Barely battle-tested newcomers. Free quotas can disappear or turn paid anytime — **prototypes only, never production**.

#### Token Harbor

- **Official site**: https://tokenharbor.ai ([pricing](https://tokenharbor.ai/pricing))
- **Free tier**: Free plan at $0/month with a monthly free allowance (renews on a **4-week rolling** cycle; unused room does not carry forward); Agent Pass at $1.99/month ($0.99 first month)
- **What the site says**: small gateway; the pricing page lists **DeepSeek V4 Flash, DeepSeek V4.1 Flash and MiMo V2.5** on the Free plan and notes "Promotional models added over time" (the lineup rotates); note that free requests may be saved by the platform
- **Free models**: DeepSeek V4 Flash, DeepSeek V4.1 Flash, MiMo V2.5
- **Status**: Active (small gateway) — verified 2026-09-12 (⚠️ the **exact allowance is unpublished**; the free allowance and any paid Pass pool into **one shared pool**, and subscribing does not replace the free allowance)

#### TokenRouter

- **Official site**: https://tokenrouter.com (free model page: https://www.tokenrouter.com/models/qwen/qwen3.8-max-free/)
- **Free tier**: qwen3.8-max-free at $0 in / $0 out; also deepseek-v4-pro-0813-free, nemotron-3-nano-omni-free, etc. (limited free compute)
- **What the site says**: OpenAI-compatible model router; the model page lists qwen3.8-max-free at $0 in / $0 out; new launches often get a free tier early on
- **Free models**: Qwen3.8 Max, DeepSeek V4 Pro (0813-free), Nemotron-3-Nano-Omni (per the site's current $0 listings)
- **Endpoint**: `https://api.tokenrouter.com/v1` (OpenAI-compatible; sign up to generate an API key)
- **Status**: Active (small gateway) — verified 2026-09-05 (official note: limited free compute, stability and concurrency not guaranteed; free flagship spots vanish fast)

#### Empero

- **Official site**: https://free.empero.org
- **Free tier**: completely free, no signup (any API key works; use `free` if one is required)
- **What the site says**: community free endpoint by EmperoAI, an independent German AI lab; prompts and responses are logged (IPs hashed) to train their open models — do not send private data
- **Free models**: glm-5.3-flash, qwen3.8-flash (a.k.a. Flash-Next), Qwen3.8-27B-FP8 and more (lineup rotates often; see the site)
- **Endpoint**: `https://free.empero.org/v1` (OpenAI-compatible, any key)
- **Status**: Active (small gateway) — verified 2026-09-05 (⚠️ often unreachable in practice — `upstream_down`; 503 when busy; prototypes only)

#### AtomCode (CodingPlan)

- **Official site**: https://ai.atomgit.com/serverless-api
- **Free tier**: CodingPlan Lite trial — limited-time free, 500 claims/day, valid 7 days, ~200 calls per 5h rolling window
- **What the site says**: free quota inside AtomCode, the terminal AI coding tool from AtomGit (Zhipu ecosystem); **not a standard API channel** — the quota only works inside the AtomCode client, no third-party endpoint access
- **Free models**: mimo-v2.5, qwen3.8-27b, deepseek-v4-flash (per the client's model list)
- **Endpoint**: none public — install the AtomCode client and sign in with an AtomGit account to claim the quota
- **Status**: Active (limited-time) — verified 2026-09-05 (does not really meet this repo's "API key + endpoint" bar; listed for reference only)

#### BazaarLink

- **Official site**: https://bazaarlink.ai ([free-model rules](https://bazaarlink.ai/docs/api#free-models))
- **Free tier**: free model tier (`auto:free` smart routing across the free pool plus `qwen/qwen3.7-flash:free`, $0 in / $0 out, rate-limited, no card required)
- **What the site says**: a Taiwan-based LLM gateway; the site lists "1 free model" and notes "free allowance, auto-switching to paid billing beyond it"; `auto:free` routes to whichever free model currently fits best
- **Free models**: `auto:free` (free-pool smart routing), `qwen/qwen3.7-flash:free` (vision-language reasoning model)
- **Endpoint**: `https://api.bazaarlink.ai/v1` (OpenAI-compatible)
- **Status**: Active (small gateway) — verified 2026-09-12 (✅ live `/v1/models` returns 171 models, with both `auto:free` and `qwen/qwen3.7-flash:free` priced at 0 — **the free tier has been restored**; the earlier "retired 2026-09-05" call was wrong. ⚠️ since 2026-09-05 the self-serve agent registration endpoint (`/api/agents/register`) returns 410 to curb free-tier abuse — register normally and create a key in the dashboard)

## Contributing

Found a new permanent-free or limited-time-free channel? Quota changed? Help keep this list alive.

- **Scope gate**: only **permanent free** (recurring free tiers / permanently-free models) and **limited-time free** (explicitly labeled promos) **API** channels — the test is "can you get an API key and keep calling it for free over an endpoint?". A free web chat UI does not count.
- Adding a channel: follow the [Free Channels](#free-channels) format — name + official site + free tier + what the site says + free models — and sync the [Model Index](#model-index).
- When a channel loses free access entirely, mark the entry **Archived** (with a date) instead of silently deleting it.

Full template and rules: [CONTRIBUTING.md](CONTRIBUTING.md).

## Disclaimer

> **Quotas, rate limits, and terms on this page can change at any time without notice.**
> This list is a snapshot. Always double-check the official pricing page before shipping anything to production.

Known sources of drift, flagged explicitly in each entry:

- **A "free tier" is not "free forever".** Google cut Gemini free quotas by ~80% in December 2025; others may follow.
- **Free lineups churn more than you think.** Verified 2026-09-11: none of OpenRouter's 19 `:free` models is a DeepSeek / GLM / Qwen / MiniMax / Kimi / Llama model; NVIDIA NIM's 80 models no longer include GLM, MiniMax, Qwen3.5, DeepSeek R1/V3 or StepFun — a model listed here may already be gone when you read it, so run a `curl` check first.
- **"Limited-time free" can end without warning.** Promo APIs (e.g. B.AI's limited-time models) publish no end date.
- **Some "free" tiers require a credit card**, a phone number, or real-name verification.
- **Your data may be used for training.** Google (free tier), Mistral (Experiment), Groq, and most OpenRouter `:free` upstreams train on free traffic; some let you opt out.
- **Small gateways are the least stable.** Newcomers like Token Harbor / BazaarLink are barely battle-tested — fine for prototypes, never for production.
- **"Free signup credits" ≠ free.** DeepSeek's official signup grant is confirmed gone (balance 0 as of 2026-08-31); the official channel is now "cheap", not "free".

## License

[MIT](LICENSE) — fork it, remix it, ship it; just keep the copyright notice.
