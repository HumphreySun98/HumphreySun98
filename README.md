# Haofei Sun

**I build LLM systems where the model proposes and deterministic code decides.**

AI Agents · LLM Infrastructure · Embedded Sensing — M.S. CS @ UT Arlington, graduating Dec 2026. **Open to full-time SWE / AI / ML Engineer roles.**

[![arXiv](https://img.shields.io/badge/arXiv-2608.01619-B31B1B?style=for-the-badge&logo=arxiv&logoColor=white)](https://arxiv.org/abs/2608.01619)
[![PyTorch](https://img.shields.io/badge/PyTorch_core-contributor-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://github.com/pytorch/pytorch/commit/e9cfafa)
[![Anthropic](https://img.shields.io/badge/Anthropic-contributor-D97757?style=for-the-badge&logo=anthropic&logoColor=white)](https://github.com/anthropics/claude-code-action/pull/1488)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-haofei--sun-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/haofei-sun)
[![Email](https://img.shields.io/badge/Email-contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:humphreysun98@gmail.com)

---

### Proof of Work

**14 merged pull requests** across the ML stack — [PyTorch](https://github.com/pytorch/pytorch/commit/e9cfafa) · [Anthropic](https://github.com/anthropics/claude-code-action/pull/1488) · [LangChain](https://github.com/langchain-ai/langchain-aws/pull/1085) · [vLLM](https://github.com/vllm-project/vllm/pull/45466) · [SGLang](https://github.com/sgl-project/sglang/pull/26971) · [Nous Research](https://github.com/NousResearch/hermes-agent/pull/64771) · [LiteLLM](https://github.com/BerriAI/litellm/pull/29707) — plus a first-author paper, an agent that designs real circuits, and products live in production.

|  | The fact | Why it's hard |
| --- | --- | --- |
| 🔥 | **Merged into PyTorch core**, reviewed by the **TorchInductor lead** ([`e9cfafa`](https://github.com/pytorch/pytorch/commit/e9cfafa)) | Couldn't build torch locally — proved runtime equivalence by diffing both versions across **18 behavioral dimensions**; then **unblocked my own merge** by proving an unrelated ROCm CI failure independent with four reproducible lines of evidence |
| 📄 | **First-author paper** — [arXiv:2608.01619](https://arxiv.org/abs/2608.01619), AAAI 2027 submission | Showed agents act on facts they *already know* are stale (recall collapses 0.44–1.0 → **0.06–0.38** open-ended, worse under CoT); fixed it with LLM-proposed / code-verified repairs: **+5.0 pts**, reproduced by a disjoint judge |
| ⚡ | **An agent loop that designs real analog circuits** (Summer 2026, Halo Microelectronics) | No numeric optimizer — LLM proposes experiment batches, a simulator holds authority over truth: **4 rounds, ~100× error reduction, 42 evaluations, 5 LLM calls, ~7 minutes**, beating the accuracy floor in the company's own codebase |
| 🔬 | **CUDA kernel correctness fix in vLLM core** (~85k★) ([#45466](https://github.com/vllm-project/vllm/pull/45466)) | The issue thread blamed FlexAttention, CUDA graphs, and drivers — the real cause was an unchecked destination-pointer alignment in the KV-cache write path; fixed for every caller |
| 📡 | **77 kHz BLE RSSI firmware** (Zephyr RTOS, nRF54L15) → **0.986 R²** recovering signals **5.3× below Nyquist** | 3× the highest published sampling rate, feeding a physics-informed network that recovers what classical sampling theory says is unrecoverable |
| 🚢 | **Shipped and live:** [archiagents.com](https://archiagents.com) · [Chrome Web Store](https://chromewebstore.google.com/detail/edbjkpfjonahanfkamlcbobmnplihmik) · [LLM gateway](https://api.manxuezhida.com) | Real users, real uptime, real billing — including the honestly-reported finding that a rule-based heuristic beat Q-learning, so the heuristic shipped |

<details>
<summary><b>For recruiters · researchers · founders — 10-second version</b></summary>

- **Recruiters:** 14 merged PRs across PyTorch / Anthropic / LangChain / vLLM / SGLang · shipped products · Dec 2026 grad seeking SWE/AI/ML roles.
- **Researchers:** first-author AAAI 2027 submission on agent memory verification · contamination-free agent benchmarking · two ICRA 2027 manuscripts in preparation · AAAI & IEEE-HKN member.
- **Founders:** I build end to end and ship — agent systems with real verifiers, a live AI product, and a production LLM gateway serving my own downstream apps.

</details>

---

### Tech Stack

**Core:** Python · C/C++ · CUDA · TypeScript · SQL
**ML systems:** PyTorch · vLLM · SGLang · quantization (AWQ/SmoothQuant) · speculative decoding · GPU profiling
**Agents:** LangChain/LangGraph · MCP · RAG · Claude/GPT/Gemini APIs · evaluation harnesses
**Systems:** Docker · Kubernetes · Linux · OpenMP/MPI · AWS/GCP · React/FastAPI/Node.js
**Embedded:** Zephyr RTOS · nRF54L15 · DMA · MATLAB

---

### Open Source — 14 Merged Pull Requests

#### [pytorch/pytorch](https://github.com/pytorch/pytorch) — the framework everything else is built on

- **[PR #191866](https://github.com/pytorch/pytorch/pull/191866)** — landed on `main` as [`e9cfafa`](https://github.com/pytorch/pytorch/commit/e9cfafa), reviewed and approved by **@jansel (TorchInductor lead)**. *(PyTorch merges via `pytorchmergebot`, which closes the PR once the commit lands — the commit link is the canonical record.)* Converted three bare expressions in the compiler runtime that *looked* useless but carried side effects into explicit `_ = expr` bindings, and removed the genuinely dead statements in `torch/fx/experimental/unification`. The bare statements turned out to be a historical trick for suppressing F811 warnings; replaced with explicit `# noqa: F811` after establishing via minimal repro that **ruff exempts underscore-prefixed names from F811 — undocumented behavior** that explained why only the public names needed suppression. Unable to build torch locally, I proved runtime equivalence by importing the pre- and post-change packages side by side and diffing **18 dimensions**: per-function behavior, exception types and messages, and the full dispatch registry.
  - **Unblocking the merge:** landing was blocked by a ROCm/gfx950 CI failure. I diagnosed it as `hipErrorIllegalState` (HIP 401) thrown from `hipModuleLaunchKernel` and proved it independent of my change with **four reproducible lines of evidence** — bytecode comparison, config-gating analysis (the relevant flags appear **0 times** in the failure logs), the module never being imported, and elimination of cache bypass — and recommended the maintainer use `@pytorchbot merge -i`. The PR landed.

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

- **[PR #2797](https://github.com/vllm-project/llm-compressor/pull/2797) (merged):** Added IBM Granite (`GraniteForCausalLM`) to the AWQ and SmoothQuant quantization mapping registries, with meta-device tests that instantiate the model skeleton and validate mapping regexes against the real module tree. Also unblocked the merge itself by resolving a `test_utils.py` rebase conflict that the maintainers' automation couldn't.

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

- **First author** — *When Memory Updates but Behavior Does Not: Repairing Implicit Stale Dependencies in Personalized Agent Responses* · [arXiv:2608.01619](https://arxiv.org/abs/2608.01619) · under submission, AAAI 2027
- Two additional first-author-track manuscripts in preparation, targeting **ICRA 2027**
- **Robotic manipulation RL** — sim-to-real on Franka & xArm (Texas Tech collaboration), contact-rich policies in Isaac Lab
- **Peer Reviewer** — AgentSkills Workshop @ ACM CAIS 2026 · *IEEE Wireless Communications Letters*
- **Member** — AAAI · IEEE-HKN &nbsp;|&nbsp; **TA of the Month** — UT Arlington CSE
- 2 Chinese patents (filed) · Provincial 2nd Prize, China Undergraduate Mathematical Contest in Modeling

---

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=HumphreySun98&show_icons=true&theme=default&hide_border=true&count_private=true" alt="GitHub stats" height="160"/>
</p>
