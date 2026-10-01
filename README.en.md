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
- [Stealth Models](#stealth-models)
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

## Stealth Models

> Models that **do not reveal who is behind them**: no vendor name, no verifiable model codename — just a handle and a limited-time free upstream deal. They don't fit the named model index below (nowhere to put them, no way to judge strength), so they get their own section.

Stealth models are not like the other channels in this list. Up front, the properties that matter:

| Property | What it means |
|----------|---------------|
| **Identity unknown** | The developer is undisclosed and the `tokenizer` is usually reported as `Other`. Third-party testing has found a tokenizer fingerprint close to the MiniMax family — that is **fingerprint similarity, not official confirmation**, so don't treat it as a MiniMax model |
| **Can vanish at any time** | There is no public stability commitment. These are typically short evaluation windows ahead of a launch; there is no telling when the model is pulled or switched to paid |
| **No capability baseline** | No public benchmark leaderboard. Claims about context size or coding ability come from single-party reviews and should not be treated as conclusions |
| **Privacy terms differ by channel** | The **same model** has completely different data-handling policies on different gateways — some zero-retention and no-training, some explicitly stating "data collected during the free period may be used to improve the model". See the table below |

| Model | Free channel | Free tier | Context / Max output | Data policy | Notes |
|-------|--------------|-----------|----------------------|-------------|-------|
| **Space Bunny Alpha** | [OpenRouter](https://openrouter.ai) | Limited-time free (`stealth/space-bunny-alpha`, $0 input and output) | 1M / 524,288 | ⚠️ Official wording: prompts and completions **may be retained** by the provider, but are **not used for training** | ✅ Measured `pricing` fields `prompt=0`, `completion=0`; 3-day availability 98.82%, throughput 89 tok/s, TTFT 1.36s |
| **Space Bunny Alpha** | [OpenCode Zen](https://opencode.ai/zen) | Limited-time free (`space-bunny-free`, $0 across Input / Output / Cached Read) | 1M / 524,288 | ✅ **Zero retention, not used for training** (OpenCode Zen's own wording) | The model ID differs per channel: Zen uses the `-free` suffix, OpenRouter has **no** `:free` suffix |

- **Endpoints**:
  - OpenRouter: `POST https://openrouter.ai/api/v1/chat/completions`, model `stealth/space-bunny-alpha` (**do not append a `:free` suffix — that returns 404**)
  - OpenCode Zen: `POST https://opencode.ai/zen/v1/chat/completions`, model `space-bunny-free` (`@ai-sdk/openai-compatible`)
  - OpenCode Zen: `POST https://opencode.ai/zen/v1/chat/completions`, model `space-bunny-free` (`@ai-sdk/openai-compatible`)
- **Status**: limited-time free — **re-verified 2026-10-01** (Space Bunny Free is listed: Zen `/v1/models` carries it among 84 models, and it is **callable with no API key at all** — `POST /v1/chat/completions` returns 200, signed "Space Bunny", with `cost:"0"`; OpenRouter still lists `stealth/space-bunny-alpha` at `prompt=0` and `completion=0`. The official wording is "free on OpenCode for a limited time", described as time to "collect feedback and improve the model"; it launched with a "free for one week" announcement (roughly expiring 2026-09-30) and **has no published end date**. ⚠️ `big-pickle` from the same batch has been removed from this section — without a key it consistently returns 403 `FreeTierError` ("OpenCode's free tier can only be used from within OpenCode") and a fake key returns 401, so **it is not reachable via direct external API calls** and fails this repo's rule of thumb: collect channels that can actually be called with an API key through an endpoint)

## Model Index

### Structured decision models (non-generative)

#### TypeSafe AI Jev

> TypeSafe AI's first System One model, released in early access on 2026-09-15; it **does not generate text** — you send a state plus a set of typed questions, and it returns choices, scores and boolean probabilities

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| ~~Vercel AI Gateway~~ **(Jev promo ended 2026-09-25)** | ~~limited-time promotional free~~ → pay-per-token ($0.042/M input, $0 output) | ⚠️ **the promo has expired**: Jev is back at list price and no longer free; the $5/month credit remains but covers only the Free Tier eligible subset and **requires a payment method on file** | Promo over |
| — | **no other free channel** | ⚠️ **full sweep 2026-09-30**: ① the official `api.typesafe.ai/v1/systemone` endpoint exists (no key → 403 `Must supply an API key!`) but **new signups have been paused since 2026-09-22**, and its pricing is the same $0.042/M input; ② OpenRouter only carries `typesafe/jev-router` with `pricing` `-1/-1` (not billed through OpenRouter), so the official price applies; ③ Cloudflare Workers AI's official model page **has no Jev / TypeSafe entry** (secondary sources are wrong); ④ Jev is positioned as an extremely cheap pay-per-token tier with free output — **a paid model, not a free channel** | — |

### DeepSeek family

#### DeepSeek V4.1 Flash

> 552B new-architecture MoE (8B/16B active), native multimodal, 1M context; released 2026-09-10

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official hosting, no card, no daily cap; Cons: 40 RPM shared, queues at peak | Frequent timeouts |
| [Token Harbor](https://tokenharbor.ai) | Within the free monthly allowance (renews on a 4-week rolling cycle) | Pros: small gateway, no card required, **the Free plan explicitly includes V4.1 Flash**; Cons: ⚠️ **region-blocked for Mainland China, Hong Kong and Macao**, requiring an overseas network; allowance undisclosed, renews every 4 weeks, gateway is young | Region-restricted |
| [Onomeo](https://onomeo.com/zh) | check-in daily allowance (8,409 credits/answer, ~23 answers off a full 200k check-in) | Pros: reachable from Mainland China without a proxy, OpenAI-compatible, works off a topped-up check-in allowance, supports image input; Cons: not a free tier, manual daily check-in required, costly per call (1,473 on 9/22 has risen to 8,409), public-beta aggregator can change anytime |  |

> ⚠️ **No official free tier, and third-party free entry points are scarce**: DeepSeek itself is paid only (off-peak $0.15/$0.60 per 1M). ⚠️ **Ollama Cloud is not a free entry point** — V4.1 Flash is in its cloud catalog, but it is a flagship model unlocked with purchased credits, while the free plan covers only the starter subset (verified 2026-09-12). ⚠️ **OrcaRouter does not offer free V4.1 either** — `deepseek/deepseek-v4.1-flash` is billed at $0.15/$0.60 on its price list, and its free pool holds only V4 Flash (`deepseek-v4-flash-free`) plus Hy3 and GLM-5.3-Flash (verified 2026-09-12). ⚠️ **Token Harbor is region-blocked** — `https://tokenharbor.ai/v1` returned `region_blocked`, explicitly refusing Mainland China, Hong Kong and Macao (verified 2026-09-12). ✅ **But NVIDIA NIM now hosts V4.1 Flash** (live `deepseek-ai/deepseek-v4.1-flash` verified 2026-09-27, permanent free at 40 RPM, no card) — **this is currently the only "free tier" entry point for V4.1 Flash**; Token Harbor has a Free plan but is region-blocked for readers in China, and Onomeo is check-in credits rather than a free tier.

#### ~~DeepSeek V4 Pro~~ (official routing retired from 2026-09-14)

> Flagship MoE, 1M context, strongest for coding & agents. ⚠️ From 2026-09-14 12:00 the official API routes all `deepseek-v4-pro` requests to V4.1 Flash at Flash rates, until V4.1 Pro ships

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Intern InkStone Token Plan](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | free monthly ink-dot allowance during the beta, converted to tokens (1 ink dot covers up to 50,000,000 tokens, priced with DeepSeek-V4-Flash) | Pros: official platform by Shanghai AI Laboratory, allowance tops up monthly, no card required, both OpenAI and Anthropic protocols; Cons: ⚠️ the exact monthly ink-dot grant was never published, you must sign in to check your balance, research-oriented platform rather than a general chat gateway, quota not withdrawable, terms can change |  |

#### DeepSeek V4 Flash

> 284B MoE, 1M context, best value for code / reasoning. ⚠️ The official model id `deepseek-v4-flash` now auto-routes to V4.1 Flash; the legacy id still works

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OrcaRouter](https://www.orcarouter.ai) | free pool, rate-limited, zero markup | Pros: 200+ models behind one gateway, 0% token markup, no card; Cons: free allowance unpublished, 429 rate limits, best-effort not production |  |
| [BazaarLink](https://bazaarlink.ai) | free tier `deepseek-v4-flash-0731free:free` ($0 in / $0 out) | Pros: Taiwan-based gateway, no card, includes the 0731 build; Cons: young small gateway, rate-limited, free allowance unpublished |  |
| [OpenCode Zen](https://opencode.ai/zen) | limited-time free (`deepseek-v4-flash-free`) | Pros: OpenCode's official gateway, no card, 1M context; Cons: limited-time free can end anytime, data may be used to improve the model during the free period, lineup flips back and forth (showed billing on 9/11) |  |
| [Hugging Face](https://huggingface.co) | $0.10 free inference credits/month, pay-as-you-go beyond | Pros: huge model catalog, OpenAI-compatible; Cons: only $0.10/month free credit, pay-as-you-go after (hard stop), rate-limited shared endpoint, no SLA | Tiny quota |
| [ModelScope](https://modelscope.cn) | ~200 req/day | Pros: China-native, OpenAI-compatible, huge catalog; Cons: low-quality free tier — only ~200 req/day per model, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |
| [Intern InkStone Token Plan](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | free monthly ink-dot allowance during the beta, converted to tokens (1 ink dot covers up to 50,000,000 tokens, priced with DeepSeek-V4-Flash) | Pros: the only model the platform explicitly names as its conversion baseline, official Shanghai AI Lab platform, monthly top-up, OpenAI + Anthropic protocols; Cons: ⚠️ the exact monthly ink-dot grant was never published, you must sign in to check your balance, "up to" 50,000,000 per dot (faster models burn it quicker), research-oriented platform |  |

### GLM family

#### GLM-5.3 Flash

> Native multimodal, 320B, 1M context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official hosting, no card, 1.3M context & multimodal, no daily cap; Cons: 40 RPM shared, queues at peak | Frequent timeouts |
| [OrcaRouter](https://www.orcarouter.ai) | free pool, rate-limited, zero markup | Pros: 200+ models behind one gateway, 0% token markup, no card; Cons: allowance unpublished, became the free default on 2026-09-07 replacing Qwen3.8-27B, high TTFT (~7.66s) | Rate-limited |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | limited-time free (ZZ.ai) | Pros: official AMD hosting, ~$10/day; Cons: limited-time, high TTFT, rate-limited | High TTFT |
| [Onomeo](https://onomeo.com/zh) | check-in daily allowance (`z-ai/glm-5.3-flash-free`, 3,149 credits/answer, ~63 answers off a full 200k check-in) | Pros: reachable from Mainland China without a proxy, OpenAI-compatible, 1M context; Cons: not a free tier, manual daily check-in required, ~16x costlier per call than the 9/22 figure, public-beta aggregator can change anytime; ⚠️ the flagship `glm-5.3` (non-flash) on the same platform is a premium model subject to the 50k credits/day cap |  |
| [Intern InkStone Token Plan](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | free monthly ink-dot allowance during the beta, converted to tokens (1 ink dot covers up to 50,000,000 tokens, priced with DeepSeek-V4-Flash) | Pros: official Shanghai AI Lab platform, monthly top-up, no card required, 1M context, OpenAI + Anthropic protocols; Cons: ⚠️ the exact monthly ink-dot grant was never published, you must sign in to check your balance, ⚠️ unverified whether GLM-5.3 is in the ink-dot free pool (the platform only names V4-Flash), research-oriented platform |  |

#### GLM 5.2 / 5.1

> Agentic-workflow flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
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

> ⚠️ **MiniMax models have been pulled from NVIDIA NIM**: GLM-4.7 and MiniMax M2.1 were briefly listed in early September 2026 and removed on 2026-09-11; a 2026-09-27 re-check confirms **MiniMax M3 is not listed either** (NIM's catalog has no minimax entries at all).

#### MiniMax M3

> Multimodal MoE, reasoning / tool use

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [OpenCode Zen](https://opencode.ai/zen) | limited-time free (in-client) | Pros: official OpenCode gateway, no card; Cons: limited-time, client-only |  |

#### MiniMax M2.1

> Enhanced multilingual coding, 204K context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| OpenCode Zen | ⚠️ deprecated (2026-03-15) | Pulled from OpenCode Zen; the official API is paid ($0.3/$1.2) |  |

#### Kimi K2.6

> 1T MoE, long-horizon coding, multimodal

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent, 40 RPM | Pros: official, no card, no daily cap; Cons: 40 RPM shared | Frequent timeouts |
| [Intern InkStone Token Plan](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | free monthly ink-dot allowance during the beta, converted to tokens (1 ink dot covers up to 50,000,000 tokens, priced with DeepSeek-V4-Flash) | Pros: official Shanghai AI Lab platform, monthly top-up, no card required, OpenAI + Anthropic protocols; Cons: ⚠️ the exact monthly ink-dot grant was never published, you must sign in to check your balance, ⚠️ unverified whether Kimi K2.6 is in the ink-dot free pool (the platform only names V4-Flash), research-oriented platform |  |

#### Kimi K3

> 2.8T native multimodal agent, 1M context, long-horizon coding / complex reasoning

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
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
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |

### Global models

#### GPT-OSS 120B / 20B

> OpenAI open-weight MoE, coding / reasoning

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Groq](https://console.groq.com) | 1,000 req/day | Pros: LPU ultra-fast; Cons: 30 RPM / 1,000 RPD, 8K TPM |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent (20B only) | Pros: official, no card; Cons: 40 RPM shared, only hosts gpt-oss-20b | Frequent timeouts |

> ⚠️ **GPT-OSS is no longer in the OpenRouter free lineup** (verified 2026-09-11).

#### GPT-6 Astra

> OpenAI flagship model (`gpt-6-astra`)

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Onomeo](https://onomeo.com/zh) | check-in daily allowance (3,948 credits/answer, ⚠️ capped by the premium daily limit: ~12/day on an account that has not bought credits) | Pros: reachable from Mainland China without a proxy, OpenAI-compatible, even flagship models are covered by the allowance; Cons: not a free tier, manual daily check-in required, **13 premium models have a separate 50k credits/day cap** (300k after buying), ~93% measured availability, public-beta aggregator can change anytime |  |

#### Gemini 2.5 Flash / Flash-Lite

> Google's free-tier workhorse, multimodal

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Google AI Studio](https://aistudio.google.com) | daily reset (2.5 Pro 5 RPM/50 RPD, Flash 15 RPM/1,500 RPD, Flash-Lite 30 RPM/1,500 RPD) | Pros: official, free, no card, multimodal, 1M context; Cons: 2.5 Pro free tier is only 5 RPM/50 RPD (trial-only), needs Google account, free-tier data may be used for product improvement, real throughput far below nominal at peak |  |

#### Nemotron 3 Ultra / Super / Lightning

> NVIDIA agentic flagship, 1M context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` (Ultra / Super / 3.5 Lightning) | Pros: aggregated routing; Cons: 50 free req/day, lineup rotates anytime |  |
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
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent (31B only) | Pros: official, no card; Cons: 40 RPM shared, NIM hosts only `gemma-4-31b-it`, no 26B-A4B | Frequent timeouts |

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

#### DeepSeek R1 / V3

> Deep-reasoning model / general flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Cloudflare](https://developers.cloudflare.com/workers-ai) | R1 distilled, 10K Neurons/day | Pros: low-latency edge inference; Cons: distilled not original, small daily quota |  |
| [OpenRouter](https://openrouter.ai) | `:free` rotates, may be absent | Pros: one API for many models; Cons: 50 free req/day (1,000 after $10), lineup rotates anytime |  |
| [ModelScope](https://modelscope.cn) | R1 ~200 req/day | Pros: China-native, huge catalog; Cons: low-quality free tier — R1 ~200/day, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |

> ⚠️ **DeepSeek R1 / V3 are no longer on NVIDIA NIM**: removed from the NIM model list on 2026-09-11; re-checked 2026-09-27, the only DeepSeek models left on NIM are `deepseek-ai/deepseek-v4.1-flash` and `deepseek-coder-6.7b-instruct` — V4 Flash 0731 and V4 Pro 0813 have both been delisted.

#### DeepSeek R2

> Next-gen general model

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Volcano Ark](https://console.volcengine.com/ark) | within collaboration-plan free quota (2M tokens/day) | Pros: large 2M tokens/day free quota; Cons: needs Volcengine account + real-name, check console |  |


## Free Channels

### Official free tiers (global)

#### NVIDIA NIM

- **Official site**: https://build.nvidia.com
- **Free tier**: permanent (40 RPM shared site-wide, no daily cap)
- **What the site says**: "100+ models free to call" — NVIDIA-hosted inference endpoints, sign up and go, no credit card
- **Free models**: **`deepseek-ai/deepseek-v4.1-flash` (newly listed 2026-09-27)**, **`z-ai/glm-5.3` / `z-ai/glm-5.3-flash`**, `moonshotai/kimi-k2.6`, `moonshotai/kimi-k3`, `google/gemma-4-31b-it`, `nvidia/nemotron-3-ultra-550b` / `nemotron-3-super-120b` / `nemotron-3.5-lightning-30b`, `openai/gpt-oss-20b`, `mistralai/mistral-large` / `mistral-large-2-instruct`, `poolside/laguna-xs-2.1` and more (check the live `/v1/models`; ⚠️ **V4 Flash 0731, V4 Pro 0813 and MiniMax M3 have all been delisted**)
- **Endpoint**: `https://integrate.api.nvidia.com/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-09-27 (in practice `/v1/models` returns **82 models** — the same count as 9/12, but with a **large lineup swap**: ✅ newly added `deepseek-ai/deepseek-v4.1-flash` and `z-ai/glm-5.3`; ❌ **removed `deepseek-v4-flash-0731`, `deepseek-v4-pro-0813` and every MiniMax entry**. NIM now carries only V4.1 Flash and `deepseek-coder-6.7b-instruct` from DeepSeek, so **V4 Flash / V4 Pro have no free tier left on NIM**; MiniMax / Qwen / StepFun / Ling still absent, GLM 5.2 / 5.1 / 4.7 have not returned. ⚠️ An unchanged count does not mean an unchanged lineup — always diff the model IDs)

#### Google AI Studio

- **Official site**: https://aistudio.google.com
- **Free tier**: permanent (daily reset)
- **What the site says**: Google's official AI dev platform; the free tier exposes Gemini models over the API
- **Free models**: Gemini 2.5 Pro (free tier **5 RPM / 50 RPD / 1M TPM**, trial-only), 2.5 Flash (15 RPM / 1,500 RPD), Flash-Lite (30 RPM / 1,500 RPD), Gemini 3.x Flash (preview, stricter limits); ⚠️ **2.5 Pro is still in the free tier** (contrary to the old "removed 2026-04-01" note), just at a very low free allowance; ⚠️ the free quota was sharply cut in Dec 2025 and real-world throughput at peak is far below nominal (community reports Flash ~20 req/day at peak)
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
- **Free tier**: **$0.10** free inference credits per month (Inference Providers routed billing, zero markup at upstream list price); pay-as-you-go beyond — free users hit a hard stop at the credit limit and must buy credits to continue
- **What the site says**: the largest open model hub, offering Inference Providers routed inference; every user gets $0.10/month free credits for trials, billed pay-as-you-go after
- **Free models**: 100k+ community & official models (DeepSeek V4 Flash etc. can be called via routing, but consume the free credit and stop when exhausted)
- **Endpoint**: `https://router.huggingface.co/hf-inference` (`InferenceClient` / REST, auth with HF User Access Token)
- **Status**: Active — verified 2026-09-14 (⚠️ **free quota has shrunk sharply**: since 2026 free users get only $0.10/month inference credit, no longer "permanently free shared endpoints"; PRO at $9/mo is only $2/month. The free tier is good for tiny experiments only — buy credits for production)

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
- **Available models (require purchased credits)**: deepseek-v4.1-flash ($0.15/$0.60 off-peak), deepseek-v4-pro, deepseek-v4-flash ($0.22/$0.66 off-peak), glm-5.1 / 5.2 / 5.3 / 5.3-flash, kimi-k2.6 / k2.7-code / k3, minimax-m2.7 / m3, qwen3.5:397b, gpt-oss:20b / 120b, gemma4, nemotron-3-nano / super / ultra, mistral-large-3 (**20 models in the cloud catalog, and all 20 carry a price on the pricing page — none at $0**)
- **Endpoint**: `https://ollama.com/api/chat` (Ollama API; API key: https://ollama.com/settings/keys — **calling without a key returns `{"error":"Unauthorized"}`**)
- **Status**: Active (**listed in no model free index**) — verified 2026-09-12 (⚠️ **important correction**: this entry previously claimed V4.1 Flash / V4 Flash and others were free entry points, which was a misreading — the 20 models returned by `/api/tags` are merely the **cloud catalog**, not a free list. Calling `deepseek-v4.1-flash` without an API key returns Unauthorized; all 20 models on the pricing page are **metered and priced, none at $0** (V4 Flash $0.22/$0.66); and the FAQ states the Free plan only provides "a starter amount of usage for a smaller set of starter models", with "Buying usage credits unlocks all models" — while **the starter list has never been published, and no endpoint or catalog tag exposes it**. So **no specific model can be confirmed as inside the free tier**, and this repo records no model as "free on Ollama Cloud". The Free plan's real value is a small undisclosed allowance on undisclosed starter-size models; 1 concurrent request, allowance resets monthly from your signup date and does not roll over)

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
- **Endpoint**: `https://spark-api-open.xf-yun.com/v1` (OpenAI-compatible; APIKey/APISecret auth, keys issued from the [console](https://xinghuo.xfyun.cn/sparkapi))
- **Status**: Active — verified 2026-09-05 (real-name verification required)

#### ModelScope (Alibaba)

- **Official site**: https://modelscope.cn
- **Free tier**: permanent (free inference for all registered users, ~2,000 req/day total, 100~500 req/day per model)
- **What the site says**: Alibaba DAMO's open model community — "free inference for all registered users"; DeepSeek-R1 ~200 req/day
- **Free models**: DeepSeek V4 Flash / R1, Qwen3 Coder 480B, Qwen3 235B, Qwen2.5 72B, GLM-4.5, MiniMax-M1 and ~3,000 open models
- **Endpoint**: `https://api-inference.modelscope.cn/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-09-02 (Alibaba Cloud account + real-name verification required)
- **⚠️ Low-quality free tier**: only ~100–500 req/day per model, shares the 2,000 req/day total pool (busy days can be crowded out); personal / non-commercial use only; shared GPUs may queue, no SLA

#### Intern InkStone Token Plan (墨点计划)

- **Official site**: https://discovery.intern-ai.org.cn · Token Plan: https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0
- **Free tier**: a monthly "ink dot" (墨点) allowance is granted automatically during the beta, converted to tokens (**1 ink dot covers up to 50,000,000 tokens, priced with DeepSeek-V4-Flash** — the page renders `5000,0000`, a typo; the correct figure is 50 million)
- **Official wording**: launched by Shanghai AI Laboratory at the 2026 Pujiang Innovation Forum; the announcement says "during the beta, every user receives free tokens each month". ⚠️ **The exact monthly grant was never published** — you must sign in to see your actual balance (everything renders as `--` when logged out)
- **Free models**: ⚠️ the platform only names DeepSeek-V4-Flash as its conversion baseline; the full catalog requires signing in
- **Endpoint**: `https://discovery-api.intern-ai.org.cn/v1` (OpenAI-compatible); it also speaks the Anthropic protocol at `https://discovery-api.intern-ai.org.cn` (no `/v1`) — **rare among free channels**
- **Status**: Active (free during the beta, terms may change) — verified 2026-09-30 (`/v1/models` without a key returns 401 `invalid_api_key`, so the endpoint exists; phone-number registration, no card required)
- **⚠️ Not withdrawable**: ink dots are platform-internal only; "up to 50,000,000 per dot" is a ceiling, not a fixed value, and pricier models burn them faster
- **Rate limits**: RPM + TPM + ink-dot balance, triple-capped, and **all API keys share the account quota** (not per-key); up to 10 keys per account, 6-month default validity
- **⚠️ Different scope**: a research platform (life sciences, materials, semiconductors, fusion, meteorology), not a general-purpose chat API gateway; quota requests go to `tokenplan@pjlab.org.cn`

### Aggregators & gateways

#### Vercel AI Gateway

- **Site**: [https://vercel.com/ai-gateway](https://vercel.com/ai-gateway) ([pricing](https://vercel.com/docs/ai-gateway/pricing) · [getting started](https://vercel.com/docs/ai-gateway/getting-started))
- **Free tier**: The free tier includes **$5/month** (the clock starts on your first AI Gateway request), limited to **Free Tier eligible models**, with lower per-model rate limits than the paid tier; ⚠️ **Jev's limited-time promo ended on 2026-09-25 and is now pay-per-token**
- **What the site says**: Vercel's managed gateway; the docs state "no markup and no platform fee on tokens" — provider list price, zero markup. On the free tier: "**To use free AI Gateway Credits, add a valid payment method to your team.**" (a payment method is required to enable free credits)
- **Free models**: ~~`typesafe-ai/jev` (limited-time promo now over)~~ plus the Free Tier eligible subset (⚠️ the full allowlist is **not published** — browse your dashboard or the [models page with `?freeTier=true`](https://vercel.com/ai-gateway/models?freeTier=true); as of 2026-09-27 only `inclusionai/ling-3.0-flash-sante-free` and `poolside/laguna-s-2.1-free` carry `*:free` pricing in the catalog)
- **Endpoint**: `https://ai-gateway.vercel.sh/v1` (OpenAI-compatible); ⚠️ **Jev must go through the Evaluation endpoint `POST /v1/evaluate`** with a `{model, state, questions}` body — it **cannot be called via `chat/completions`** (verified 2026-09-20: `/v1/evaluate` with the Jev model returns `Authentication failed`, i.e. the endpoint is correct but unauthenticated, whereas `/v1/evaluations` and `/v1/decisions` both return 404)
- **Status**: Active ($5/month free tier) — verified 2026-09-27 (⚠️ boundaries to remember: ① **the Jev promo ended on schedule on 2026-09-25** (multi-source: Vercel Weekly 2026-09-21 stated "Jev … free to use until September 25"; it is back to TypeSafe list price — $0.042/M input, $0 output), so **Jev has been dropped from the free index**; ② **free credits require a payment method on file**, but nothing is charged unless you top up (`Commitment: None`); ③ **purchasing credits moves the account to the paid tier and permanently voids the $5/month free credit** — `Once you purchase credits, your account transitions to the paid tier and the monthly free credit no longer applies.` Exhaust the free credit before considering a top-up; ④ free-tier limits are lower than paid, and exceeding them returns 429)

#### OpenRouter

- **Official site**: https://openrouter.ai
- **Free tier**: permanent (`:free` models, 50 req/day and 20 req/min; 1000/day after a $10 lifetime top-up)
- **What the site says**: multi-model router exposing a `:free` lineup; `openrouter/free` auto-routes between them (⚠️ the widely-quoted "200 req/day" is outdated — the official limits page states 50/1000)
- **Free models**: `thinkingmachines/inkling(-small)` (1M-context multimodal), `nvidia/nemotron-3-ultra-550b`, `nemotron-3-super-120b`, `nemotron-3.5-lightning`, `gemma-4-26b-a4b`, `gemma-4-31b`, `inclusionai/ling-3.0-flash-sante/-fin/-vl`, `nex-agi/nex-n2.5-pro/-mini`, `cohere/north-mini-code`, `poolside/laguna-s-2.1/-xs-2.1`, `dots-studio/dots-3-note-preview` (512K), `liquid/lfm-2.5-2.6b` — **19 in total** (⚠️ **DeepSeek / GLM / Qwen / MiniMax / Kimi / Llama are all absent**; check `openrouter.ai/models?max_price=0` first)
- **Endpoint**: `https://openrouter.ai/api/v1` (most model names need the `:free` suffix; ⚠️ the exception is `stealth/space-bunny-alpha`, which carries no suffix and is already priced at 0 — appending one returns 404. See [Stealth Models](#stealth-models))
- **Status**: Active — verified 2026-09-27 (free lineup re-verified live: **17** `:free` models, down from 21 on 9/20 — **four left: `z-ai/glm-5.2`, Nex AGI N2.5 mini/pro and `ling-3.0-flash-vl`; nothing new this week**; still listed are Qwen3.8-27B, Gemma 4 ×2, five Nemotron variants, Poolside Laguna ×2, Thinking Machines Inkling ×2, Ling 3.0 Flash Fin/Sante, Liquid LFM 2.5 and Cohere North Mini Code. 50 req/day, 1,000 after $10. ⚠️ four models can leave in a week — "lands in the free pool on launch day" is a cold-start signal, not a long-term commitment, so always keep a fallback)

#### AIHubMix

- **Official site**: https://aihubmix.com (free model list: https://aihubmix.com/models/free)
- **Free tier**: free models (10 trial calls on signup, no expiry; a one-time $1+ top-up permanently switches to daily quotas: 100 req/day and 1M tokens/day, reset daily)
- **What the site says**: "56 free models — no credit card required"; the platform subsidizes inference cost — every free model bills $0 in & out
- **Free models**: glm-4.7-flash-free, hy3-free, minimax-m3-free, k2.6-code-preview-free, gpt-oss-20b-free, nemotron-3-ultra/super-free, gemma-4-31b-it-free, xiaomi-mimo-v2.5(-pro)-free, coding-glm-5.3-free, gpt-5.5-free, gemini-3.8-flash-free and 50+ more
- **Endpoint**: `https://aihubmix.com/v1` (Chat Completions / Messages / Responses compatible)
- **Status**: Active — verified 2026-09-05 ($1 top-up required for daily quotas; shared free pool)

#### OpenCode Zen

- **Official site**: [https://opencode.ai/zen](https://opencode.ai/zen) ([pricing](https://opencode.ai/docs/zen/))
- **Free tier**: limited-time free models (DeepSeek V4 Flash, MiMo-V2.5, Ling 3.0 Flash Fin, Nemotron 3 Ultra, Nemotron 3.5 Lightning, Muse Spark 1.2 / 1.3 Contributor, Jev 1.13 — $0 across input, output and cache read/write)
- **What the site says**: OpenCode's official model gateway; the pricing page explicitly marks the free models as Free and notes they are "available for a limited time while the team collects feedback"; **the platform itself is not free** — the full DeepSeek / GLM / Kimi / Qwen editions are pay-per-token
- **Free models**: DeepSeek V4 Flash Free (1M context), MiMo-V2.5 Free (multimodal), Ling 3.0 Flash Fin Free, Nemotron 3 Ultra Free, Nemotron 3.5 Lightning Free, Muse Spark 1.2 / 1.3 Contributor Free, Jev 1.13 Free (decision model, via the Evaluation API) — 7 total (verified against `/v1/models` on 2026-10-01)
- **Endpoint**: `https://opencode.ai/zen/v1` (OpenAI-compatible; some models use `/messages` Anthropic or `/responses`)
- **Status**: Active (limited-time) — verified 2026-10-01 (✅ the catalog carries **84 models**, of which 11 carry the `-free` suffix, including `space-bunny-free` (a stealth model — see [Stealth Models](#stealth-models)); ⚠️ `big-pickle` is in the catalog but **not reachable via direct external API calls** (no key returns 403 `FreeTierError`, a fake key returns 401), so it is left out of the free list; ⚠️ `deepseek-v4-flash-free` showed pay-per-token pricing in a 2026-09-11 check ($0.14/$0.28) and returned to the free list on 9/20 — the lineup flips back and forth, so check the current catalog before calling)

#### OrcaRouter

- **Official site**: [https://www.orcarouter.ai](https://www.orcarouter.ai) ([docs](https://docs.orcarouter.ai))
- **Free tier**: free pool rate-limited per workspace (allowance unpublished); **0% token markup** on the paid side (pass-through at upstream list price)
- **What the site says**: an OpenAI-compatible LLM routing gateway with 200+ models behind one endpoint; free models are catalog models exposed under separate free IDs with identical weights/capabilities, running in an isolated rate-limited pool — **a saturated free model will not silently fall back to its paid counterpart**
- **Free models**: `orcarouter/free` (difficulty-aware routing across the free pool), `z-ai/glm-5.3-flash-free`, `deepseek/deepseek-v4-flash-free`, `tencent/hy3-free` (4 free of 202 models in the live `/v1/models` on 2026-09-27)
- **Endpoint**: `https://api.orcarouter.ai/v1` (OpenAI-compatible, no card required)
- **Status**: Active (rate-limited) — verified 2026-09-20 (on 2026-09-07 the free default switched from Qwen3.8-27B to GLM-5.3 Flash: quality score 4→8, context 262K→1M, but TTFT 1.96s→7.66s and throughput 196→74 tok/s; ⚠️ accounts that never purchased credit get a smaller daily allowance, `429 + Retry-After` means the window is full while a 429 without the header means the prompt is too long; the vendor explicitly calls it best-effort, not production capacity)

#### Onomeo

- **Official site**: https://onomeo.com/zh ([models page](https://onomeo.com/zh/models))
- **Free tier**: check-in-based daily allowance (not a free-tier model) — daily check-in grants up to 200,000 credits (50,000 on day one, rising daily until the 7-day streak cap), referrals grant 50,000 to both sides. The credits are funded by paid market-research surveys (vendor FAQ: users answer surveys, the research partner pays, and that money covers the calls the credits pay for). **Credits never expire**; balance caps at 10,000,000
- **Paid tier**: ⚠️ **13 "premium" models carry their own daily spend cap** (measured from `premium.models`): `claude-sonnet-5`, `claude-haiku-4.5`, `gpt-6-astra`, `gpt-5.6-terra`, `gemini-3.1-pro-preview`, `kimi-k3`, `glm-5.3`, `mistral-large-3`, `nemotron-3-ultra-550b-a55b`, `claude-opus-5.5`, `gpt-6-sol`, `gpt-6-luna`, `grok-4.7`. **Accounts that have not bought credits may spend at most 50,000 credits/day on these models; buying raises it to 300,000/day** (FAQ #13, verbatim: "未购买额度的账号每日最多在 Claude、GPT 等大模型上消耗 50,000 额度，购买后提高到每日 300,000"). ⚠️ So **check-in credits alone cannot drive the flagships** — at 3,948 per call, `gpt-6-astra` works out to about **12 calls/day** on a free account (50,000 ÷ 3,948), and `claude-opus-5.5` / `gpt-6-sol` about 7 each; over the cap returns 402 `premium_daily_cap` (nothing is deducted)
- **What the site says**: a Chinese aggregator gateway, one key for **47 models** behind an OpenAI-compatible endpoint (homepage text, verified 2026-09-27 — the 54 previously recorded is outdated); ⚠️ the vendor states that `usage.total_tokens` is exactly what gets deducted and that **each call differs**, so every cost figure below is a "from about X per answer" floor that floats with token count
- **Free models**: the check-in allowance covers all 47 in the catalog; figures below are the **minimum per-answer cost** measured 2026-09-27 from the data embedded in `/zh/models` (answers off a full 200k check-in = 200,000 ÷ cost): `gemini-3.1-flash-lite` (9 ≈ 22,222 — best value), `gemini-3-flash-preview` (21), `poolside/laguna-s-2.1:free` (21), `dots-3-note-preview:free` (22), `stepfun/step-3.7-flash:free` (43), `glm-5.3` (517 ≈ 386), `gemini-3.1-pro-preview` (867), `stealth/space-bunny-alpha` (1,932, an anonymous model — see [Stealth Models](#stealth-models)), `deepseek-v4-flash` (2,385 ≈ 83), `tencent/hy3-free` (2,712), `gpt-6-luna` (2,917), `gpt-6-astra` (3,948 ≈ 50), `z-ai/glm-5.3-flash-free` (3,149 ≈ 63), `deepseek-v4.1-flash` (8,409 ≈ 23), `Qwen/Qwen3.8-Flash-Next` (41,457 ≈ 4 — priciest)
- **Endpoint**: `https://onomeo.com/v1` (OpenAI-compatible; re-verified 2026-09-27 — `/v1/models` without a key returns 401 `bad_key`, i.e. the endpoint exists and only lacks auth; reachable from Mainland China without a proxy)
- **Status**: Active (check-in-based) — verified 2026-09-27 (⚠️ **the free mechanism is "earn allowance by checking in", not a free tier**: credits expire daily and require a manual check-in every day; the aggregator runs its own allowance pool (many `:free` entries share names with OpenRouter's free pool, so they look relayed), and may change rules or shut down at any time. ✅ All 47 models carry a `training` flag and **most are `trains`** (the whole Gemini line, the gpt-6 line, glm-5.3, …), with a few `no` / `optout` / `unknown` — **treat your prompts as possibly used for training**. Measured availability (`health.ok/failed`) varies a lot: `deepseek-v4.1-flash`, `deepseek-v4-flash`, `z-ai/glm-5.3-flash-free` and `glm-5.3` are all at 100%, but `gemini-3.7-flash` is only 36%, `claude-opus-5.5` 57%, and both `cohere/north-mini-code:free` and `nemotron-3.5-lightning` 56% — no SLA. ⚠️ Three more rate limits stack on top: the premium models' daily credit cap (above), the site-wide premium budget released in four batches a day (UTC 00/06/12/18, each reserving 30% for accounts that bought credits — everyone else gets 503 `premium_budget_exhausted` with `reserved:true` once that slice is gone), and a rolling 5-hour call cap per account / per IP (`perAccountWindowMax` 60, `perIpWindowMax` 120))

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
- **Free tier**: ~~limited-time (0 Credits)~~ **ENDED** — since 2026-09-16 17:00 (Singapore time) every model moved to at least a 10% discount; the platform has zero 0-Credit models left
- **What the site says**: AI-agent infrastructure platform; API is OpenAI- and Anthropic-compatible. Free-tier timeline (per the official promo page): 8/17 DeepSeek V4 Flash free → 9/3 tiered discount (50% peak / 25% off-peak); 8/21 Hy3, 8/24 MiMo-V2.5, 8/29 GLM-5.3-Flash / Qwen3.8-Flash free → 9/12 GLM-5.3-Flash and V4.1-Flash moved to 10% discount → **9/16 17:00 Qwen3.8-Flash / Hy3 / MiMo-V2.5 also moved to 10% discount — the free tier is gone**
- **Free models**: ~~GLM-5.3-Flash (Ox Alpha), Qwen3.8 Flash, Hy3, MiMo-V2.5~~ (all ended; now at least 10% off)
- **Endpoint**: `https://api.b.ai/v1` (use `api.bankofai.io` if the main domain is unreachable from China; OpenAI-compatible)
- **Status**: **Inactive (free tier ended 2026-09-16)** — verified 2026-09-20 (⚠️ no longer listed as a free channel; re-evaluate if a free tier returns)

#### Experiential Labs

- **Official site**: [https://platform.experientiallabs.ai](https://platform.experientiallabs.ai) (YC-backed; calls itself "the open-source OpenRouter")
- **Free tier**: limited-time (models marked $0 in/out still exist, but the Free plan is now a **capped monthly credit allowance of ~500 credits/month**, 1 credit = 1 cent; hard stop when exhausted, no auto-upgrade to paid; new orgs also get welcome credits)
- **What the site says**: the business model is "free traffic in exchange for training data" — the platform documents a flow for uploading traces as telemetry, so the free tier is a customer-acquisition investment and **the allowance can shrink at any time**
- **Free models**: `Qwen3.8 27B free` (1M context, 192 tok/s, 80.2% uptime), `DeepSeek V4 Flash free` (1.05M, 141 tok/s, 100% uptime), `GPT-5.6 Luna free` (1.05M, 154 tok/s, 97.5%), `Claude Fable 5.1 free` (1M, 86.9 tok/s, **72.5% uptime**), `GPT-6 Astra free` (1.05M, 88 tok/s, 89%) — the latter two list at $10/$50 (models marked $0 still fall under the ~500 credits/month cap)
- **Endpoint**: `https://api.experientiallabs.ai/v1` (OpenAI-compatible, register for a key)
- **Status**: Active (limited-time) — verified 2026-09-14 (⚠️ **low uptime on the free tier**: Claude Fable 5.1 only 72.5%, TTFT ~4.5s; **free allowance tightened to ~500 credits/month**, and once depleted it returns an error that explicitly says retrying will not help**; for tasting only, do not put it in a production path)

### Small gateways (use with care)

> Barely battle-tested newcomers. Free quotas can disappear or turn paid anytime — **prototypes only, never production**.

#### Token Harbor

- **Official site**: https://tokenharbor.ai ([pricing](https://tokenharbor.ai/pricing))
- **Free tier**: Free plan at $0/month with a monthly free allowance (renews on a **4-week rolling** cycle; unused room does not carry forward); Agent Pass at $1.99/month ($0.99 first month)
- **What the site says**: small gateway; the pricing page lists **DeepSeek V4 Flash, DeepSeek V4.1 Flash and MiMo V2.5** on the Free plan and notes "Promotional models added over time" (the lineup rotates); note that free requests may be saved by the platform
- **Free models**: DeepSeek V4 Flash, DeepSeek V4.1 Flash, MiMo V2.5
- **Endpoint**: `https://tokenharbor.ai/v1` (OpenAI-compatible; generate an API key after signing up)
- **Status**: Active (small gateway, **⚠️ unavailable from Mainland China / Hong Kong / Macao**) — verified 2026-09-12 (⚠️ the endpoint returns `{"type":"region_blocked"}` in practice; the message states it "Cannot serve requests from … **Mainland China, Hong Kong and Macau**", so **readers in Mainland China need an overseas network path** — and the operator asks users to turn off VPNs and retry, since it only sees the country your connection exits from; ⚠️ the **exact allowance is unpublished**; the free allowance and any paid Pass pool into **one shared pool**, and subscribing does not replace the free allowance)

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
- **Free tier**: free model tier (`auto:free` smart routing across the free pool plus `qwen/qwen3.7-flash:free` and `deepseek/deepseek-v4-flash-0731free:free`, $0 in / $0 out, rate-limited, no card required)
- **What the site says**: a Taiwan-based LLM gateway; the site lists "1 free model" and notes "free allowance, auto-switching to paid billing beyond it"; `auto:free` routes to whichever free model currently fits best
- **Free models**: `auto:free` (free-pool smart routing), `qwen/qwen3.7-flash:free` (vision-language reasoning), `deepseek/deepseek-v4-flash-0731free:free` (new as of 2026-09-20)
- **Endpoint**: `https://api.bazaarlink.ai/v1` (OpenAI-compatible)
- **Status**: Active (small gateway) — verified 2026-09-27 (✅ live `/v1/models` returns 128 models, with three `*:free` models priced at 0 (auto / qwen3.7-flash / deepseek-v4-flash-0731) — the free tier holds, ⚠️ though the catalog shrank from 175 to 128 models as paid ones were delisted; ⚠️ since 2026-09-05 the self-serve agent registration endpoint (`/api/agents/register`) returns 410 to curb free-tier abuse — register normally and create a key in the dashboard)

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
- **Free lineups churn more than you think.** OpenRouter's `:free` lineup measured **19 → 21 → 17** models on 2026-09-11 / 09-20 / 09-27 — `z-ai/glm-5.2` lasted only 11 days in the pool. NVIDIA NIM kept a constant count of 82 across both checks while swapping a batch of models (out: `deepseek-v4-flash-0731` and `deepseek-v4-pro-0813`; in: `deepseek-v4.1-flash` and `glm-5.3`) — a model listed here may already be gone when you read it, so run a `curl` check first.
- **"Limited-time free" can end without warning.** Promo APIs (e.g. B.AI's former limited-time tier) publish no end date.
- **Some "free" tiers require a credit card**, a phone number, or real-name verification. Example: Vercel AI Gateway's $5/month free credit explicitly requires **a valid payment method on file** before it can be used (`To use free AI Gateway Credits, add a valid payment method to your team.`, verified 2026-09-20) — having a card on file does not mean being charged, but the barrier is real.
- **Not every "free model" generates text.** Structured decision models like Jev (state plus typed questions in, choices/scores/probabilities out) are served over Evaluation or Decisions APIs and **cannot be used as chat models**; OpenAI-compatible chat/completions calling conventions usually do not apply.
- **Your data may be used for training.** Google (free tier), Mistral (Experiment), Groq, and most OpenRouter `:free` upstreams train on free traffic; some let you opt out.
- **Small gateways are the least stable.** Newcomers like Token Harbor / BazaarLink are barely battle-tested — fine for prototypes, never for production.
- **"Having credits" is not "being able to call freely."** Check-in platforms often cap daily spend on flagship models separately — Onomeo has 13 premium models limited to 50,000 credits/day for accounts that have not bought credits (300,000 after buying), so even a full 200k check-in gets you only about 12 `gpt-6-astra` calls a day, and going over returns 402 with nothing deducted. **Work out the real ceiling from two numbers: per-call cost × daily cap, whichever is smaller.**
- **"Check-in for credits" is not a "free-tier model".** Aggregator platforms like Onomeo trade check-ins/surveys for a daily allowance — the whole catalog is callable but consumption varies wildly (measured on one platform: `gemini-3.1-flash-lite` costs 9 credits per answer, `deepseek-v4.1-flash` 8,409, `Qwen3.8-Flash-Next` 41,457 — a **4,000x spread**), credits expire daily and must be claimed manually, and public-beta platforms can change the rules at any time. ⚠️ **Per-call cost can spike as upstream pricing moves** — Onomeo's `deepseek-v4.1-flash` went from 1,473 to 8,409 in five days, so any "how many calls per day" claim must carry the date it was verified.
- **Some overseas gateways apply regional blocks.** Token Harbor returned `region_blocked`, explicitly refusing Mainland China, Hong Kong and Macao (2026-09-12). Even with a free allowance, such endpoints require an overseas network path from Mainland China — and the operator typically asks you to turn VPNs off, since it only sees the country your connection exits from.
- **"Free signup credits" ≠ free.** DeepSeek's official signup grant is confirmed gone (balance 0 as of 2026-08-31); the official channel is now "cheap", not "free".

## License

[MIT](LICENSE) — fork it, remix it, ship it; just keep the copyright notice.
