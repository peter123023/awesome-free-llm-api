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

#### DeepSeek V4 Pro

> Flagship MoE, 1M context, strongest for coding & agents

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM, no daily cap | Pros: official, no credit card, no daily cap; Cons: 40 RPM shared across all models | Frequent timeouts |

#### DeepSeek V4 Flash

> 284B MoE, 1M context, best value for code / reasoning

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [SenseNova](https://platform.sensenova.cn) | free public beta, 1,500 req/5h | Pros: official China platform, generous beta quota; Cons: limited-time beta, paid tiers coming |  |
| [Ollama Cloud](https://ollama.com) | monthly starter credits (amount unpublished) | Pros: official Ollama cloud hosting, sign up & go, no card; Cons: small unpublished free quota, 1 concurrent request, extra credits needed beyond it |  |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | ~$10/day credits | Pros: official AMD GPU hosting, OpenAI-compatible, no card; Cons: resets daily, high TTFT (~22s), rate-limited | High TTFT |
| [Hugging Face](https://huggingface.co) | shared endpoint, rate-limited | Pros: free, huge model catalog; Cons: heavily rate-limited shared endpoint, no SLA | Heavy rate limits |
| [ModelScope](https://modelscope.cn) | ~200 req/day | Pros: China-native, OpenAI-compatible, huge catalog; Cons: low-quality free tier — only ~200 req/day per model, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official & most stable, no credit card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### DeepSeek R1 / V3

> Deep-reasoning model / general flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | R1 distilled, 10K Neurons/day | Pros: low-latency edge inference; Cons: distilled not original, small daily quota |  |
| [OpenRouter](https://openrouter.ai) | `:free` rotates, may be absent | Pros: one API for many models; Cons: 50 free req/day (1,000 after $10), lineup rotates monthly |  |
| [ModelScope](https://modelscope.cn) | R1 ~200 req/day | Pros: China-native, huge catalog; Cons: low-quality free tier — R1 ~200/day, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

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
| [B.AI](https://b.ai) | limited-time free (0 Credits) | Pros: anonymous, $0 output; Cons: no end date published, could end anytime |  |
| [Ollama Cloud](https://ollama.com) | monthly starter credits (amount unpublished) | Pros: official Ollama cloud hosting, sign up & go, no card; Cons: small unpublished free quota, 1 concurrent request, extra credits needed beyond it |  |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | limited-time free (ZZ.ai) | Pros: official AMD hosting, ~$10/day; Cons: limited-time, high TTFT, rate-limited | High TTFT |

#### GLM 5.2 / 5.1

> Agentic-workflow flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [SenseNova](https://platform.sensenova.cn) | free public beta (verified working) | Pros: official China platform, verified working; Cons: limited-time beta, paid tiers coming |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### GLM-4.7-Flash / GLM-4-Flash

> Zhipu's free lead-gen models, 200K context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Zhipu BigModel](https://open.bigmodel.cn) | permanently free, rate-limited only | Pros: official, permanently free, 200K context; Cons: small Flash models only, rate-limited |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |

### Qwen family

#### Qwen3.5 122B / 397B

> Alibaba flagship MoE, multimodal, agent-ready

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [ModelScope](https://modelscope.cn) | within shared quota | Pros: China-native, full Qwen family; Cons: low-quality free tier — shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### Qwen3 Coder 480B

> SOTA coding model, agentic coding

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` rotates | Pros: aggregated routing, one API; Cons: 50 free req/day, rotates monthly |  |
| [ModelScope](https://modelscope.cn) | ~500 req/day | Pros: China-native, huge catalog; Cons: low-quality free tier — ~500/day, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |

#### Qwen3 235B

> General-purpose MoE flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` rotates | Pros: aggregated routing, one API; Cons: 50 free req/day, rotates monthly |  |
| [ModelScope](https://modelscope.cn) | ~500 req/day | Pros: China-native, huge catalog; Cons: low-quality free tier — ~500/day, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |

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
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### MiniMax M3

> Multimodal MoE, reasoning / tool use

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Ollama Cloud](https://ollama.com) | monthly starter credits (amount unpublished) | Pros: official Ollama cloud hosting, sign up & go, no card; Cons: small unpublished free quota, 1 concurrent request, extra credits needed beyond it |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent (deprecation notice on site) | Pros: official, no card; Cons: deprecation notice on site, use with care | Frequent timeouts |

#### Kimi K2.6

> 1T MoE, long-horizon coding, multimodal

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Ollama Cloud](https://ollama.com) | monthly starter credits (amount unpublished) | Pros: official Ollama cloud hosting, sign up & go, no card; Cons: small unpublished free quota, 1 concurrent request, extra credits needed beyond it |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### StepFun Step 3.7 Flash

> China-native sparse-MoE reasoning model

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | permanent | Pros: official, no card; Cons: 40 RPM shared | Frequent timeouts |

#### Doubao Lite

> ByteDance lightweight flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Volcano Ark](https://console.volcengine.com/ark) | 2M tokens/day free | Pros: large 2M tokens/day quota, China-native; Cons: needs account + real-name, check console |  |

#### Hunyuan Lite / Hy3

> Tencent general / flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Tencent Hunyuan](https://cloud.tencent.com/product/hunyuan) | Lite permanently free | Pros: official, permanently free; Cons: Lite only, needs Tencent Cloud account |  |
| [B.AI](https://b.ai) | Hy3 limited-time free | Pros: anonymous; Cons: limited-time, no end date |  |
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

#### SenseNova 6.7 Flash-Lite

> SenseTime native multimodal agent

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [SenseNova](https://platform.sensenova.cn) | free public beta, 1,500 req/5h | Pros: official, generous beta quota; Cons: limited-time beta, paid tiers coming |  |

### Global models

#### GPT-OSS 120B / 20B

> OpenAI open-weight MoE, coding / reasoning

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Groq](https://console.groq.com) | 1,000 req/day | Pros: LPU ultra-fast; Cons: 30 RPM / 1,000 RPD, 8K TPM |  |
| [OpenRouter](https://openrouter.ai) | `:free` | Pros: aggregated routing; Cons: 50 free req/day, rotates monthly |  |
| [Ollama Cloud](https://ollama.com) | monthly starter credits (amount unpublished) | Pros: official Ollama cloud hosting, sign up & go, no card; Cons: small unpublished free quota, 1 concurrent request, extra credits needed beyond it |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent | Pros: official, no card; Cons: 40 RPM shared | Frequent timeouts |

#### Gemini 2.5 Flash / Flash-Lite

> Google's free-tier workhorse, multimodal

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Google AI Studio](https://aistudio.google.com) | daily reset (Flash ~1,500 req/day, Flash-Lite ~1,000 req/day) | Pros: official, large free quota, no card, multimodal; Cons: needs Google account, free-tier data may be used for product improvement |  |

#### Nemotron 3 Ultra / Super

> NVIDIA agentic flagship, 1M context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` | Pros: aggregated routing; Cons: 50 free req/day, rotates monthly |  |
| [Ollama Cloud](https://ollama.com) | monthly starter credits (amount unpublished) | Pros: official Ollama cloud hosting, sign up & go, no card; Cons: small unpublished free quota, 1 concurrent request, extra credits needed beyond it |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: NVIDIA's own flagship, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |

#### Llama 3.3 70B

> Classic general-purpose open model

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | distilled, 10K Neurons/day | Pros: low-latency edge; Cons: distilled not original, small daily quota |  |

#### Llama 4 Scout

> Fast & light, huge context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` | Pros: aggregated routing; Cons: 50 free req/day, rotates monthly |  |

#### Mistral Large / Small / Codestral

> European open flagships, coding / general

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | Small, 10K Neurons/day | Pros: low-latency edge; Cons: Small only, small daily quota |  |

#### Gemma 4 31B

> Google open model, vision + text

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` | Pros: aggregated routing; Cons: 50 free req/day, rotates monthly |  |
| [Ollama Cloud](https://ollama.com) | monthly starter credits (amount unpublished) | Pros: official Ollama cloud hosting, sign up & go, no card; Cons: small unpublished free quota, 1 concurrent request, extra credits needed beyond it |  |
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
- **Free models**: DeepSeek V4 Flash / V4 Pro / R1, Qwen3.5 122B / 397B, GLM 5.2 / 5.1, MiniMax M2.7 / M3, Kimi K2.6, GPT-OSS, Gemma 4 31B, StepFun 3.7 Flash, Nemotron 3 Ultra / Super and 100+
- **Endpoint**: `https://integrate.api.nvidia.com/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-09-02

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

- **Official site**: https://ollama.com (cloud model catalog: https://ollama.com/search?c=cloud)
- **Free tier**: permanent (Free plan includes starter usage credits, refresh monthly, never expire; amount not published)
- **What the site says**: pricing page lists Free at $0 — "Starter usage credits included / Access to starter models"; cloud models bill per token against the credits; add credits to unlock all models
- **Free models**: deepseek-v4-flash, gemma4, glm-5.3-flash, gpt-oss:20b/120b, kimi-k2.6, minimax-m3, nemotron-3-super/ultra and more (starter lineup per the official site)
- **Endpoint**: `https://ollama.com/api/chat` (Ollama API; API key: https://ollama.com/settings/keys)
- **Status**: Active — verified 2026-09-05 (monthly starter credits, amount unpublished; 1 concurrent request)

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

#### Tencent Hunyuan

- **Official site**: https://cloud.tencent.com/product/hunyuan
- **Free tier**: permanent free model (Hunyuan-Lite fully free, rate-limited only)
- **What the site says**: Tencent Cloud marks Hunyuan-Lite as free forever
- **Free models**: Hunyuan-Lite (256K context)
- **Endpoint**: see official docs
- **Status**: Active — verified 2026-08-31 (QQ/WeChat login)

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
- **Free tier**: limited-time (open beta, fully free; paid Lite/Pro tiers coming soon)
- **What the site says**: "fully free during public beta, paid tiers launching soon"; 1,500 calls per model per 5 hours, auto-resets
- **Free models**: DeepSeek V4 Flash, GLM-5.2 (verified working), SenseNova 6.7 Flash-Lite (multimodal agent), SenseNova U1 Fast (infographics), SenseNova U1.5 Lite (image generation)
- **Endpoint**: `https://token.sensenova.cn/v1` (OpenAI-compatible; Anthropic-compatible endpoint also available)
- **Status**: Active (limited-time beta) — verified 2026-08-31 (phone signup; no card, no real-name)

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
- **Free tier**: permanent (`:free` models, 50 req/day; 1000/day after $10 lifetime top-up)
- **What the site says**: multi-model router advertising 20+ free models; `openrouter/free` auto-routes between them
- **Free models**: GPT-OSS 120B / 20B, Nemotron 3 Ultra / Super, Gemma 4 31B, Qwen3 235B, Llama 4 Scout and more (**list rotates monthly** — DeepSeek / Mistral have been pulled entirely before; check `openrouter.ai/models?max_price=0` first)
- **Endpoint**: `https://openrouter.ai/api/v1` (append `:free` to the model name)
- **Status**: Active — verified 2026-08-31

#### AIHubMix

- **Official site**: https://aihubmix.com (free model list: https://aihubmix.com/models/free)
- **Free tier**: free models (10 trial calls on signup, no expiry; a one-time $1+ top-up permanently switches to daily quotas: 100 req/day and 1M tokens/day, reset daily)
- **What the site says**: "56 free models — no credit card required"; the platform subsidizes inference cost — every free model bills $0 in & out
- **Free models**: glm-4.7-flash-free, hy3-free, minimax-m3-free, k2.6-code-preview-free, gpt-oss-20b-free, nemotron-3-ultra/super-free, gemma-4-31b-it-free, xiaomi-mimo-v2.5(-pro)-free, coding-glm-5.3-free, gpt-5.5-free, gemini-3.8-flash-free and 50+ more
- **Endpoint**: `https://aihubmix.com/v1` (Chat Completions / Messages / Responses compatible)
- **Status**: Active — verified 2026-09-05 ($1 top-up required for daily quotas; shared free pool)

#### ~~Chutes~~ (retired)

~~Retired (verified 2026-09-05): all 14 models on the pricing page carry prices (DeepSeek V4 Flash 0731 at $0.44/$1.32); no free endpoint found. Entry kept for reference.~~

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

### Small gateways (use with care)

> Barely battle-tested newcomers. Free quotas can disappear or turn paid anytime — **prototypes only, never production**.

#### Token Harbor

- **Official site**: https://tokenharbor.ai
- **Free tier**: `deepseek-v4-flash:free` / `mimo-v2.5:free`
- **What the site says**: small gateway; note that free requests may be saved by the platform
- **Free models**: DeepSeek V4 Flash, Mimo2.5
- **Status**: Active (small gateway) — verified 2026-08-31

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

- **Official site**: https://bazaarlink.ai
- **Free tier**: ~~Qwen3.7 Flash free (the only free model on the site right now)~~ ⚠️ **now paid** (pricing page updated 2026-08-06: $0.03 in / $0.13 out per 1M)
- **What the site says**: small gateway, no credit card required; GPT / Gemini models are discounted, not free
- **Free models**: Qwen3.7 Flash (now paid)
- **Status**: ~~Active (small gateway) — verified 2026-08-31~~ **retired (2026-09-05)** — no longer qualifies as free; entry kept for reference

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
- **"Limited-time free" can end without warning.** Promo APIs (e.g. B.AI's limited-time models) publish no end date.
- **Some "free" tiers require a credit card**, a phone number, or real-name verification.
- **Your data may be used for training.** Google (free tier), Mistral (Experiment), Groq, and most OpenRouter `:free` upstreams train on free traffic; some let you opt out.
- **Small gateways are the least stable.** Newcomers like Token Harbor / BazaarLink are barely battle-tested — fine for prototypes, never for production.
- **"Free signup credits" ≠ free.** DeepSeek's official signup grant is confirmed gone (balance 0 as of 2026-08-31); the official channel is now "cheap", not "free".

## License

[MIT](LICENSE) — fork it, remix it, ship it; just keep the copyright notice.
