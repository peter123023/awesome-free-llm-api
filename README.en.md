# Awesome Free LLM API

**English** | [简体中文](README.md)

> Channel-first: every channel below lists its official site, free tier, and what the site itself says about free access. Looking for the free channels of a specific model? See the [Model Index](#model-index) for flagship models.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

This list covers only APIs you can **keep calling** for free — **permanently free** tiers and models, plus APIs **explicitly labeled limited-time free**. **API access only**: it must be programmable via an API key and an HTTP endpoint. A free web chat UI (e.g. a provider's chat page) does **not** count.

Free LLM API info rots fast. Quotas change, rate limits get cut, and "free forever" becomes "free until next quarter". This list tries to stay honest about it: every channel carries a **status tag**, and all data here was verified on 2026-08-31.

---

## Table of Contents

- [Disclaimer](#disclaimer)
- [Scope](#scope)
- [Model Index](#model-index)
- [Free Channels](#free-channels)
  - [Official free tiers (global)](#official-free-tiers-global)
  - [China platforms](#china-platforms)
  - [Aggregators & gateways](#aggregators--gateways)
  - [Limited-time free](#limited-time-free)
  - [Small gateways (use with care)](#small-gateways-use-with-care)
- [Contributing](#contributing)
- [License](#license)

---

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

## Scope

Only **two** categories:

| Type | Meaning | Tag |
|------|---------|-----|
| **Permanent free tier** | Recurring quota that resets (per day / per month), no expiry | `permanent-free` |
| **Permanently free models** | Specific models free with no quota (only rate-limited) | `permanent-free` |
| **Limited / time-limited free** | Models or channels explicitly labeled "Limited-Time Free / Limited Free" | `limited-free` |

All of the above is **API-level free**: you get an API key and call it over an HTTP endpoint / SDK. A free web chat UI (e.g. a provider's chat page) does **not** count.

## Model Index

> Want a specific model? One table per model: column 1 = model name + official site, column 2 = description, column 3 = every channel serving it **for free right now** and how.
> **Ordering: China-native models first, generous & stable free tiers first, stronger models first within a tier.**
> Free lineups rotate often. This index is a **2026-09-02** verified snapshot; re-check the provider's site before relying on it. Full channel details (rate limits, endpoint, gotchas) live in [Free Channels](#free-channels).

### DeepSeek family

#### DeepSeek V4 Pro

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [DeepSeek V4 Pro](https://deepseek.com) | Flagship MoE, 1M context, strongest for coding & agents | [NVIDIA NIM](https://build.nvidia.com): permanent, 40 RPM, no daily cap |

#### DeepSeek V4 Flash

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [DeepSeek V4 Flash](https://deepseek.com) | 284B MoE, 1M context, best value for code / reasoning | [NVIDIA NIM](https://build.nvidia.com): permanent, 40 RPM; [ModelScope](https://modelscope.cn): ~200 req/day; [SenseNova](https://platform.sensenova.cn): free public beta, 1,500 req/5h; [B.AI](https://b.ai): limited-time free (0 Credits); [Hugging Face](https://huggingface.co): shared endpoint, rate-limited |

#### DeepSeek R1 / V3

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [DeepSeek R1 / V3](https://deepseek.com) | Deep-reasoning model / general flagship | [NVIDIA NIM](https://build.nvidia.com): permanent, 40 RPM; [ModelScope](https://modelscope.cn): R1 ~200 req/day; [SambaNova](https://cloud.sambanova.ai): 30 RPM; [Cloudflare](https://developers.cloudflare.com/workers-ai): R1 distilled, 10K Neurons/day; [OpenRouter](https://openrouter.ai): `:free` rotates, may be absent |

#### DeepSeek R2

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [DeepSeek R2](https://deepseek.com) | Next-gen general model | [Volcengine Ark](https://console.volcengine.com/ark): within collaboration-plan free quota (2M tokens/day, check console) |

### Qwen family

#### Qwen3.5 122B / 397B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Qwen3.5 122B / 397B](https://qwen.ai) | Alibaba flagship MoE, multimodal, agent-ready | [NVIDIA NIM](https://build.nvidia.com): permanent, 40 RPM; [ModelScope](https://modelscope.cn): shared quota |

#### Qwen3 Coder 480B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Qwen3 Coder 480B](https://qwen.ai) | SOTA coding model, agentic coding | [ModelScope](https://modelscope.cn): ~500 req/day; [OpenRouter](https://openrouter.ai): `:free` rotates |

#### Qwen3 235B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Qwen3 235B](https://qwen.ai) | General-purpose MoE flagship | [ModelScope](https://modelscope.cn): ~500 req/day; [OpenRouter](https://openrouter.ai): `:free` rotates |

#### Qwen3.8 Flash

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Qwen3.8 Flash](https://qwen.ai) | Lightweight multimodal, strong Chinese writing | [B.AI](https://b.ai): limited-time free; [Groq](https://console.groq.com): 1,000 req/day |

#### Qwen3.6 27B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Qwen3.6 27B](https://qwen.ai) | Lightweight general, multilingual | [Groq](https://console.groq.com): 1,000 req/day |

#### Qwen2.5 72B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Qwen2.5 72B](https://qwen.ai) | General large model | [SambaNova](https://cloud.sambanova.ai): 30 RPM; [ModelScope](https://modelscope.cn): shared quota |

#### Qwen3-8B / GLM-4-9B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Qwen3-8B / GLM-4-9B](https://qwen.ai) | 9B-class lightweight models | [SiliconFlow](https://cloud.siliconflow.cn): 9B-and-under permanently free |

### GLM family

#### GLM-5.3 Flash

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [GLM-5.3 Flash](https://z.ai) | Native multimodal, 320B, 1M context | [B.AI](https://b.ai): limited-time free (0 Credits) |

#### GLM 5.2 / 5.1

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [GLM 5.2 / 5.1](https://z.ai) | Agentic-workflow flagship | [NVIDIA NIM](https://build.nvidia.com): permanent, 40 RPM; [SenseNova](https://platform.sensenova.cn): free public beta (verified working) |

#### GLM-4.7-Flash / GLM-4-Flash

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [GLM-4.7-Flash / GLM-4-Flash](https://open.bigmodel.cn) | Zhipu's free lead-gen models, 200K context | [Zhipu BigModel](https://open.bigmodel.cn): permanently free, rate-limited only |

### Other China-native models

#### MiniMax M2.7

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [MiniMax M2.7](https://minimax.io) | 230B, coding / reasoning / office | [NVIDIA NIM](https://build.nvidia.com): permanent, 40 RPM |

#### MiniMax M3

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [MiniMax M3](https://minimax.io) | Multimodal MoE, reasoning / tool use | [NVIDIA NIM](https://build.nvidia.com): permanent (deprecation notice on site, use with care) |

#### Kimi K2.6

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Kimi K2.6](https://www.moonshot.cn) | 1T MoE, long-horizon coding, multimodal | [NVIDIA NIM](https://build.nvidia.com): permanent, 40 RPM |

#### StepFun Step 3.7 Flash

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [StepFun Step 3.7 Flash](https://www.stepfun.com) | China-native sparse-MoE reasoning model | [NVIDIA NIM](https://build.nvidia.com): permanent |

#### Doubao Lite

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Doubao Lite](https://www.volcengine.com/product/doubao) | ByteDance lightweight flagship | [Volcengine Ark](https://console.volcengine.com/ark): 2M tokens/day free |

#### Hunyuan Lite / Hy3

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Hunyuan Lite / Hy3](https://cloud.tencent.com/product/hunyuan) | Tencent general / flagship | [Tencent Hunyuan](https://cloud.tencent.com/product/hunyuan): Lite permanently free; [B.AI](https://b.ai): Hy3 limited-time free |

#### ERNIE-Speed / Lite

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [ERNIE-Speed / Lite](https://cloud.baidu.com/product/wenxinworkshop) | Baidu's free lightweight line | [Baidu Qianfan](https://cloud.baidu.com/product/wenxinworkshop): permanently free, rate-limited |

#### MiMo-V2.5

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [MiMo-V2.5](https://github.com/XiaomiMiMo) | Xiaomi multimodal reasoning | [B.AI](https://b.ai): limited-time free |

#### SenseNova 6.7 Flash-Lite

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [SenseNova 6.7 Flash-Lite](https://platform.sensenova.cn) | SenseTime native multimodal agent | [SenseNova](https://platform.sensenova.cn): free public beta, 1,500 req/5h |

### Global models

#### GPT-OSS 120B / 20B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [GPT-OSS 120B / 20B](https://openai.com) | OpenAI open-weight MoE, coding / reasoning | [Groq](https://console.groq.com): 1,000 req/day; [NVIDIA NIM](https://build.nvidia.com): permanent; [OpenRouter](https://openrouter.ai): `:free` |

#### Gemini 2.5 Flash / Flash-Lite

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Gemini 2.5 Flash / Flash-Lite](https://aistudio.google.com) | Google's free-tier workhorse, multimodal | [Google AI Studio](https://aistudio.google.com): daily reset (Flash ~1,500 req/day, Flash-Lite ~1,000 req/day) |

#### Nemotron 3 Ultra / Super

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Nemotron 3 Ultra / Super](https://build.nvidia.com) | NVIDIA agentic flagship, 1M context | [NVIDIA NIM](https://build.nvidia.com): permanent, 40 RPM; [OpenRouter](https://openrouter.ai): `:free` |

#### Llama 3.1 405B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Llama 3.1 405B](https://llama.com) | The largest open-weight model | [SambaNova](https://cloud.sambanova.ai): 30 RPM |

#### Llama 3.3 70B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Llama 3.3 70B](https://llama.com) | Classic general-purpose open model | [SambaNova](https://cloud.sambanova.ai): 30 RPM; [Cloudflare](https://developers.cloudflare.com/workers-ai): distilled, 10K Neurons/day |

#### Llama 4 Scout

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Llama 4 Scout](https://llama.com) | Fast & light, huge context | [SambaNova](https://cloud.sambanova.ai): 30 RPM; [OpenRouter](https://openrouter.ai): `:free` |

#### Mistral Large / Small / Codestral

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Mistral Large / Small / Codestral](https://mistral.ai) | European open flagships, coding / general | [Mistral](https://console.mistral.ai): Experiment tier (~1B tokens/month); [Cloudflare](https://developers.cloudflare.com/workers-ai): Small, 10K Neurons/day |

#### Gemma 4 31B

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Gemma 4 31B](https://deepmind.google) | Google open model, vision + text | [NVIDIA NIM](https://build.nvidia.com): permanent; [OpenRouter](https://openrouter.ai): `:free` |

#### Whisper

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Whisper](https://openai.com) | Speech-to-text | [Groq](https://console.groq.com): 2,000 req/day |

#### Embedding models

| Model (site) | Description | Free channels (free tier) |
|------|------|------|
| [Embedding models](https://mistral.ai) | Vectorization / retrieval | [Mistral](https://console.mistral.ai): Experiment tier; [Cloudflare](https://developers.cloudflare.com/workers-ai): 10K Neurons/day |

## Free Channels

> Channels are the protagonists. One entry per channel: **official site + free tier + what the site itself says about free access + free models**.
> **Ordering: stable official free tiers first, small gateways last; China platforms sit before other gateways within their group.**

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

#### Mistral La Plateforme

- **Official site**: https://console.mistral.ai
- **Free tier**: permanent (~1B tokens/month, Experiment plan)
- **What the site says**: Mistral's official free tier (Experiment) — generous quota, but data is used for training by default (can be turned off)
- **Free models**: Mistral Large / Small, Codestral, Embedding
- **Endpoint**: `https://api.mistral.ai/v1`
- **Status**: Active — verified 2026-08-31

#### SambaNova

- **Official site**: https://cloud.sambanova.ai
- **Free tier**: permanent (30 RPM, ~200K tokens/day, no total cap)
- **What the site says**: RDU-chip inference with a permanent free tier — one of the few places to touch 405B-class models for free
- **Free models**: Llama 3.1 405B, Llama 3.3 70B, Llama 4 Scout, Qwen 2.5 72B, DeepSeek R1 / V3 and more
- **Endpoint**: `https://api.sambanova.ai/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-09-02

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

### China platforms

#### ModelScope (Alibaba)

- **Official site**: https://modelscope.cn
- **Free tier**: permanent (free inference for all registered users, ~2,000 req/day total, 100~500 req/day per model)
- **What the site says**: Alibaba DAMO's open model community — "free inference for all registered users"; DeepSeek-R1 ~200 req/day
- **Free models**: DeepSeek V4 Flash / R1, Qwen3 Coder 480B, Qwen3 235B, Qwen2.5 72B, GLM-4.5, MiniMax-M1 and ~3,000 open models
- **Endpoint**: `https://api-inference.modelscope.cn/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-08-31 (Alibaba Cloud account + real-name verification required)

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

#### SenseNova (SenseTime)

- **Official site**: https://platform.sensenova.cn · Token Plan: https://www.sensenova.cn/token-plan
- **Free tier**: limited-time (open beta, fully free; paid Lite/Pro tiers coming soon)
- **What the site says**: "fully free during public beta, paid tiers launching soon"; 1,500 calls per model per 5 hours, auto-resets
- **Free models**: DeepSeek V4 Flash, GLM-5.2 (verified working), SenseNova 6.7 Flash-Lite (multimodal agent), SenseNova U1 Fast (infographics), SenseNova U1.5 Lite (image generation)
- **Endpoint**: `https://token.sensenova.cn/v1` (OpenAI-compatible; Anthropic-compatible endpoint also available)
- **Status**: Active (limited-time beta) — verified 2026-08-31 (phone signup; no card, no real-name)

### Aggregators & gateways

#### OpenRouter

- **Official site**: https://openrouter.ai
- **Free tier**: permanent (`:free` models, 50 req/day; 1000/day after $10 lifetime top-up)
- **What the site says**: multi-model router advertising 20+ free models; `openrouter/free` auto-routes between them
- **Free models**: GPT-OSS 120B / 20B, Nemotron 3 Ultra / Super, Gemma 4 31B, Qwen3 235B, Llama 4 Scout and more (**list rotates monthly** — DeepSeek / Mistral have been pulled entirely before; check `openrouter.ai/models?max_price=0` first)
- **Endpoint**: `https://openrouter.ai/api/v1` (append `:free` to the model name)
- **Status**: Active — verified 2026-08-31

#### Chutes

- **Official site**: https://chutes.ai
- **Free tier**: community GPU free endpoints (often free when a hot new model launches)
- **What the site says**: community GPU marketplace; new releases get free calls early on
- **Free models**: newly released open models (whether DeepSeek V4 Flash is currently free here is **unconfirmed** — not listed in the index)
- **Endpoint**: see official docs
- **Status**: Active (quota can disappear anytime) — verified 2026-09-02

### Limited-time free

#### B.AI

- **Official site**: https://b.ai · API docs: https://b.ai/docs
- **Free tier**: limited-time (6 models at 0 Credits during the promo, per the official announcement page; **no published end date, can end anytime**)
- **What the site says**: AI-agent infrastructure platform; the "activities & adjustments" page states these 6 models settle at 0 Credits; API is OpenAI- and Anthropic-compatible
- **Free models**: DeepSeek V4 Flash, DeepSeek V4 Flash Vision Exp (API only), GLM-5.3-Flash, Qwen3.8 Flash, Hy3, MiMo-V2.5
- **Endpoint**: `https://api.b.ai/v1` (use `api.bankofai.io` if the main domain is unreachable from China; OpenAI-compatible)
- **Status**: Active (limited-time) — verified 2026-09-02

### Small gateways (use with care)

> Barely battle-tested newcomers. Free quotas can disappear or turn paid anytime — **prototypes only, never production**.

#### Token Harbor

- **Official site**: https://tokenharbor.ai
- **Free tier**: `deepseek-v4-flash:free` / `mimo-v2.5:free`
- **What the site says**: small gateway; note that free requests may be saved by the platform
- **Free models**: DeepSeek V4 Flash, Mimo2.5
- **Status**: Active (small gateway) — verified 2026-08-31

#### OpenModel

- **Official site**: https://console.openmodel.ai
- **Free tier**: DeepSeek V4 Flash free
- **What the site says**: small gateway with an Anthropic-compatible endpoint
- **Free models**: DeepSeek V4 Flash
- **Status**: Active (small gateway) — verified 2026-08-31

#### BazaarLink

- **Official site**: https://bazaarlink.ai
- **Free tier**: Qwen3.7 Flash free (the only free model on the site right now)
- **What the site says**: small gateway, no credit card required; GPT / Gemini models are discounted, not free
- **Free models**: Qwen3.7 Flash
- **Status**: Active (small gateway) — verified 2026-08-31

## Contributing

Found a new permanent-free or limited-time-free channel? Quota changed? Help keep this list alive.

- **Scope gate**: only **permanent free** (recurring free tiers / permanently-free models) and **limited-time free** (explicitly labeled promos) **API** channels — the test is "can you get an API key and keep calling it for free over an endpoint?". A free web chat UI does not count.
- Adding a channel: follow the [Free Channels](#free-channels) format — name + official site + free tier + what the site says + free models — and sync the [Model Index](#model-index).
- When a channel loses free access entirely, mark the entry **Archived** (with a date) instead of silently deleting it.

Full template and rules: [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[MIT](LICENSE) — fork it, remix it, ship it; just keep the copyright notice.
