# Haofei Sun

**I build LLM systems where the model proposes and deterministic code decides.**

AI Agents · LLM Infrastructure · Deep Learning

**Open to full-time SWE / AI / ML Engineer roles.**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-haofei--sun-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/haofei-sun)
[![Email](https://img.shields.io/badge/Email-humphreysun98@gmail.com-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:humphreysun98@gmail.com)
[![arXiv](https://img.shields.io/badge/arXiv-2608.01619-B31B1B?style=flat&logo=arxiv&logoColor=white)](https://arxiv.org/abs/2608.01619)
[![PyTorch Merged](https://img.shields.io/badge/PyTorch_core-2_PRs_Merged-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://github.com/pytorch/pytorch/commit/b78a4fe7)
[![Anthropic PR Merged](https://img.shields.io/badge/Anthropic_claude--code--action-PR_Merged-D97757?style=flat)](https://github.com/anthropics/claude-code-action/pull/1488)
[![LangChain PR Merged](https://img.shields.io/badge/LangChain-PR_Merged-1C3C3C?style=flat)](https://github.com/langchain-ai/langchain-aws/pull/1085)
[![vLLM core PRs Merged](https://img.shields.io/badge/vLLM_core-2_PRs_Merged-FFD21E?style=flat)](https://github.com/vllm-project/vllm/pull/45466)
[![SGLang PRs Merged](https://img.shields.io/badge/SGLang-2_PRs_Merged-EE4C2C?style=flat)](https://github.com/sgl-project/sglang/pull/26971)
[![hermes-agent PRs Merged](https://img.shields.io/badge/Nous_hermes--agent-2_PRs_Merged-000000?style=flat)](https://github.com/NousResearch/hermes-agent/pull/64771)
[![LiteLLM PR Merged](https://img.shields.io/badge/LiteLLM-PR_Merged-00B8D9?style=flat)](https://github.com/BerriAI/litellm/pull/29707)
[![llm-compressor PR Merged](https://img.shields.io/badge/llm--compressor-PR_Merged-6236FF?style=flat)](https://github.com/vllm-project/llm-compressor/pull/2797)
[![vLLM production-stack Merged](https://img.shields.io/badge/vLLM_production--stack-3_PRs_Merged-30A14E?style=flat)](https://github.com/vllm-project/production-stack/pull/969)
[![SmartStudy on Chrome Web Store](https://img.shields.io/badge/Chrome_Web_Store-SmartStudy_Live-4285F4?style=flat&logo=googlechrome&logoColor=white)](https://chromewebstore.google.com/detail/edbjkpfjonahanfkamlcbobmnplihmik)
[![Archiagents Live](https://img.shields.io/badge/Archiagents-Live-FF6B35?style=flat)](https://archiagents.com)
[![LLM API Gateway](https://img.shields.io/badge/LLM_API_Gateway-api.manxuezhida.com-2496ED?style=flat)](https://api.manxuezhida.com)
[![Blog](https://img.shields.io/badge/Blog-SafetyCommander_Architecture-0A0A0A?style=flat&logo=devdotto&logoColor=white)](https://dev.to/humphreysun98/safetycommander-an-ai-safety-officer-where-the-model-reasons-and-the-code-never-decides-4765)

---

### Proof of Work

**16 merged pull requests** across the ML stack — [PyTorch](https://github.com/pytorch/pytorch/commit/e9cfafa) · [Anthropic](https://github.com/anthropics/claude-code-action/pull/1488) · [LangChain](https://github.com/langchain-ai/langchain-aws/pull/1085) · [vLLM](https://github.com/vllm-project/vllm/pull/45466) · [SGLang](https://github.com/sgl-project/sglang/pull/26971) · [Nous Research](https://github.com/NousResearch/hermes-agent/pull/64771) · [LiteLLM](https://github.com/BerriAI/litellm/pull/29707) — plus a first-author paper, an agent that designs real circuits, and products live in production.

|  | The fact | Why it's hard |
| --- | --- | --- |
| 🔥 | **Merged into PyTorch core**, reviewed by the **TorchInductor lead** ([`e9cfafa`](https://github.com/pytorch/pytorch/commit/e9cfafa)) | Couldn't build torch locally — proved runtime equivalence by diffing both versions across **18 behavioral dimensions**; then **unblocked my own merge** by proving an unrelated ROCm CI failure independent with four reproducible lines of evidence |
| ⚡ | **An agent loop that designs real analog circuits** (Summer 2026, Halo Microelectronics) | No numeric optimizer — LLM proposes experiment batches, a simulator holds authority over truth: **4 rounds, ~100× error reduction, 42 evaluations, 5 LLM calls, ~7 minutes**, beating the accuracy floor in the company's own codebase |
| 🔬 | **CUDA kernel correctness fix in vLLM core** (~85k★) ([#45466](https://github.com/vllm-project/vllm/pull/45466)) | The issue thread blamed FlexAttention, CUDA graphs, and drivers — the real cause was an unchecked destination-pointer alignment in the KV-cache write path; fixed for every caller |
| 📡 | **77 kHz BLE RSSI firmware** (Zephyr RTOS, nRF54L15) → **0.986 R²** recovering signals **5.3× below Nyquist** | 3× the highest published sampling rate, feeding a physics-informed network that recovers what classical sampling theory says is unrecoverable |
| 🧪 | **RepoAgentBench** — contamination-free coding-agent benchmarks ([PyPI](https://pypi.org/project/repoagentbench/)) | Public benchmarks overestimate agents by 20–50% via training-data contamination; mine *freshly merged* PRs so tasks postdate any model's cutoff — surfaced the same model producing **opposite outcomes** under two different harnesses |
| 🧵 | **Speculative-decoding correctness fix in vLLM** ([#45352](https://github.com/vllm-project/vllm/pull/45352)) | A silent config-propagation bug made a draft model instantiate at full 675B-scale dimensions in CI; fix required composing callable overrides *and* solving the pickling failure the composition introduced |
| 🏗️ | **Multi-tenant cache-routing crash fix in SGLang** (~29k★) ([#26971](https://github.com/sgl-project/sglang/pull/26971)) | A per-request key wasn't indexed per sub-request, silently collapsing prefix-cache isolation between tenants — fixed with a 6-path regression test across CPU, AMD, and CUDA CI |
| 💸 | **~6× prompt-token cost cut in LangChain** ([#1085](https://github.com/langchain-ai/langchain-aws/pull/1085)) | Repo-wide static analysis found `ensure_ascii` defaults silently escaping CJK/emoji to `\uXXXX` across 11 sites in 3 modules — the kind of bug nobody sees because every request still succeeds |
| 🚢 | **Shipped and live:** [archiagents.com](https://archiagents.com) · [Chrome Web Store](https://chromewebstore.google.com/detail/edbjkpfjonahanfkamlcbobmnplihmik) · [LLM gateway](https://api.manxuezhida.com) | Real users, real uptime, real billing — including the honestly-reported finding that a rule-based heuristic beat Q-learning, so the heuristic shipped |

<details>
<summary><b>For recruiters · researchers · founders — 10-second version</b></summary>

- **Recruiters:** 16 merged PRs across PyTorch / Anthropic / LangChain / vLLM / SGLang · shipped products · Dec 2026 grad seeking SWE/AI/ML roles.
- **Researchers:** first-author on agent memory verification · contamination-free agent benchmarking · AAAI & IEEE-HKN member.
- **Founders:** I build end to end and ship — agent systems with real verifiers, a live AI product, and a production LLM gateway serving my own downstream apps.

</details>

---

### Tech Stack

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=flat&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat&logo=cplusplus&logoColor=white)
![CUDA](https://img.shields.io/badge/CUDA-76B900?style=flat&logo=nvidia&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Verilog](https://img.shields.io/badge/Verilog-B22222?style=flat)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat&logo=gnubash&logoColor=white)

**ML Systems & AI**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![vLLM](https://img.shields.io/badge/vLLM-FFD21E?style=flat)
![SGLang](https://img.shields.io/badge/SGLang-EE4C2C?style=flat)
![Quantization](https://img.shields.io/badge/AWQ%2FSmoothQuant-6236FF?style=flat)
![Speculative Decoding](https://img.shields.io/badge/Speculative_Decoding-8A2BE2?style=flat)
![Claude](https://img.shields.io/badge/Claude_API-D97757?style=flat&logo=anthropic&logoColor=white)
![GPT](https://img.shields.io/badge/GPT_API-412991?style=flat&logo=openai&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini_API-4285F4?style=flat&logo=google&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat)
![MCP](https://img.shields.io/badge/MCP-000000?style=flat)
![RAG](https://img.shields.io/badge/RAG-0A9396?style=flat)
![Transformers](https://img.shields.io/badge/Transformers-FFD21E?style=flat&logo=huggingface&logoColor=black)
![Vercel AI SDK](https://img.shields.io/badge/Vercel_AI_SDK-000000?style=flat&logo=vercel&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)

**Backend & Web**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat&logo=flask&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind_v4-06B6D4?style=flat&logo=tailwindcss&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)

**Infrastructure & HPC**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat&logo=kubernetes&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI%2FCD-2088FF?style=flat&logo=githubactions&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-4285F4?style=flat&logo=googlecloud&logoColor=white)
![OpenMP](https://img.shields.io/badge/OpenMP-0070D1?style=flat)
![MPI](https://img.shields.io/badge/MPI-003594?style=flat)
![VPS](https://img.shields.io/badge/VPS_Deployment-0F4C5C?style=flat)

**Embedded & Hardware**

![Zephyr](https://img.shields.io/badge/Zephyr_RTOS-512BD4?style=flat)
![nRF](https://img.shields.io/badge/nRF54L15-00A9CE?style=flat&logo=nordicsemiconductor&logoColor=white)
![DMA](https://img.shields.io/badge/DMA-777777?style=flat)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=flat&logo=mathworks&logoColor=white)
![Isaac Lab](https://img.shields.io/badge/Isaac_Lab-76B900?style=flat&logo=nvidia&logoColor=white)
![Autodesk APS](https://img.shields.io/badge/Autodesk_APS-0696D7?style=flat&logo=autodesk&logoColor=white)
![IFC4 BIM](https://img.shields.io/badge/IFC4_BIM-1F5582?style=flat)

---

### Open Source — 16 Merged Pull Requests

#### [pytorch/pytorch](https://github.com/pytorch/pytorch) — the framework everything else is built on

- **[PR #191866](https://github.com/pytorch/pytorch/pull/191866)** — landed on `main` as [`e9cfafa`](https://github.com/pytorch/pytorch/commit/e9cfafa), reviewed and approved by **@jansel (TorchInductor lead)**. *(PyTorch merges via `pytorchmergebot`, which closes the PR once the commit lands — the commit link is the canonical record.)* Converted three bare expressions in the compiler runtime that *looked* useless but carried side effects into explicit `_ = expr` bindings, and removed the genuinely dead statements in `torch/fx/experimental/unification`. The bare statements turned out to be a historical trick for suppressing F811 warnings; replaced with explicit `# noqa: F811` after establishing via minimal repro that **ruff exempts underscore-prefixed names from F811 — undocumented behavior** that explained why only the public names needed suppression. Unable to build torch locally, I proved runtime equivalence by importing the pre- and post-change packages side by side and diffing **18 dimensions**: per-function behavior, exception types and messages, and the full dispatch registry.
  - **Unblocking the merge:** landing was blocked by a ROCm/gfx950 CI failure. I diagnosed it as `hipErrorIllegalState` (HIP 401) thrown from `hipModuleLaunchKernel` and proved it independent of my change with **four reproducible lines of evidence** — bytecode comparison, config-gating analysis (the relevant flags appear **0 times** in the failure logs), the module never being imported, and elimination of cache bypass — and recommended the maintainer use `@pytorchbot merge -i`. The PR landed.
- **[PR #192123](https://github.com/pytorch/pytorch/pull/192123)** — landed on `main` as [`b78a4fe7`](https://github.com/pytorch/pytorch/commit/b78a4fe7): `[inductor] Drop the dead frame walk in _find_names`. Removed a stack-walk in inductor's bandwidth profiler that materialized every frame's `f_locals` so `gc.get_referrers()` could see them. The walk only ever surfaced noise (`obj`, `self`); its real harm was the AOTI lazy-compile path, where the intended fallback to `inductor_meta["kernel_name"]` became unreachable and kernels were labeled `"self"`. Dead on Python 3.13+ since PEP 667 (`f_locals` now returns a non-dict `FrameLocalsProxy`); harmful on ≤3.12 — so the change aligns 3.10–3.12 with the already-correct 3.13/3.14 behavior, stated plainly as a behavior change rather than dressed up as cleanup.
  - **Answering what the maintainer's bot couldn't:** @jansel asked whether the walk was working around a historical GC bug and set his bot on the archaeology; its 20-commit shallow clone came up empty. From the full repo I traced the chain — introduced 2023-02 ([#95355](https://github.com/pytorch/pytorch/pull/95355), starting from `f_back`, so `obj` could never leak), then broken 2023-10 by a flake8-bugbear B020 lint refactor ([#110823](https://github.com/pytorch/pytorch/pull/110823)) that moved the start frame to `currentframe()`. The defect was a lint-cleanup regression all along.
  - **Tests that never existed:** added regression coverage for three-year-old behavior, including `test_unbound_kernel_falls_back_to_inductor_meta_name` — returns `"self"` on the old code under 3.12, falls back correctly after the fix. One subtle detail: the probe must be a custom class instance, because `object()` isn't gc-tracked and the test would pass on 3.14 while failing on 3.12/3.13. Unable to build torch locally, I verified the patched function against the real call shape across **Python 3.12 / 3.13 / 3.14 via `uvx`** and posted all three results in the PR.
  - **A public self-correction:** my first fix went the opposite direction — restoring the walk on 3.13+. Verifying against the real call shape showed that would spread the `"self"` bug to newer versions; I force-pushed the reversal and documented why on the PR before any reviewer raised it.

#### [anthropics/claude-code-action](https://github.com/anthropics/claude-code-action) (8.4k★) — Anthropic's official GitHub Action

- **[PR #1488](https://github.com/anthropics/claude-code-action/pull/1488) (merged):** Closed a gap in the content sanitizer, which stripped injected instructions from inline images `![alt](url)` but not reference-style images `![alt][ref]`. Added regression tests (771 passing); reviewed and merged into `main` by an Anthropic engineer.

#### [langchain-ai/langchain-aws](https://github.com/langchain-ai/langchain-aws) — AWS/Bedrock integrations for LangChain

- **[PR #1085](https://github.com/langchain-ai/langchain-aws/pull/1085) (merged):** Repo-wide static analysis caught `ensure_ascii=True` defaults in `json.dumps` across Bedrock converters, tool-schema serializers, and stream parsers — silently escaping CJK/emoji to `\uXXXX` and inflating prompt token cost ~6×. Fixed across 11 sites in 3 modules.

#### [vllm-project/vllm](https://github.com/vllm-project/vllm) (~85k★) — the core LLM inference engine

- **[PR #45466](https://github.com/vllm-project/vllm/pull/45466) (merged):** CUDA kernel correctness fix. Root-caused a `CUDA error: misaligned address` crash (surfacing via FlexAttention with `head_size=46`) that had been misattributed across the issue thread to FlexAttention, CUDA graphs, and GPU drivers. Real cause: the shared `vectorize_with_alignment` helper only checked the *input* pointer's alignment — but in `reshape_and_cache_flash` the destination KV-cache row isn't 16-byte-aligned for head sizes not a multiple of 8, so the kernel's 16-byte vectorized stores faulted. Added an output-pointer alignment check + scalar fallback, eliminating the unguarded-store hazard for every caller (incl. fp8/int8 quant kernels), Linux behavior byte-for-byte unchanged. Added a GPU regression test (`head_size=46`); merged into main by a core committer.
- **[PR #45352](https://github.com/vllm-project/vllm/pull/45352) (merged):** Speculative-decoding correctness fix. Root-caused a recurring CI OOM to a silent config-propagation bug: the draft-model config hardcoded its own `hf_overrides`, silently dropping the target model's — so test-shrinking overrides never reached the Eagle draft, which instantiated at full 675B-scale dimensions. Fixed by composing the target's callable override with the draft's; also resolved a multiprocessing-pickling failure the composition introduced (nested closure → `functools.partial` on a static method) since vLLM's engine core pickles configs across `spawn`. Added a picklability regression test; re-enabled a previously-excluded test path. Shepherded and merged by a core maintainer.

#### [sgl-project/sglang](https://github.com/sgl-project/sglang) (~29k★) — high-performance LLM/multimodal inference-serving framework

- **[PR #26971](https://github.com/sgl-project/sglang/pull/26971) (merged):** Fixed a batched multi-tenant cache-routing crash — `GenerateReqInput.extra_key` wasn't indexed per sub-request, so the whole list was passed to `RadixKey.child_key()`, crashing prefix-cache matching with `TypeError: unhashable type: 'list'`. Added `_normalize_extra_key()` (scalar broadcast / list-length validation / parallel-sample expansion) + a 6-path regression test; passed 121 CI checks.
- **[PR #25975](https://github.com/sgl-project/sglang/pull/25975) (merged, co-author):** Prefill-delayer monitoring-metric fix — `prefill_delayer_wait_*` histogram stuck at 0 because the release path read `next_state=None`; maintainer adopted the `prev_state` approach and credited me as co-author.

#### [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) (~216k★) — Nous Research's agent framework

- **[PR #64771](https://github.com/NousResearch/hermes-agent/pull/64771) (merged):** cost-safe model routing — a bare-provider `/model` switch was silently routing to the priciest flagship model (a billing footgun that once escalated to a premium model and billed 863 requests before the user noticed); routed it through the cost-safe default instead, with regression tests. Merged into `main`.
- **[PR #61835](https://github.com/NousResearch/hermes-agent/pull/61835) (merged):** fixed a crash on null web/backend configuration and added regression tests; merged into `main`.

#### [BerriAI/litellm](https://github.com/BerriAI/litellm) (50k★) — LLM gateway/proxy unifying 100+ providers

- **[PR #29707](https://github.com/BerriAI/litellm/pull/29707) (merged):** Diagnosed a Vertex AI context-caching 404 on multi-region (eu/us) endpoints — the caching path hardcoded the single-region host instead of the multi-region REP host the inference path already used — and contributed the merged parametrized regression suite locking the corrected host-resolution invariant. 49 green CI checks.

#### [vllm-project/llm-compressor](https://github.com/vllm-project/llm-compressor) — vLLM's model-quantization toolkit

- **[PR #2797 and #2802](https://github.com/vllm-project/llm-compressor/pull/2797) (merged):** Added IBM Granite (`GraniteForCausalLM`) to the AWQ and SmoothQuant quantization mapping registries, with meta-device tests that instantiate the model skeleton and validate mapping regexes against the real module tree. Also unblocked the merge itself by resolving a `test_utils.py` rebase conflict that the maintainers' automation couldn't.

#### [vllm-project/production-stack](https://github.com/vllm-project/production-stack) — official Kubernetes deployment stack for vLLM

- **[PR #969](https://github.com/vllm-project/production-stack/pull/969) (merged):** Router bug fix — `route_sleep_wakeup_request` consumed only the router-internal `id` query param and silently dropped the rest, so `POST /sleep?id=X&level=2` degraded to `level=1`. Fixed by forwarding all non-`id` query params to every upstream call.
- **[PR #976](https://github.com/vllm-project/production-stack/pull/976) / [PR #970](https://github.com/vllm-project/production-stack/pull/970) (merged):** Cross-platform macOS support for the cluster install tooling — `uname`-based OS/arch detection, `sysctl -n hw.memsize` for Darwin memory sizing, Linux-only calls gated behind OS checks.

---

### Featured Projects

| Project | Description | Stack |
| --- | --- | --- |
| [**RepoAgentBench**](https://github.com/HumphreySun98/repoagentbench) | Open-source CLI that mines merged GitHub PRs into reproducible, **contamination-free** coding-agent benchmarks — public benchmarks overestimate agent capability by 20–50% through training-data contamination. Surfaced what leaderboards can't: the same model produced *opposite* outcomes on an identical task under two different agent harnesses. | Python, PyPI, GitHub API |
| [**SafetyCommander**](https://github.com/HumphreySun98/safety-commander-agent) *(Zapdos Labs × Antler hackathon)* | Factory-safety agent where a VLM judges risk **by reading the written safety policy and citing the controlling clause** — risk is decided in exactly one auditable module; edit one line of policy and the verdict flips. 📝 [Architecture write-up](https://dev.to/humphreysun98/safetycommander-an-ai-safety-officer-where-the-model-reasons-and-the-code-never-decides-4765) | Qwen3-VL, vLLM, YOLO, RAG |
| [**Archiagents**](https://archiagents.com/) | Live AI product for architectural design (2-person team): briefs + CAD/IFC in → design schemes, photorealistic renders, IFC4 BIM models out. Competed in an OpenAI hackathon. | Vercel AI SDK, gpt-image-1, Autodesk APS |
| [**LLM API Gateway**](https://api.manxuezhida.com) | Production multi-provider LLM proxy (Claude/GPT/Gemini) with load balancing and key management — powers my downstream products. | Node.js, Express, VPS |
| [**SmartStudy Agent**](https://github.com/HumphreySun98/Smart-Study-Agent) *([Chrome Web Store](https://chromewebstore.google.com/detail/edbjkpfjonahanfkamlcbobmnplihmik))* | Closed-loop learning agent with a 4-policy benchmark — honestly reported that a rule-based heuristic (+35%) beat Q-learning (+18%) short-horizon, so the heuristic shipped. | Python, Claude API, Chrome MV3 |
| [**NeuroUnfold**](https://github.com/HumphreySun98/physical-informed-Deep-Learning-for-wireless-sensing) | Physics-informed DL recovering 406 kHz LoRa chirps from **5.3× aliased** BLE RSSI at **0.986 R²** — a signal classical sampling theory says is unrecoverable. | PyTorch, NumPy |
| [**77 kHz BLE Firmware**](https://github.com/HumphreySun98/High-speed-BLE-RSSI-sampling-rate) | Custom Zephyr RTOS firmware on nRF54L15 — **3× the highest published sampling rate**, <0.01% drop. | C, Zephyr RTOS, DMA |
| [**Dual-Stream Gesture Transformer**](https://github.com/HumphreySun98/dual-stream-gesture-transformer) | Real-time gesture recognition at **557 FPS** (1.79 ms), 88.2% accuracy from 35 labeled samples via sim-to-real. | PyTorch, MediaPipe |

---

### Research & Service

- **First author** — *When Memory Updates but Behavior Does Not: Repairing Implicit Stale Dependencies in Personalized Agent Responses* · [arXiv:2608.01619](https://arxiv.org/abs/2608.01619) 
- **Robotic manipulation RL** — sim-to-real on Franka & xArm, contact-rich policies in Isaac Lab
- **Peer Reviewer** — AgentSkills Workshop @ ACM CAIS 2026 · *IEEE Wireless Communications Letters*
- **Member** — AAAI · IEEE-HKN &nbsp;|&nbsp; 
- 2 Chinese patents · Provincial 2nd Prize, China Undergraduate Mathematical Contest in Modeling

---

### A Year in Commits

<picture>
  <img src="https://raw.githubusercontent.com/HumphreySun98/HumphreySun98/main/profile-3d-contrib/manhattan-night.svg" width="100%"/>
</picture>
