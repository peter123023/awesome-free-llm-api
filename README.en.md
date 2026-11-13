# Awesome Free LLM API

**English** | [Chinese](README.md)

> Channel-first: every channel below lists its official site, free tier, and what the site itself says about free access. Looking for the free channels of a specific model? See the [Model Index](#model-index) for key models.
> Last full live re-check: **2026-11-12** (pulled `/v1/models` and pricing for each channel, plus POST probes); **2026-11-14** added cheapllm.shop after a single-channel measurement. Free lineups rotate fast: older dates are kept per entry, "2026-11-12" marks that full re-check and "2026-11-14" marks the new entry.

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
  - [Client-only free (no public API)](#client-only-free-no-public-api)
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

The **one exception** is the [Client-only free](#client-only-free-no-public-api) section: products like Freebuff and AtomCode that keep their allowance inside their own client and expose no public endpoint. They are listed for reference only — **not collected channels, not in the model index, and not an endorsement that their terms allow external calls** (Freebuff's terms forbid them).

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
| **Glyph Cluster** | [BazaarLink](https://bazaarlink.ai) · [Vercel AI Gateway](https://vercel.com/ai-gateway) · [Kilo Gateway](https://kilo.ai) | free-tier $0 (`stealth/glyph-cluster`; on BazaarLink the free route is `stealth/glyph-cluster:free`) | 256K / unpublished | unpublished (BazaarLink catalog: `owned_by: stealth`, `zdr_available: false`; Kilo flags `mayTrainOnYourPrompts: true`) | ⚠️ Listed 2026-10-07; verified 2026-11-12: present and $0 in all three catalogs, but Vercel / BazaarLink need a key — **only Kilo returned 200 on a keyless POST**; no vendor name, no public benchmark; BazaarLink applies the shared free allowance (10 RPM / 60 weighted units per day without credit) |

> ℹ️ **Stealth codenames do get revealed**: Reflection's **Beam** (501B MoE) circulated as `cat-jam` (OpenCode) / `MissingNo` (Nous Portal) before its weights and identity went public on 2026-10-16, after which it became a named model (see [Global models](#global-models)). Stealth models are usually just **a temporary window before the reveal**; the reverse happens too — a model can disappear before it is ever revealed. The OpenCode Zen stealth pair (`space-bunny-free` and `big-pickle`) has been dropped from this table; see the endpoint notes below.

- **Endpoints** (for Glyph Cluster, still listed above; all three verified reachable on 2026-11-12):
  - BazaarLink: `POST https://api.bazaarlink.ai/v1/chat/completions`, model `stealth/glyph-cluster:free` (keyless probe returns 401, auth missing)
  - Vercel AI Gateway: `POST https://ai-gateway.vercel.sh/v1/chat/completions`, model `stealth/glyph-cluster` (keyless probe returns 401, auth missing)
  - Kilo Gateway: `POST https://api.kilo.ai/api/gateway/v1/chat/completions`, model `stealth/glyph-cluster` — **no signup, no key, verified 200**, the only directly callable route in this section
- **Stealth models removed from the table (kept for reference)**: OpenCode Zen's `space-bunny-free` (`POST https://opencode.ai/zen/v1/chat/completions`) and `big-pickle` — ⚠️ verified 2026-10-12: both keyless requests and requests with a valid Zen API key return 403 `FreeTierError` ("can only be used from within OpenCode"; the key was proven valid — the same key returns 402 insufficient funds on paid models), so the free tier is callable only from inside the OpenCode client; ⚠️ re-checked 2026-10-24: `space-bunny-free` has been delisted and `big-pickle`, while still in Zen's catalog, returns 403 all the same — hence both were dropped from this table. Separately, OpenRouter's `stealth/space-bunny-alpha` channel was delisted on 2026-10-06; the former endpoint `POST https://openrouter.ai/api/v1/chat/completions` no longer works

## Model Index

### DeepSeek family

#### DeepSeek V4.1 Flash

> 552B new-architecture MoE (8B/16B active), native multimodal, 1M context; released 2026-09-10

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | permanent (no token cap), 40 RPM | Pros: official hosting, no card, no credits or daily cap, 1M context; Cons: SMS phone verification required, 40 RPM shared, queues at peak | Frequent timeouts |
| [Token Harbor](https://tokenharbor.ai) | Within the free monthly allowance (renews on a 4-week rolling cycle) | Pros: small gateway, no card required, **the Free plan explicitly includes V4.1 Flash**; Cons: ⚠️ **region-blocked for Mainland China, Hong Kong and Macao**, requiring an overseas network; allowance undisclosed, renews every 4 weeks, gateway is young | Region-restricted |
| ~~[Onomeo](https://onomeo.com/zh)~~ | ⚠️ mechanism unverified (2026-11-12) | ⚠️ The site has been redesigned: all check-in/survey copy is gone (embedded `survey: false`) and premium is flagged `buyersOnly: true`, so **no free entry path can currently be confirmed**. The old "8,409 credits/answer, ~23 answers off a 200k check-in" and the 9/22 figure of 1,473 are void — do not use them to estimate call counts |  |
| [ModelScope](https://modelscope.cn) | within shared quota (2,000/day site-wide) | Pros: China-native, direct access without a proxy, OpenAI-compatible, the catalog carries `deepseek-ai/DeepSeek-V4.1-Flash` (verified in the catalog on 2026-10-12); Cons: low-quality free tier — shares the 2,000/day pool, ~500/day per model, Alibaba real-name, personal/non-commercial only | Low quality |
| [BeatAPI](https://beatapi.io) | limited-time free (`deepseek-v4.1-flash-free`, $0 in / $0 out) | Pros: OpenAI-compatible, no card and no top-up, **works on a zero balance**, 2,000 successful requests/day, reachable directly from Mainland China; Cons: ⚠️ **only 1 successful request per minute before the first top-up** (10/min after any top-up), free access is limited-time with a lineup that changes, discounted reseller launched in Oct 2026, end-to-end calls unverified | Unverified |
| [Zro (MoonMath)](https://zro.moonmath.ai) | free-tier daily allowance (`deepseek-v4.1-flash`, resets daily, amount unpublished) | Pros: first-party inference, OpenAI-compatible, zero request retention and no training, no payment needed, reachable directly from Mainland China; Cons: daily free amount unpublished, only the Flash models are free, one account per person (no multi-account farming), end-to-end unverified | Unverified |
| [cheapllm.shop](https://cheapllm.shop) | limited-time free ($0 during beta, no rate limit; the ToS promises a permanent ≥5,000 / 1,000 tokens-per-hour allowance after beta) | Pros: signup is just email + password — no card, no phone, no email verification — and the key is issued immediately; OpenAI-compatible, reachable directly from Mainland China, no per-key rate limit; Cons: ⚠️ the legal notice leaves every operator detail blank, the service is about a week old with no third-party coverage, no SLA and accounts can be closed without reason, fallback inference providers may retain data for training, end-to-end unverified | Unverified |

> ⚠️ **No official free tier** (paid only, off-peak $0.15/$0.60 per 1M). Ollama Cloud and OrcaRouter do not offer free V4.1. ✅ Five genuine "free tier" entry points: **NVIDIA NIM** (permanent free at 40 RPM, no card), **ModelScope** (within its daily free allowance, direct access from China), **BeatAPI** (limited-time `deepseek-v4.1-flash-free`, zero balance works but only 1 request/minute), **Zro** (a free daily allowance, zero retention) and **cheapllm.shop** ($0 during beta; the ToS promises a permanent allowance of ≥5,000 / 1,000 tokens per hour after beta); Token Harbor is region-blocked; ⚠️ **Onomeo was redesigned on 2026-11-12 with its check-in mechanism removed and its free entry path unverified**, so it is no longer counted here as "check-in credits".

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
| [OpenCode Zen](https://opencode.ai/zen) | limited-time free (`deepseek-v4.1-flash-free`) | Pros: OpenCode's official gateway, no card, 1M context; Cons: ⚠️ verified 2026-10-24: the old `deepseek-v4-flash-free` is gone and the current id is `deepseek-v4.1-flash-free`, but **keyless calls return 403 `FreeTierError` — usable only inside the OpenCode client**; data may be used to improve the model during the free period, lineup flips back and forth | Client-locked |
| [Hugging Face](https://huggingface.co) | $0.10 free inference credits/month, pay-as-you-go beyond | Pros: huge model catalog, OpenAI-compatible; Cons: only $0.10/month free credit, pay-as-you-go after (hard stop), rate-limited shared endpoint, no SLA | Tiny quota |
| [ModelScope](https://modelscope.cn) | ~200 req/day | Pros: China-native, OpenAI-compatible, huge catalog; Cons: low-quality free tier — only ~200 req/day per model, shares a 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |
| [Intern InkStone Token Plan](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | free monthly ink-dot allowance during the beta, converted to tokens (1 ink dot covers up to 50,000,000 tokens, priced with DeepSeek-V4-Flash) | Pros: the only model the platform explicitly names as its conversion baseline, official Shanghai AI Lab platform, monthly top-up, OpenAI + Anthropic protocols; Cons: ⚠️ the exact monthly ink-dot grant was never published, you must sign in to check your balance, "up to" 50,000,000 per dot (faster models burn it quicker), research-oriented platform |  |

### GLM family

#### GLM-5.3 Flash

> Native multimodal, 320B, 1M context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | permanent (no token cap), 40 RPM | Pros: official hosting, no card, no credits or daily cap, 1.3M context & multimodal; Cons: SMS phone verification required, 40 RPM shared, queues at peak | Frequent timeouts |
| [OrcaRouter](https://www.orcarouter.ai) | free pool, rate-limited, zero markup | Pros: 200+ models behind one gateway, 0% token markup, no card; Cons: allowance unpublished, became the free default on 2026-09-07 replacing Qwen3.8-27B, high TTFT (~7.66s) | Rate-limited |
| [AMD Token Factory](https://developer.amd.com.cn/radeon/tokenfactory) | limited-time free (ZZ.ai) | Pros: official AMD hosting, ~$10/day; Cons: limited-time, high TTFT, rate-limited | High TTFT |
| [BeatAPI](https://beatapi.io) | limited-time free (`glm-5.3-flash-free`, $0 in / $0 out) | Pros: OpenAI-compatible, no card and no top-up, works on a zero balance, 2,000 successful requests/day; Cons: ⚠️ **only 1 successful request per minute before the first top-up** (10/min after), limited-time free tier, end-to-end calls unverified | Unverified |
| [Zro (MoonMath)](https://zro.moonmath.ai) | free-tier daily allowance (`glm-5.3-flash`, resets daily, amount unpublished) | Pros: first-party inference, OpenAI-compatible, zero request retention and no training, no payment needed, 236 tok/s, 1M context; Cons: daily free amount unpublished, only the Flash models are free, one account per person (no multi-account farming), end-to-end unverified | Unverified |
| ~~[Onomeo](https://onomeo.com/zh)~~ | ⚠️ mechanism unverified (2026-11-12) | ⚠️ After the redesign the ID `z-ai/glm-5.3-flash-free` no longer exists (it is now `glm-5.3-flash`, cost 7,701); check-in copy and the "50k/day premium cap" rule are both gone. The old "3,149 credits/answer, ~63 answers" figure is void |  |
| [Intern InkStone Token Plan](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | free monthly ink-dot allowance during the beta, converted to tokens (1 ink dot covers up to 50,000,000 tokens, priced with DeepSeek-V4-Flash) | Pros: official Shanghai AI Lab platform, monthly top-up, no card required, 1M context, OpenAI + Anthropic protocols; Cons: ⚠️ the exact monthly ink-dot grant was never published, you must sign in to check your balance, ⚠️ unverified whether GLM-5.3 is in the ink-dot free pool (the platform only names V4-Flash), research-oriented platform |  |

#### GLM 5.2 / 5.1

> Agentic-workflow flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenCode Zen](https://opencode.ai/zen) | limited-time free model (`glm-5.3-flash-free`) | Pros: official OpenCode gateway, no card; Cons: only the limited-time Flash tier is free, full GLM 5.3 is paid ($1.4/$4.4); ⚠️ verified 2026-10-24: Zen added `glm-5.3-flash-free` ($0), but keyless calls still return 403 `FreeTierError` — usable only inside the OpenCode client |  |

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

#### Qwen3 Coder Plus

> Code-specialised, 1M context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| — | **no free API channel** | ⚠️ Verified 2026-11-12: the xKiro AI catalog shrank from 97 to **69 models** and `access_tier: free` from 47 to **26**; **the entire Qwen lineup left the free tier** and none of the remaining free models is a Qwen. `qwen/qwen3-coder-plus` is gone from the catalog; the old free row is removed |  |

#### Qwen3 Coder 480B

> SOTA coding model, agentic coding

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| ~~[ModelScope](https://modelscope.cn)~~ | ⚠️ gone from catalog (2026-11-12) | ⚠️ Verified 2026-11-12: `api-inference.modelscope.cn/v1/models` has 38 entries and **no `Qwen3-Coder-480B`**; the old "~500 req/day" figure is void |  |

> ⚠️ **Qwen3 Coder 480B is no longer in the OpenRouter free lineup** (verified 2026-09-11).

#### Qwen3 235B

> General-purpose MoE flagship

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| ~~[ModelScope](https://modelscope.cn)~~ | ⚠️ gone from catalog (2026-11-12) | ⚠️ Same check: `Qwen3-235B` is not in the current 38-model catalog; the old "~500 req/day" figure is void |  |

> ⚠️ **Qwen3 235B is no longer in the OpenRouter free lineup** (verified 2026-09-11).

#### Qwen3.8 Max / Qwen3.7 Max

> Alibaba's flagship Max tier, 1M context (this repo previously had almost no decent free channel for Qwen)

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| — | **no free API channel** | ⚠️ Verified 2026-11-12: xKiro AI has removed `qwen/qwen3.8-max:free` and `qwen/qwen3.7-max:free`; no Qwen model is free there any more. The earlier "only free entry point to Qwen Max" claim is void |  |

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
| ~~[ModelScope](https://modelscope.cn)~~ | ⚠️ gone from catalog (2026-11-12) | ⚠️ Verified 2026-11-12: no `Qwen2.5-72B` in the catalog; current Qwen entries are `Qwen3.5-122B-A10B` / `Qwen3.5-397B-A17B` / `Qwen3.8-27B` / `Qwen3.8-Flash-Next` | Low quality |

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

> ⚠️ **MiniMax models have been pulled from NVIDIA NIM**: GLM-4.7 and MiniMax M2.1 were briefly listed in early September 2026 and removed on 2026-09-11; a 2026-09-27 re-check confirms **MiniMax M3 is not listed either** (NIM's catalog has no minimax entries at all); ✅ **2026-10-24 re-check: MiniMax is back on NIM** — `minimaxai/minimax-m3.1-flash` is listed (see below).

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

#### MiniMax M3.1 Flash

> New Flash tier listed in October 2026; as of 2026-11-12 **only NVIDIA NIM still offers it for free**

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [NVIDIA NIM](https://build.nvidia.com) | permanent (no token cap), 40 RPM | Pros: official hosting, no card, no credits or daily cap; Cons: SMS phone verification required, 40 RPM shared (verified in catalog 2026-10-24: `minimaxai/minimax-m3.1-flash`) | Frequent timeouts |

> ⚠️ **Verified 2026-11-12: two free channels failed at once** — Vercel AI Gateway moved `minimax/minimax-m3.1-flash` to paid pricing ($0.15/M input, $0.6/M output), and BeatAPI dropped `minimax-m3.1-flash-free` from its free lineup (now only 3 free models). Both rows are removed per this repo's rules; **NVIDIA NIM is the only free channel left here**.

#### Kimi K2.6

> 1T MoE, long-horizon coding, multimodal

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent (no token cap), 40 RPM | Pros: official hosting, no card, no credits or daily cap; Cons: SMS phone verification required, 40 RPM shared | Frequent timeouts |
| [Intern InkStone Token Plan](https://discovery.intern-ai.org.cn/token-plan/home?tabIndex=0) | free monthly ink-dot allowance during the beta, converted to tokens (1 ink dot covers up to 50,000,000 tokens, priced with DeepSeek-V4-Flash) | Pros: official Shanghai AI Lab platform, monthly top-up, no card required, OpenAI + Anthropic protocols; Cons: ⚠️ the exact monthly ink-dot grant was never published, you must sign in to check your balance, ⚠️ unverified whether Kimi K2.6 is in the ink-dot free pool (the platform only names V4-Flash), research-oriented platform |  |

#### Kimi K3

> 2.8T native multimodal agent, 1M context, long-horizon coding / complex reasoning

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| ~~[NVIDIA NIM](https://build.nvidia.com)~~ | ⚠️ delisted (2026-10-24) | ⚠️ verified 2026-10-24: `integrate.api.nvidia.com/v1/models` no longer carries `moonshotai/kimi-k3` (Kimi on NIM is now down to `kimi-k2.6`); K3 currently has **no free API channel** and the official API is paid |  |

#### StepFun Step 3.7 Flash

> China-native sparse-MoE reasoning model

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [ModelScope](https://modelscope.cn) | within shared quota (2,000 req/day site-wide) | Pros: China-native, reachable without a proxy, OpenAI-compatible, `stepfun-ai/Step-3.7-Flash` present in the `api-inference` catalog on 2026-11-12; Cons: shares the 2,000/day pool, Alibaba real-name, personal/non-commercial only | Low quality |

> ⚠️ NVIDIA NIM still has no Step 3.7 Flash (it added `stepfun-ai/step-5-preview` on 10-24); the earlier "no free API at present" note is outdated.

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
| [NVIDIA NIM](https://build.nvidia.com) | permanent (no token cap, 20B only) | Pros: official hosting, no card, no credits or daily cap; Cons: SMS phone verification required, 40 RPM shared, only hosts gpt-oss-20b | Frequent timeouts |

> ⚠️ **GPT-OSS is no longer in the OpenRouter free lineup** (verified 2026-09-11).

#### Reflection Beam

> Reflection AI's first open-weight model: 501B MoE (23B active per token), 1M context, Apache 2.0; weights released 2026-10-16. ⚠️ It previously circulated as the anonymous codenames `cat-jam` (OpenCode) / `MissingNo` (Nous Portal) — see [Stealth Models](#stealth-models)

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Vercel AI Gateway](https://vercel.com/ai-gateway) | limited-time zero-priced routes (`reflection/beam-free` and `reflection/beam`, both $0/$0) | Pros: served by Reflection itself, 1M context, adjustable reasoning effort, tool calling and structured outputs, zero data retention; Cons: ⚠️ limited-time, and the two ids behave differently — per the official note, the `-free` variant **stops serving when the free period ends** while the unsuffixed one silently rolls over to paid rates; using the free credit requires a payment method on file |  |
| [OpenCode Zen](https://opencode.ai/zen) | limited-time free (`beam-free`, client-only) | Pros: official OpenCode gateway, no card; Cons: ⚠️ verified 2026-11-12, a keyless call returns 403 `RegionError` ("This model is not available in your country") — **only usable inside the OpenCode client**, with an additional regional block | Client-locked |

> ⚠️ **Verified 2026-11-12: three channels left this section** — BazaarLink moved `reflection/beam` to paid pricing ($0.25/$1 per 1M) and dropped the `beam-free` zero-priced route; Kilo Gateway's `reflection/beam-free` now returns 404 "model does not exist" on a keyless call; Ollama Cloud has never published a starter free-model list and returns 401 without a key, so it is **not recorded as a free channel**. All three rows were removed per this repo's rules; Vercel AI Gateway and the externally unreachable OpenCode Zen are what remains.

> ⚠️ **Reflection's own API is a free public beta** (`https://api.reflection.ai/openai/v1`, model id `Beam-1.0-501B-A23B`), but **it publishes no per-token prices and you must register for a key**; on 2026-10-24 a keyless request was blocked at the edge with 403 (an HTTP-level block, not an auth response). Under this repo's rule that signup grants do not count, the official beta allowance is **not listed in the index**. On OpenRouter, `reflection/beam-1.0-501b-a23b` is **paid** ($0.25 / $1 per 1M) — don't confuse it with the free routes.

#### GPT-6 Astra

> OpenAI flagship model (`gpt-6-astra`)

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| ~~[Onomeo](https://onomeo.com/zh)~~ | ⚠️ mechanism unverified (2026-11-12) | ⚠️ After the redesign the premium list grew from 13 to 28 IDs, `dailyCap` fell to 10,000 and is flagged `buyersOnly: true`, and all check-in copy is gone. The old "3,948 credits/answer, ~12 calls/day, 13 premium models capped at 50k/day" figures are void; whether unpaid accounts can call at all is unconfirmed |  |

#### Gemini 2.5 Flash / Flash-Lite

> Google's free-tier workhorse, multimodal

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [Google AI Studio](https://aistudio.google.com) | daily reset (2.5 Pro 5 RPM/50 RPD, Flash 15 RPM/1,500 RPD, Flash-Lite 30 RPM/1,500 RPD) | Pros: official, free, no card, multimodal, 1M context; Cons: 2.5 Pro free tier is only 5 RPM/50 RPD (trial-only), needs Google account, free-tier data may be used for product improvement, real throughput far below nominal at peak |  |

#### Nemotron 3 Ultra / Super / Lightning

> NVIDIA agentic flagship, 1M context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` (Ultra / 3.5 Lightning / 3.5 Super VL / 3 Nano Omni — 5 routes) | Pros: aggregated routing; Cons: 50 free req/day, lineup rotates anytime; ⚠️ verified 2026-11-12: **`nemotron-3-super-120b-a12b:free` and `nemotron-3.5-content-safety:free` left the zero-priced pool** — Super returned on 10-24 and lasted only 19 days |  |
| [AIHubMix](https://aihubmix.com/models/free) | free tier (100 req/day after one-time $1 top-up) | Pros: subsidized free models, OpenAI-compatible, no card on signup; Cons: 10 trial calls only before top-up, 1M tokens/day shared across the free pool |  |
| [Kilo Gateway](https://kilo.ai) | free-tier $0 (`:free` variants, now 5 Nemotron routes) | Pros: **no signup, no key**, anonymous access documented by the vendor, 200 req/hr/IP; `nvidia/nemotron-3.5-lightning:free` returned 200 keyless on 2026-11-12; Cons: ⚠️ several non-Nemotron free routes left that catalog in the same round (see the channel entry), and all free models flag `mayTrainOnYourPrompts: true` |  |
| [NVIDIA NIM](https://build.nvidia.com) | permanent (no token cap), 40 RPM | Pros: NVIDIA's own flagship, no card, no credits or daily cap, 1M context; Cons: SMS phone verification required, 40 RPM shared, hosts Ultra/Lightning only (Super delisted) | Frequent timeouts |

#### InKling / ~~Ling 3.0 Flash~~ (new OpenRouter free entries)

> Thinking Machines' InKling and Ant's Ling 3.0 Flash, both multimodal with 1M / 262K context

| Free channel | Free tier | Pros / Cons | API quality |
|------|------|------|------|
| [OpenRouter](https://openrouter.ai) | `:free` (now just `inkling-2-small`) | Pros: 1M-context multimodal, aggregated routing; Cons: 50 free req/day, lineup rotates anytime; ⚠️ verified 2026-11-12: both old `inkling` / `inkling-small` routes left the zero-priced pool and the three Ling 3.0 Flash routes have not returned; two unrelated models joined the pool in the same round — see [Free Channels](#free-channels) |  |

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
| [NVIDIA NIM](https://build.nvidia.com) | permanent (no token cap, 31B only) | Pros: official hosting, no card, no credits or daily cap; Cons: SMS phone verification required, 40 RPM shared, NIM hosts only `gemma-4-31b-it`, no 26B-A4B | Frequent timeouts |

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
| ~~[ModelScope](https://modelscope.cn)~~ | ⚠️ gone from catalog (2026-11-12) | ⚠️ Verified 2026-11-12: the 38-model catalog no longer contains `deepseek-ai/DeepSeek-R1`; the old "~200 req/day" figure is void | Low quality |

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
- **Free tier**: permanent (**no token cap / no credits**, 40 RPM shared site-wide, no daily cap)
- **What the site says**: "100+ models free to call" — NVIDIA-hosted inference endpoints, sign up and go, no credit card. ⚠️ **The mechanism has changed: the old "~1,000 credits" allowance is gone.** NVIDIA's account verification dialog now reads *"Unlimited API requests without daily limits"* — there is no token quota any more, and **the only ceiling is roughly 40 RPM per key** (no official way to raise it on the free tier)
- **Free models**: **`deepseek-ai/deepseek-v4.1-flash`**, **`z-ai/glm-5.3-flash`**, `moonshotai/kimi-k2.6`, `google/gemma-4-31b-it`, `nvidia/nemotron-3-ultra-550b-a55b` / `nemotron-3-super-120b-a12b` / `nemotron-3.5-lightning-30b-a3b`, `openai/gpt-oss-20b`, `mistralai/mistral-large` / `mistral-large-2-instruct` / `mistral-large-4-1t-a52b`, `poolside/laguna-xs-2.1`, `minimaxai/minimax-m3.1-flash`, `stepfun-ai/step-5-preview` and more (verify via `/v1/models`; ⚠️ re-checked 2026-11-12: **the non-flash `z-ai/glm-5.3` is gone**; V4 Flash 0731, V4 Pro 0813 and `moonshotai/kimi-k3` remain delisted)
- **Endpoint**: `https://integrate.api.nvidia.com/v1` (OpenAI-compatible)
- **Sign-up requirement**: **SMS phone verification is mandatory** (the API key page shows a "We'll need to verify your phone number" modal and withholds the key until a one-time code is entered). ⚠️ Some country/region prefixes are not on the supported list and cannot register at all; NVIDIA states virtual numbers and borrowed SIMs violate its terms and risk account revocation
- **Status**: Active — verified 2026-11-12 (`/v1/models` returns **84 models**, one fewer than the 85 on 10-24). Changes this round: ❌ the non-flash `z-ai/glm-5.3` left, leaving only `z-ai/glm-5.3-flash`; ✅ `minimaxai/minimax-m3.1-flash` and `stepfun-ai/step-5-preview` are still listed, as are `mistralai/mistral-large-4-1t-a52b` and `meta/muse-glimmer-30b`; ❌ `moonshotai/kimi-k3` has not returned. DeepSeek is still just `deepseek-ai/deepseek-v4.1-flash` and `deepseek-coder-6.7b-instruct` — **V4 Flash / V4 Pro have no free NIM tier**; Qwen / Ling are absent and GLM 5.2 / 5.1 / 4.7 have not returned. ⚠️ Model count alone hides roster churn — always check exact IDs

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
- **Available models (require purchased credits)**: the cloud catalog measured **23 models** on 2026-11-12 — glm-5.3-flash, deepseek-v4.1-flash (incl. `:1017`), deepseek-v4-pro, gpt-oss:20b / 120b, mimo-v2.6-flash / pro, kimi-k2.6 / k2.7-code / k3 / k3.1-pro, muse-spark-open, glm-5.2 / 5.3, minimax-m3 / m3.1-flash, mistral-large-4, gemma4:31b, nemotron-3-super / ultra, clef:27b, beam (**every one is metered on the pricing page; none is $0**)
- **Endpoint**: `https://ollama.com/api/chat` (Ollama API; API key: https://ollama.com/settings/keys — **calling without a key returns `{"error":"Unauthorized"}`**)
- **Status**: Active (**listed in no model free index**) — re-checked 2026-11-12: the cloud catalog grew from 20 to **23 models**, but the conclusion is unchanged. `/api/tags` is just the cloud catalog, not a free list; all 23 are metered with none at $0, and a keyless call to `beam` returns 401 `Unauthorized`. The FAQ says the Free plan includes only "a starter amount of usage for a smaller set of starter models", and **that starter list has never been published**, so this repo records no specific model as "free on Ollama Cloud". Free plan: 1 concurrent request, monthly allowance resets on the signup anniversary and does not roll over

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
- **Status**: ~~Active — verified 2026-08-31~~ **expired (legacy platform fully shut down on 2026-09-30)** — Hunyuan-Lite's "free forever" is over, no longer qualifies for inclusion, entry kept for reference (re-confirmed 2026-11-12)

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
- **Free models**: the `api-inference` catalog measured **38 models** on 2026-11-12: `deepseek-ai/DeepSeek-V4.1-Flash` / `DeepSeek-V4.1-Flash-1017` / `DeepSeek-V4-Flash-0731` / `DeepSeek-V4-Pro`, `stepfun-ai/Step-3.7-Flash` / `Step-5-Preview`, `Qwen/Qwen3.5-122B-A10B` / `Qwen3.5-397B-A17B` / `Qwen3.8-Flash-Next`, `MiniMax/MiniMax-M3`, `ZhipuAI/GLM-4.7-Flash` / `GLM-5.2`, `moonshotai/Kimi-K3.1-Pro` and more; ❌ **Qwen3 Coder 480B, Qwen3 235B, Qwen2.5 72B and DeepSeek-R1 are not in the current catalog**
- **Endpoint**: `https://api-inference.modelscope.cn/v1` (OpenAI-compatible)
- **Status**: Active — verified 2026-11-12 (⚠️ **this entry follows the live `api-inference` `/v1/models`, which returned 38 models that day**, one more than the 37 on 10-24): ✅ joined — `stepfun-ai/Step-3.7-Flash` (previously recorded here as "no free API", now corrected), `ZhipuAI/GLM-4.7-Flash`, `moonshotai/Kimi-K3.1-Pro` and others; ❌ `Qwen3 Coder 480B`, `Qwen3 235B`, `Qwen2.5 72B` and `DeepSeek-R1` are still absent. Requires an Alibaba Cloud account + real-name verification
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
- **Free models**: ~~`typesafe-ai/jev` (limited-time promo now over)~~ plus **zero-priced routes (which do not spend the $5 credit)** — the 2026-11-12 catalog of 507 models has **11 with both input and output priced at $0**: `reflection/beam` / `reflection/beam-free`, `nvidia/nemotron-3.5-lightning-free`, `stealth/glyph-cluster` (stealth model — see [Stealth Models](#stealth-models)), `humansand/ampersand-v0.1`, and six **speech-to-text** models (`elevenlabs/scribe-v2`, `microsoft/mai-transcribe-2`, `mistral/voxtral-mini-transcribe-3` / `voxtral-small-transcribe-3`, `openai/gpt-transcribe`, `spacexai/grok-stt`). ⚠️ **`minimax/minimax-m3.1-flash` has moved to paid pricing** ($0.15/$0.6 per 1M), `convaiinnovations/laya` no longer has $0 input, and `poolside/laguna-s-2.1-free` was delisted. Vercel still publishes no full whitelist; the zero-priced routes and the "$5 free credit" are two separate free mechanisms
- **Endpoint**: `https://ai-gateway.vercel.sh/v1` (OpenAI-compatible); ⚠️ **Jev must go through the Evaluation endpoint `POST /v1/evaluate`** with a `{model, state, questions}` body — it **cannot be called via `chat/completions`** (verified 2026-09-20: `/v1/evaluate` with the Jev model returns `Authentication failed`, i.e. the endpoint is correct but unauthenticated, whereas `/v1/evaluations` and `/v1/decisions` both return 404)
- **Status**: Active ($5/month free tier + zero-priced routes) — verified 2026-11-12 (① **the Jev promo ended on 2026-09-25**, back to TypeSafe list price, so Jev is out of the free index; ② the free credit requires a valid payment method on file, but no top-up means no charge; ③ **once you buy credits, the account moves to the paid tier and the monthly $5 credit is gone for good**; ④ free-tier rate limits are lower, excess requests return 429; ⑤ **zero-priced routes do not consume the $5 credit**, but they are also time-limited — the MiniMax M3.1 Flash switch to paid pricing this round is a live example)

#### OpenRouter

- **Official site**: https://openrouter.ai
- **Free tier**: permanent (`:free` models, 50 req/day and 20 req/min; 1000/day after a $10 lifetime top-up)
- **What the site says**: multi-model router exposing a `:free` lineup; `openrouter/free` auto-routes between them (⚠️ the widely-quoted "200 req/day" is outdated — the official limits page states 50/1000)
- **Free models**: the 2026-11-12 check shows **16 zero-priced routes** (two are Google Lyria music generators and `openrouter/free` is an auto-router, so **13 usable text `:free` models**): `baidu/ernie-5.5-flash-preview:free`, `thinkingmachines/inkling-2-small:free`, `liquid/lfm-3-1.7b:free`, `recursive/flint-v1.0:free`, `nvidia/nemotron-3-ultra-550b-a55b:free` / `nemotron-3.5-lightning:free` / `nemotron-3.5-super-vl:free` / `nemotron-3-nano-omni-30b-a3b-reasoning:free`, `cohere/north-mini-code:free`, `dots-studio/dots-3-note-preview:free`, `liquid/lfm-2.5-2.6b:free`, `google/gemma-4-26b-a4b-it:free` / `gemma-4-31b-it:free` (**lineup rotates** — no DeepSeek / GLM / Qwen / MiniMax / Kimi / Ling in the free pool; check `openrouter.ai/models?max_price=0` before use)
- **Endpoint**: `https://openrouter.ai/api/v1` (most model names need the `:free` suffix; ⚠️ the exception is `stealth/space-bunny-alpha`, which carries no suffix and is already priced at 0 — appending one returns 404. See [Stealth Models](#stealth-models))
- **Status**: Active — verified 2026-11-12 (**468 models** in the catalog, **16 zero-priced routes**, down from 20 on 10-24): ✅ joined — `baidu/ernie-5.5-flash-preview:free`, `thinkingmachines/inkling-2-small:free`, `liquid/lfm-3-1.7b:free`; ❌ left — `thinkingmachines/inkling` / `inkling-small`, `nvidia/nemotron-3-super-120b-a12b:free` (back for only 19 days), `nvidia/nemotron-3.5-content-safety:free`, `xingchen-agi/xing4.0-29b-a4b:free`, `poolside/laguna-s-2.1` / `laguna-xs-2.1`. 50 req/day, 1,000 after a $10 top-up. ⚠️ The pool can swap four models in a week; "free on launch day" is a cold-start signal, not a promise — keep a fallback

#### Kilo Gateway

- **Site**: https://kilo.ai (the official Kilo Code gateway; [docs](https://kilo.ai/docs))
- **Free tier**: ✅ **anonymous access is officially supported** — the docs say "The gateway allows unauthenticated access for free models only. Anonymous requests are identified by IP address and are subject to rate limiting (**200 requests per hour per IP**)", i.e. **you can call every `:free` model without signing up or holding a key**
- **Notes**: proxies the free pools of OpenRouter / NVIDIA / Poolside / Recursive and others behind one endpoint; paid models require sign-in (verified: 401 `PAID_MODEL_AUTH_REQUIRED`) while free models need no auth at all
- **Free models**: the 2026-11-12 `/v1/models` check shows **383 models**, **12 with `isFree: true`**: `nvidia/nemotron-3-ultra-550b-a55b:free`, `nvidia/nemotron-3.5-lightning:free`, `nvidia/nemotron-3.5-super-vl:free`, `nvidia/nemotron-3-nano-omni-30b-a3b-reasoning:free`, `baidu/ernie-5.5-flash-preview:free`, `thinkingmachines/inkling-2-small:free`, `liquid/lfm-3-1.7b:free`, `dots-studio/dots-3-note-preview:free`, `cohere/north-mini-code:free`, `stealth/glyph-cluster` (stealth model — see [Stealth Models](#stealth-models)), `openrouter/free`, `kilo-auto/free`
- **Endpoint**: `https://api.kilo.ai/api/gateway/v1` (OpenAI-compatible; `https://api.kilo.ai/api/gateway` works too)
- **Status**: Active — verified 2026-11-12 (✅ **still the only channel in this repo confirmed reachable at 200 with no signup and no key**: keyless POSTs to `baidu/ernie-5.5-flash-preview:free`, `nvidia/nemotron-3.5-lightning:free` and `stealth/glyph-cluster` all returned 200; paid models return 401 `PAID_MODEL_AUTH_REQUIRED`; the docs still state the 200 req/hr/IP anonymous limit). ⚠️ Heavy churn in the free pool: `reflection/beam-free` (**now 404, model does not exist**), `recursive/flint-v1.0:free`, `poolside/laguna-*:free`, `liquid/lfm-2.5-2.6b:free` and `nvidia/nemotron-3-super-120b-a12b:free` have all left; `thinkingmachines/inkling-2-small:free` returns 403 "not available in your region". ⚠️ **All 12 free models flag `mayTrainOnYourPrompts: true`** — never send sensitive data; the limit is per egress IP, so shared exits contend with each other

#### AIHubMix

- **Official site**: https://aihubmix.com (free model list: https://aihubmix.com/models/free)
- **Free tier**: free models (10 trial calls on signup, no expiry; a one-time $1+ top-up permanently switches to daily quotas: 100 req/day and 1M tokens/day, reset daily)
- **What the site says**: "56 free models — no credit card required"; the platform subsidizes inference cost — every free model bills $0 in & out
- **Free models**: glm-4.7-flash-free, hy3-free, minimax-m3-free, k2.6-code-preview-free, gpt-oss-20b-free, nemotron-3-ultra/super-free, gemma-4-31b-it-free, xiaomi-mimo-v2.5(-pro)-free, coding-glm-5.3-free, gpt-5.5-free, gemini-3.8-flash-free and 50+ more
- **Endpoint**: `https://aihubmix.com/v1` (Chat Completions / Messages / Responses compatible)
- **Status**: Active — verified 2026-09-05 ($1 top-up required for daily quotas; shared free pool)

#### OpenCode Zen

- **Official site**: [https://opencode.ai/zen](https://opencode.ai/zen) ([pricing](https://opencode.ai/docs/zen/))
- **Free tier**: limited-time free models (Beam, Flint 40B, MiMo-V2.6-Flash, Nemotron 3.5 Super VL / Lightning, DeepSeek V4.1 Flash, GLM-5.3 Flash, MiniMax M3.1 Flash, LongCat 2.5, Iceman, Inkling 2 Small — $0 across input, output and cache reads/writes; the lineup rotates roughly every two weeks)
- **What the site says**: OpenCode's official model gateway; the pricing page explicitly marks the free models as Free and notes they are "available for a limited time while the team collects feedback"; **the platform itself is not free** — the full DeepSeek / GLM / Kimi / Qwen editions are pay-per-token
- **Free models**: the 2026-11-12 `/v1/models` check still shows **85 models**, but **11 `-free` entries** (plus the unsuffixed `big-pickle`): `beam-free`, `flint-40b-free`, `mimo-v2.6-flash-free`, `nemotron-3.5-super-vl-free`, `nemotron-3.5-lightning-free`, `deepseek-v4.1-flash-free`, `glm-5.3-flash-free`, `minimax-m3.1-flash-free`, `longcat-2.5-free`, `iceman-free`, `inkling-2-small-free`. ⚠️ **Four in, one out this round**: added minimax-m3.1-flash / longcat-2.5 / iceman / inkling-2-small, dropped `jev-1.13-free`; `space-bunny-free` is still absent
- **Endpoint**: `https://opencode.ai/zen/v1` (OpenAI-compatible; some models use `/messages` Anthropic or `/responses`)
- **Status**: Active (limited-time, but **not callable from outside**) — verified 2026-11-12 (✅ 85 models, 11 `-free` entries; ⚠️ **the external endpoint still does not work**: `beam-free` returns 403 `RegionError` and `iceman-free` returns 429 `FreeUsageLimitError` ("Free models work in OpenCode") without a key — the same client-binding mechanism as the earlier 403 `FreeTierError`, just a different error code; a valid key also gets 403. In practice Zen's free tier only matters inside the OpenCode client)

#### OrcaRouter

- **Official site**: [https://www.orcarouter.ai](https://www.orcarouter.ai) ([docs](https://docs.orcarouter.ai))
- **Free tier**: free pool rate-limited per workspace (allowance unpublished); **0% token markup** on the paid side (pass-through at upstream list price)
- **What the site says**: an OpenAI-compatible LLM routing gateway with 200+ models behind one endpoint; free models are catalog models exposed under separate free IDs with identical weights/capabilities, running in an isolated rate-limited pool — **a saturated free model will not silently fall back to its paid counterpart**
- **Free models**: re-checked 2026-11-12, `/v1/models` has **215 models** and **6 free routes**: `orcarouter/free` (difficulty-aware routing across the free pool), `z-ai/glm-5.3-flash-free`, `deepseek/deepseek-v4-flash-free`, `deepseek/deepseek-v4.1-flash-free`, `tencent/hy3-free`, `tencent/hy4-preview-free` (`deepseek-v4.1-flash-free` is 0 across all pricing fields; most of the others only price `request` at 0); ❌ `orca/orcaverify-text1.0-free` has left the catalog
- **Endpoint**: `https://api.orcarouter.ai/v1` (OpenAI-compatible, no card required)
- **Status**: Active (rate-limited) — verified 2026-11-12 (215 models / 6 free routes; on 2026-09-07 the free default switched from Qwen3.8-27B to GLM-5.3 Flash: quality 4→8, context 262K→1M, but TTFT 1.96s→7.66s and throughput 196→74 tok/s; ⚠️ unfunded accounts get a smaller daily allowance, `429 + Retry-After` means rate limiting while a 429 without that header means the prompt is too long; the vendor calls this best-effort, not production capacity)

#### Onomeo

- **Official site**: https://onomeo.com/zh ([models page](https://onomeo.com/zh/models))
- **Free tier**: ⚠️ **mechanism changed, unverified (2026-11-12)**: the old "daily check-in credits funded by survey revenue" story can no longer be reproduced on the site — neither `/zh/models` nor the homepage mentions check-ins or a free allowance, and the embedded config now reads `survey: false`, `invite.days: 0`, `invite.calls: 0`. **Treat the 2026-09-27 allowance and cost figures below as a historical snapshot; do not use them to estimate call counts**
- **Paid tier**: current rules read from the config embedded in `/zh/models` on 2026-11-12: `premium.models` has grown to **28 IDs** (including aliases; new entries are `gpt-6.1-terra` / `gpt-6.1-sol`, `claude-fable-5.2`, `kimi-k3.1-pro`, `glm-5.3-flash`, `gemini-3.8-flash`, `mimo-v2.6-*`, `deepseek-v4.1-flash-1017`, `hy4-preview` and others), with `premium.dailyCap: 10000`, `premium.buyersOnly: true` and `trialCalls: 0`; the paid plan is **$5 / 3,000,000 credits per month**. ⚠️ This is **tighter** than the old rule where unpaid accounts could still spend 50,000 credits/day on premium models — premium models are now flagged as buyers-only
- **What the site says**: a Chinese aggregator gateway with an OpenAI-compatible endpoint; verified 2026-11-12, `/zh/models` has been redesigned into a model leaderboard (showing reference price per million output tokens and uptime), with 71 records in the embedded `rows` (~28 unique models) and a largely new set of model IDs
- **Model costs (2026-11-12, from the embedded `rows`; relative comparison only)**: `deepseek-flash` 2,368; `hy4-preview` 705; `glm-5.3` 845; `kimi-k3` 1,560; `claude-haiku-5.5` 1,770; `gpt-6.1-sol` 3,348; `gemini-3.8-flash` 3,755; `deepseek-v4.1-flash-1017` 5,609; `gpt-6-luna` 7,168; `glm-5.3-flash` 7,701; `gpt-6.1-terra` 18,859; `claude-sonnet-5.5` 45,615; `claude-opus-5.5` 57,811; `grok-4.7` 140,810; `qwen3.8-max` 396,776 (credits/answer; `null` means no sample yet). ⚠️ The IDs in the old table — `deepseek-v4.1-flash` 8,409, `z-ai/glm-5.3-flash-free` 3,149, `gpt-6-astra` 3,948 — no longer exist in the current catalog
- **Endpoint**: `https://onomeo.com/v1` (OpenAI-compatible; a keyless call returned 401 `bad_key` on 2026-09-22, endpoint unchanged on 2026-11-12, reachable directly from Mainland China)
- **Status**: ⚠️ **mechanism unverified (2026-11-12)** — after the redesign, check-in/survey copy is gone and premium is flagged `buyersOnly`; **this repo cannot confirm that any no-payment allowance still exists**. Other config captured: `perMinute: 60`, `perAccountWindowMax: 30`, `perIpWindowMax: 60`, `windowMinutes: 300` (all tighter than the 60 / 120 recorded on 9-27), and most `training` values are `trains`. Until the vendor documents a free path again, **do not rely on Onomeo as a stable free channel**; check the index rows that reference it too

#### Chutes ~~(retired)~~

~~Retired (re-checked 2026-11-12: **19 models, all metered, none at $0** — 11 are `-TEE` variants, plus non-TEE entries such as `deepseek-ai/DeepSeek-V4.1-Flash-1017`, `Qwen/Qwen3.8-Max-0902`, `zai-org/GLM-5.3` and `tencent/Hy4`, all pay-as-you-go; DeepSeek V4 Flash 0731 is $0.039/$1.25): no free endpoint found in `llm.chutes.ai/v1/models`; kept for reference.~~

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
- **Status**: ⚠️ **endpoint in maintenance (2026-11-12)** — the homepage now shows "MAINTENANCE / We are preparing the free endpoint for Free API. Quick restart in progress", and both `/v1/models` and `/v1/chat/completions` return 503 `maintenance` ("The endpoint is offline for now and will be back soon"). **It is completely unusable right now**; the vendor asks people to watch its X account for the restart and gives no ETA. The earlier "often `upstream_down`" note has escalated to a full outage — treat as unavailable

#### BazaarLink

- **Official site**: https://bazaarlink.ai ([free-model rules](https://bazaarlink.ai/docs/api#free-models))
- **Free tier**: free model tier (`auto:free` smart routing across the free pool plus five more, $0 in / $0 out, rate-limited, no card required). ✅ **The allowance is published now** (the old "allowance unpublished" note is outdated): accounts without credit get **10 RPM / 60 weighted units per day**, credited accounts **20 RPM / 120 per day**, a 20 RPM site-wide free cap, 2 concurrent free requests per account, resetting daily at 00:00 UTC; longer inputs burn more units
- **What the site says**: a Taiwan-based LLM gateway; the site lists "1 free model" and notes "free allowance, auto-switching to paid billing beyond it"; `auto:free` routes to whichever free model currently fits best
- **Free models**: verified 2026-11-12, `/v1/models` has **125 models** and **7 routes priced at $0 on both ends**: `qwen/qwen3.7-flash:free`, `nvidia/nemotron-3.5-lightning-free:free`, `nemotron-3.5-lightning-free`, `glyph-cluster`, `stealth/glyph-cluster:free` (stealth model — see [Stealth Models](#stealth-models)), `deepseek/deepseek-v4-flash-0731free:free`, `auto:free` (smart routing across the free pool). ⚠️ **`reflection/beam` and `reflection/beam-free` have left the free pool** (`beam` is now metered at $0.25/$1 per 1M)
- **Endpoint**: `https://api.bazaarlink.ai/v1` (OpenAI-compatible)
- **Status**: Active (small gateway) — verified 2026-11-12 (✅ `/v1/models` returns **125 models** with 7 zero-priced routes, free tier still alive; ✅ allowance rules unchanged: **10 RPM / 60 weighted units per day** without credit, **20 RPM / 120** with credit, 20 RPM site-wide free cap, 2 concurrent requests per account, resets 00:00 UTC; ⚠️ roster churn — both Reflection Beam routes moved to paid; ⚠️ self-serve agent registration was disabled on 2026-09-05 to curb abuse, so sign up normally and create a key in the dashboard)


#### xKiro AI

- **Site**: https://xkiro.com ([docs](https://docs.xkiro.com))
- **Free tier**: a free tier (models flagged `access_tier: free` cost nothing), recorded by third-party catalogs as **5M tokens/day, free models only**; speaks both OpenAI `/v1/chat/completions` and Anthropic `/v1/messages`
- **Notes**: aggregates Qwen / Cohere / Mistral / MiniMax / Meituan and more; free models are flagged `access_tier: free` in the catalog. ⚠️ **As of 2026-11-12 the Qwen lineup is gone entirely** — the remaining free set is Mistral, Cohere and Sensenova only
- **Free models**: ⚠️ verified 2026-11-12, `/v1/models` **shrank from 97 to 69 models** and `access_tier: free` **from 47 to 26**, with **the entire Qwen lineup removed**. The 26 remaining free models are Mistral (`mistral-large-2512` / `medium-3.5` / `small-2603` / `devstral-medium` / `codestral-2508` / `ministral-*`), Cohere (`command-a` / `command-a-plus` / `command-a-reasoning` / `command-a-vision` / `command-r*` / `north-mini-code` / `north-small-translate` / `aya-*` / `tiny-aya-*`), `sensenova/sensenova-6.8-flash-lite` and `stealth/big-pickle`. ❌ `qwen3.8-max` / `qwen3.7-max` / `qwen3-coder-plus` and all other Qwen models have left the catalog
- **Endpoint**: `https://api.xkiro.com/v1` (OpenAI-compatible; accepts either `Authorization` or `x-api-key`)
- **Status**: Active (small gateway, **but the free roster collapsed**) — verified 2026-11-12 (⚠️ a key is still required: keyless POST returns 401 `Missing ClientApiKey`, end-to-end calls remain unverified; ⚠️ **this repo's earlier claim that xKiro was "the only free entry point to Qwen Max / Coder Plus" is void** — all Qwen free models disappeared within two weeks; catalog 97 → 69, free 47 → 26, faster churn than the OpenRouter free pool. The third-party "5M tokens/day" figure also needs re-verification)

#### BeatAPI

- **Official site**: [https://beatapi.io](https://beatapi.io) ([pricing](https://beatapi.io/zh/pricing), [docs](https://docs.beatapi.io/zh))
- **Free tier**: limited-time free models — the Free category whose ids end in `-free`, $0 per 1M tokens on both input and output; **no card, no top-up, callable on a zero balance**. Per-account limits: **2,000 successful requests/day**, plus **1 successful request per minute before the first top-up** and **10 per minute after any top-up** (regardless of amount). This pool is counted **separately** from the paid rate tiers, so free calls do not consume paid allowance
- **What the site says**: a discounted reseller gateway (text/image/video models plus 1,000+ data APIs). The homepage advertises "4 models free for a limited time" and states: "each account can make 1 successful free call per minute before its first top-up, up to 10 after; the daily allowance is adjusted periodically. Free access is offered for a limited time and may be throttled or stopped. A top-up does not switch you to paid models automatically." The FAQ adds that free models "sit outside these tiers" and are counted in their own pool
- **Free models**: ⚠️ **only 3 $0 models remain on 2026-11-12** (the keyless `POST /v1/capabilities/search` with `{"query":"free","kind":"model"}` returns `total: 3`): `deepseek-v4.1-flash-free`, `glm-5.3-flash-free`, `hy4-free`. ❌ All four others from the 11-02 check — `gemini-3.8-flash-free`, `minimax-m3.1-flash-free`, `jev-1.13-free`, `jev-1.14-free` — **have left**. The official `skill-refs/free-models.md` says the free lineup changes without notice and IDs must not be hardcoded; the homepage's "4 models free" copy is stale too
- **Endpoint**: `https://api.beatapi.io/v1` (OpenAI-compatible: `/v1/chat/completions` and `/v1/responses`; also Anthropic `/v1/messages` and the Gemini-native format; text can also use `https://direct.beatapi.io`). Create a key in the dashboard after signing up; free models work on a zero balance
- **Status**: Active (limited-time free, **end-to-end calls not verified by this repo**) — checked 2026-11-12 (✅ endpoint real: `/v1/models` returns `missing_api_key` without a key; ✅ the official `free-models.md` confirms no card / zero balance, 1 successful request per minute on free models before the first top-up (10/min after), and 429 responses carrying `retry_after_seconds`; ✅ reachable directly from Mainland China, no `region_blocked`; ⚠️ the free lineup went from 6 to 3 models in ten days; ⚠️ a small discount reseller launched in Oct 2026 with no SLA; ⚠️ the privacy policy says customer content is not used to train general models, but explicitly does not promise zero retention at every upstream)

#### Zro (MoonMath)

- **Official site**: [https://zro.moonmath.ai](https://zro.moonmath.ai) ([pricing](https://zro.moonmath.ai/pricing), [model catalog](https://zro.moonmath.ai/model-catalog), [docs](https://zro.moonmath.ai/docs))
- **Free tier**: the Free plan (**$0/month**) — a **daily free allowance that resets every day**, covering `deepseek-v4.1-flash` and `glm-5.3-flash`. No payment needed ("no card" is inferred from the $0 plan; signup untested). The exact daily amount is not published
- **What the site says**: MoonMath.ai's first-party private inference service for coding agents, marketed as "Private / Uncensored models". The pricing page states: "Free plan for Flash models. $0 per month. included daily usage. Free daily usage on GLM-5.3 Flash and DeepSeek V4.1 Flash. Resets every day," alongside "OpenAI-compatible API", "Zero request retention" and "No training on requests". Paid plans: Pro $20/month (with $40 usage), Max $60/month (with $120 usage); usage packs from $5, expiring after 90 days
- **Free models**: the free tier covers the two Flash models `deepseek-v4.1-flash` and `glm-5.3-flash`; paid-only models on the same platform — `glm-5.3`, `dolly1-security`, `dolly2-security` (the last two are "uncensored" security models) — are not on the free tier
- **Endpoint**: `https://zro.moonmath.ai/v1` (OpenAI-compatible `/v1/chat/completions` and `/v1/responses`); Anthropic Messages uses the base `https://zro.moonmath.ai`; `Authorization: Bearer sk-...`; every request authenticates and routes through an EU gateway, with inference running in the EU or US
- **Status**: Active (free tier, **end-to-end calls not verified by this repo**) — re-checked 2026-11-12 (✅ `/v1/models` still returns 401 `auth_error` without a key, endpoint real; ✅ reachable from Mainland China; ✅ pricing page still states a $0/month Free plan with a daily allowance covering `deepseek-v4.1-flash` and `glm-5.3-flash`, plus zero request retention and no training; ⚠️ **the exact daily allowance is still unpublished**; ⚠️ one account per person, young site with no SLA; ⚠️ the homepage fetch timed out this round, so the legal text was not re-read word by word)

#### cheapllm.shop

- **Official site**: https://cheapllm.shop ([pricing](https://cheapllm.shop/#stall), [docs](https://cheapllm.shop/docs/), [terms](https://cheapllm.shop/terms/), [privacy](https://cheapllm.shop/privacy/), [legal notice](https://cheapllm.shop/legal/))
- **Free tier**: limited-time free during the beta — $0 for input, output and cached input, with no claimed rate limit (4 MB request body, up to 25 keys per account; at peak, requests queue for up to 30 s before a 503 with `Retry-After`). **Both the ToS and the docs promise a permanent free allowance once the beta ends: at least 5,000 input / 1,000 output tokens per hour (rolling hour, per account, all keys combined), no card, and a floor that can only be raised.** Beyond it, usage is billed at $0.005 / $0.001 / $0.14 per 1M, and nothing is charged unless you add a payment method yourself. The end of the beta is announced by email, with no published date
- **What the site says**: a single-model small gateway. The homepage reads "free, no rate limit" and "free during the beta, no credit card"; the pricing section (`#stall`) strikes through $0.005 / $0.001 / $0.14 and shows $0.00, and the FAQ says "yes, as long as the beta lasts". Signup is just email + password — no card, no phone number, no email verification — and `/api/signup` hands back an `sk-cheap-` key immediately
- **Free models**: only `deepseek-v4.1-flash-1017`; the docs say any model name containing `deepseek` also routes to it, so tools with hardcoded model names work
- **Endpoint**: `https://cheapllm.shop/v1` (OpenAI-compatible `POST /v1/chat/completions` and `GET /v1/models`; `Authorization: Bearer sk-cheap-...`). ⚠️ The homepage suggests `curl -fsSL https://cheapllm.shop/setup.sh | sh`, which rewrites the base URL in 40 local tools (Claude Code, Codex CLI, Cursor and others) — edit configs by hand instead, and do not run it on a production machine
- **Status**: Active (limited-time free / small gateway, **end-to-end calls not verified by this repo**) — checked 2026-11-14 (✅ `GET /v1/models` returns 200 with only `deepseek-v4.1-flash-1017`; ✅ `POST /v1/chat/completions` returns 401 `invalid_api_key` without a key and 401 `not valid` with a bogus key, so the endpoint and auth layer are real; ✅ reachable directly from Mainland China; ⚠️ **every operator field the French LCEN requires on the legal notice page — name, legal form, registration number, address, phone, host — reads "not provided yet"**; ⚠️ domain registered 2026-03-28, first blog post 2026-11-08, terms updated 2026-11-12 — the service is about a week old with no third-party coverage; ⚠️ the ToS calls free access "a courtesy, not a right" and allows closing accounts, revoking keys or stopping the service without reason, with no SLA, while the homepage already warns of slowdowns from higher-than-expected demand; ⚠️ prompts are not written to disk, but when primary capacity is unavailable requests may go to fallback inference providers whose own terms can retain prompts and answers for model improvement, and the ToS allows swapping upstream providers without notice — the model behind the endpoint cannot be independently verified)

### Client-only free (no public API)

> These products lock their free allowance inside their own client: **no public endpoint and no API key you could use from a third-party app**. They are listed so readers know the models really are free to use there — **not** as a channel you can wire into your own program. Being in this section does not mean external calls are allowed; Freebuff's terms forbid them outright.

#### Freebuff

- **Official site**: [https://freebuff.com](https://freebuff.com) ([plans](https://freebuff.com/plans))
- **Free tier**: the Free plan grants "30 hours refilled daily" of session time (converted per model, not interchangeable across models); ad-funded, no card, no token metering
- **What the site says**: the free coding agent from the Codebuff team (Codebuff Pro is the paid tier), shipped as a CLI (`npm install -g freebuff`), a desktop app and a web app; the site calls itself "the free coding agent" and "funded by ads", and the plans page states the Free plan gets `30 hours refilled daily`
- **Free models**: the Free plan names MiMo v2.6 Flash (Slow / Fast), DeepSeek V4.1 Flash 10/17 and Claude Haiku 5.5 (100k context); the same page also carries an hours-per-day table for GLM 5.3 Flash, GPT-6 Luna, MiMo 2.6 Pro, Muse Spark 1.3, Nemotron 3.5 Lightning, Solar Mini 4 / Pro 4 and Glyph Cluster, without saying which plan each one belongs to
- **Endpoint**: **none public, no API key** — `/docs`, `/api/models` and `/api/v1/models` all land on the site's `Page not found` (checked 2026-10-29) and the only pages are product pages like the homepage, `/plans`, `/cli` and `/app`; the only credential is an `authToken` in the client's local `~/.config/manicode/credentials.json`
- **Status**: Active (client-locked, **not usable as an upstream**) — verified 2026-10-29 (⚠️ **the terms forbid external calls outright**: "Free Access and Human Use" bars anyone from accessing "the underlying servers or endpoints directly or through scripts, custom clients, wrappers, integrations, or third-party software", and also bans resell / rent / proxy / relay and shared accounts — community reverse proxies (Freebuff2API, freebuff2api-workers) therefore breach the terms and are not recommended here; ⚠️ **regional**: full mode covers only 25+ countries, everywhere else (or behind a VPN) drops to limited mode with DeepSeek V4 Flash alone and 6 one-hour sessions a day — and spoofing your region with a VPN itself violates the terms; ⚠️ **expensive privacy trade**: to target ads the clients scan project config/doc files and collect pre-send typing and interaction signals, and models labelled "May use data for AI training" may have their submissions licensed or sold to third parties for training; ⚠️ **the allowance contradicts itself**: the 2026-10-09 launch post describes limited mode as "DeepSeek V4 Flash + 6 × 1 hour" while the plans page says "30 hours a day" and its own conversion table shows 52 hours, and the terms reserve the right to change models and limits at any time)

#### AtomCode (CodingPlan)

- **Official site**: https://ai.atomgit.com/serverless-api
- **Free tier**: CodingPlan Lite trial — limited-time free, 500 claims/day, valid 7 days, ~200 calls per 5h rolling window
- **What the site says**: free quota inside AtomCode, the terminal AI coding tool from AtomGit (Zhipu ecosystem); **not a standard API channel** — the quota only works inside the AtomCode client, no third-party endpoint access
- **Free models**: mimo-v2.5, qwen3.8-27b, deepseek-v4-flash (per the client's model list)
- **Endpoint**: none public — install the AtomCode client and sign in with an AtomGit account to claim the quota
- **Status**: Active (limited-time) — verified 2026-09-05 (does not really meet this repo's "API key + endpoint" bar; listed for reference only)


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
- **Free lineups churn more than you think.** OpenRouter's `:free` lineup measured **19 → 21 → 17 → 20 → 16** on 2026-09-11 / 09-20 / 09-27 / 10-24 / **11-12**; `nemotron-3-super-120b` returned for only 19 days before leaving again, and `inkling` / `inkling-small` were replaced by `inkling-2-small`. NVIDIA NIM went 82 → 80 → 85 → **84**, swapping members every round. OpenCode Zen's `-free` lineup went from 8 to 11 in two weeks (Jev 1.13 out, four in). **xKiro AI went 97 → 69 models and 47 → 26 free in two weeks, with the entire Qwen lineup zeroed out. BeatAPI went 6 → 3 free models in ten days. Vercel's MiniMax M3.1 Flash zero-priced route switched straight to paid.** A listed model may be gone by the time you read this — run one `curl` before relying on it.
- **"Limited-time free" can end without warning.** Promo APIs (e.g. B.AI's former limited-time tier) publish no end date.
- **Some "free" tiers require a credit card**, a phone number, or real-name verification. Example: Vercel AI Gateway's $5/month free credit explicitly requires **a valid payment method on file** before it can be used (`To use free AI Gateway Credits, add a valid payment method to your team.`, verified 2026-09-20) — having a card on file does not mean being charged, but the barrier is real.
- **Not every "free model" generates text.** Structured decision models like Jev (state plus typed questions in, choices/scores/probabilities out) are served over Evaluation or Decisions APIs and **cannot be used as chat models**; OpenAI-compatible chat/completions calling conventions usually do not apply.
- **Your data may be used for training.** Google (free tier), Mistral (Experiment), Groq, and most OpenRouter `:free` upstreams train on free traffic; some let you opt out.
- **Small gateways are the least stable.** Newcomers like Token Harbor / BazaarLink are barely battle-tested — fine for prototypes, never for production.
- **"Free inside the client" is not a channel, and a reverse proxy is not a workaround.** Services such as Freebuff / OpenCode Zen / AtomCode lock their allowance to their own clients, and the community keeps shipping one-file reverse proxies that expose them as OpenAI-compatible APIs — but the terms usually forbid calling `endpoints directly` and forbid `proxy / relay` outright. Using one breaches the agreement, with suspension and quota clawback on you; this list keeps them in [Client-only free](#client-only-free-no-public-api) for reference only.
- **"Having credits" is not "being able to call freely."** Check-in/allowance platforms often cap daily spend on flagship models separately — Onomeo's 2026-09-27 snapshot had 13 premium models limited to 50,000 credits/day (300,000 after buying), so `gpt-6-astra` topped out near 12 calls/day. ⚠️ **But the site was redesigned by 2026-11-12**: premium grew to 28 IDs, `dailyCap` fell to 10,000 and is flagged `buyersOnly`, and all check-in copy is gone — the old conversion table is void. **The real ceiling is still per-call cost × daily cap (whichever is smaller), but first confirm the mechanism still exists.**
- **"Check-in for credits" is not a "free-tier model".** Onomeo once traded check-ins/surveys for a daily allowance — callable across the whole catalog but with wildly different costs (2026-09-27: `gemini-3.1-flash-lite` 9 credits vs `Qwen3.8-Flash-Next` 41,457, a 4,000x spread), and `deepseek-v4.1-flash` rose from 1,473 to 8,409 in five days. ⚠️ Verified 2026-11-12: the site is now a leaderboard, model IDs have all changed (`deepseek-flash` 2,368, `qwen3.8-max` 396,776), check-in copy is gone and `survey: false` is set. **No free entry path can currently be confirmed — do not reuse the old cost figures to estimate call counts.**
- **Some overseas gateways apply regional blocks.** Token Harbor returned `region_blocked`, explicitly refusing Mainland China, Hong Kong and Macao (2026-09-12). Even with a free allowance, such endpoints require an overseas network path from Mainland China — and the operator typically asks you to turn VPNs off, since it only sees the country your connection exits from.
- **"Free signup credits" ≠ free.** DeepSeek's official signup grant is confirmed gone (balance 0 as of 2026-08-31); the official channel is now "cheap", not "free".

## License

[MIT](LICENSE) — fork it, remix it, ship it; just keep the copyright notice.
