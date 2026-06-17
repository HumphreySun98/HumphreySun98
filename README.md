# Hi, I'm Haofei Sun

*AI Agents & LLM Infrastructure · Deep Learning for Wireless Sensing · Embedded Systems*

**Open to full-time SWE / AI Engineer / ML Engineer roles — graduating Dec 2026.**


[![LinkedIn](https://img.shields.io/badge/LinkedIn-haofei--sun-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/haofei-sun)
[![Email](https://img.shields.io/badge/Email-humphreysun98@gmail.com-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:humphreysun98@gmail.com)
[![SmartStudy on Chrome Web Store](https://img.shields.io/badge/Chrome_Web_Store-SmartStudy_Live-4285F4?style=flat&logo=googlechrome&logoColor=white)](https://chromewebstore.google.com/detail/edbjkpfjonahanfkamlcbobmnplihmik)
[![Archiagents Live](https://img.shields.io/badge/Archiagents-Live-FF6B35?style=flat)](https://archiagents.com)
[![LLM API Gateway](https://img.shields.io/badge/LLM_API_Gateway-api.manxuezhida.com-2496ED?style=flat)](https://api.manxuezhida.com)
[![SGLang PRs Merged](https://img.shields.io/badge/SGLang-2_PRs_Merged-EE4C2C?style=flat)](https://github.com/sgl-project/sglang/pull/26971)
[![vLLM production-stack Merged](https://img.shields.io/badge/vLLM_production--stack-PR_Merged-30A14E?style=flat)](https://github.com/vllm-project/production-stack/pull/976)
[![LiteLLM PR Merged](https://img.shields.io/badge/LiteLLM-PR_%2329707_Merged-00B8D9?style=flat)](https://github.com/BerriAI/litellm/pull/29707)
[![LangChain PR Merged](https://img.shields.io/badge/LangChain-PR_%231085_Merged-1C3C3C?style=flat)](https://github.com/langchain-ai/langchain-aws/pull/1085)

---

### About Me

Engineer who connects hardware signals to intelligent software, and who ships systems honestly — including when the simple baseline wins. Recently I've contributed merged fixes to several leading LLM-infrastructure projects (SGLang, LiteLLM, LangChain), built embedded RTOS firmware sampling RF at **77 kHz** (3x prior published rates), trained deep-learning models that **recover signals lost to aliasing** with **0.986 R2** on chirp recovery, and shipped full-stack LLM agents live on the Chrome Web Store and in production.

- **Contributed to leading LLM-infrastructure ecosystems** — merged PRs into **SGLang** (~29k★ serving framework), **vLLM** (production-stack deployment), **LiteLLM** (50k★ gateway), and **LangChain**, spanning multi-tenant batching, multi-region routing, prompt-encoding, and cross-platform deployment (details below)
- Built a **physics-informed neural network** on NVIDIA B200 reconstructing aliased RF signals with **0.986 R2** on chirp recovery
- Custom **Zephyr RTOS firmware** on nRF54L15 hitting **77 kHz BLE RSSI** sampling with <0.01% drop rate
- Shipped **Archiagents** (https://archiagents.com/) — an end-to-end AI agent for architectural design that takes project briefs through to IFC4 BIM models and photorealistic renders. Owned engineering implementation and VPS deployment (2-person team)
- Deployed a **Claude-powered learning agent** live on **Chrome Web Store** + HuggingFace, with a 4-policy benchmark and an honestly-reported finding that a rule-based heuristic outperformed Q-learning on short-horizon tasks
- Shipped **RepoAgentBench**, an open-source toolkit that mines merged PRs into reproducible coding-agent benchmarks; tested 4 frontier LLMs across claude-code and aider with real API spend
- Running a **production LLM API gateway** (https://api.manxuezhida.com) with multi-provider routing, load balancing, and key management — serves my downstream products
- **Summer 2026** intern at Halo Microelectronics — full-stack AI agent system for analog IC design (RAG + agent orchestration)

Interests: LLM serving infrastructure, edge AI, wireless sensing, LLM agents, signal processing, sim-to-real for robotics.

---

### Open Source — LLM Infrastructure Contributions

#### [sgl-project/sglang](https://github.com/sgl-project/sglang) (~29k★) — high-performance LLM/multimodal inference-serving framework

- **[PR #26971](https://github.com/sgl-project/sglang/pull/26971) (merged):** Fixed a batched multi-tenant cache-routing crash — `GenerateReqInput.extra_key` wasn't indexed per sub-request, so the whole list was passed to `RadixKey.child_key()`, crashing prefix-cache matching with `TypeError: unhashable type: 'list'`. Added `_normalize_extra_key()` (scalar broadcast / list-length validation / parallel-sample expansion) + a 6-path regression test; passed 121 CI checks.
- **[PR #25975](https://github.com/sgl-project/sglang/pull/25975) (merged, co-author):** Prefill-delayer monitoring-metric fix — `prefill_delayer_wait_*` histogram stuck at 0 because the release path read `next_state=None`; maintainer adopted the `prev_state` approach and credited me as co-author.

#### [BerriAI/litellm](https://github.com/BerriAI/litellm) (50k★) — LLM gateway/proxy unifying 100+ providers

- **[PR #29707](https://github.com/BerriAI/litellm/pull/29707) (merged):** Diagnosed a Vertex AI context-caching 404 on multi-region (eu/us) endpoints — the caching path hardcoded the single-region host instead of the multi-region REP host the inference path already used — and contributed the merged parametrized regression suite locking the corrected host-resolution invariant. 49 green CI checks.

#### [vllm-project/production-stack](https://github.com/vllm-project/production-stack) — official Kubernetes deployment stack for vLLM

- **[PR #976](https://github.com/vllm-project/production-stack/pull/976) (merged):** Added macOS support to the cluster install tooling via `uname`-based OS/arch detection (linux/darwin × amd64/arm64), so the kubectl install script fetches the matching release instead of assuming Linux. (Companion PR #970 extends the same cross-platform support to the minikube cluster script — approved, pending final merge.)

#### [langchain-ai/langchain-aws](https://github.com/langchain-ai/langchain-aws) — AWS/Bedrock integrations for LangChain

- **[PR #1085](https://github.com/langchain-ai/langchain-aws/pull/1085) (merged):** Repo-wide static analysis caught `ensure_ascii=True` defaults in `json.dumps` across Bedrock converters, tool-schema serializers, and stream parsers — silently escaping CJK/emoji to `\uXXXX` and inflating prompt token cost ~6x. Fixed across 11 sites in 3 modules.

#### [RepoAgentBench](https://github.com/HumphreySun98/repoagentbench)

- My open-source CLI on PyPI for reproducible, contamination-free coding-agent benchmarks.

---

### Tech Stack

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=flat&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat&logo=cplusplus&logoColor=white)
![Verilog](https://img.shields.io/badge/Verilog-B22222?style=flat)
![CUDA](https://img.shields.io/badge/CUDA-76B900?style=flat&logo=nvidia&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=mysql&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat&logo=gnubash&logoColor=white)

**AI / ML**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-D97757?style=flat&logo=anthropic&logoColor=white)
![GPT](https://img.shields.io/badge/GPT_API-412991?style=flat&logo=openai&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini_API-4285F4?style=flat&logo=google&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat)
![SGLang](https://img.shields.io/badge/SGLang-EE4C2C?style=flat)
![MCP](https://img.shields.io/badge/MCP-000000?style=flat)
![Vercel AI SDK](https://img.shields.io/badge/Vercel_AI_SDK-000000?style=flat&logo=vercel&logoColor=white)
![Transformers](https://img.shields.io/badge/Transformers-FFD21E?style=flat&logo=huggingface&logoColor=black)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)

**Backend & Web**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![shadcn/ui](https://img.shields.io/badge/shadcn/ui-000000?style=flat)
![Tailwind](https://img.shields.io/badge/Tailwind_v4-06B6D4?style=flat&logo=tailwindcss&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)

**Infrastructure**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![VPS](https://img.shields.io/badge/VPS_Deployment-0F4C5C?style=flat)
![OpenMP](https://img.shields.io/badge/OpenMP-0070D1?style=flat)
![MPI](https://img.shields.io/badge/MPI-003594?style=flat)

**Embedded & Hardware**

![Zephyr](https://img.shields.io/badge/Zephyr_RTOS-512BD4?style=flat)
![nRF](https://img.shields.io/badge/nRF54L15-00A9CE?style=flat&logo=nordicsemiconductor&logoColor=white)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=flat&logo=mathworks&logoColor=white)
![Isaac Lab](https://img.shields.io/badge/Isaac_Lab-76B900?style=flat&logo=nvidia&logoColor=white)
![Autodesk APS](https://img.shields.io/badge/Autodesk_APS-0696D7?style=flat&logo=autodesk&logoColor=white)
![IFC4 BIM](https://img.shields.io/badge/IFC4_BIM-1F5582?style=flat)

---

### Featured Projects

| Project | Description | Stack |
| --- | --- | --- |
| [**Archiagents** — https://archiagents.com/](https://archiagents.com/) | End-to-end AI agent for architectural design (2-person team). Ingests project briefs + CAD/DWG/IFC/Revit files, conducts requirement dialogue, generates design schemes, renders photorealistic visualizations (gpt-image-1), and outputs IFC4 BIM models with embedded Autodesk APS viewer. Multi-LLM backend (Claude / GPT / Gemini); deployed on custom domain via VPS. | Vercel AI SDK, shadcn/ui, gpt-image-1, Autodesk APS, IFC4 |
| [**LLM API Gateway** — https://api.manxuezhida.com](https://api.manxuezhida.com) | Production LLM API proxy serving multiple providers (Claude / GPT / Gemini) with load balancing, API key management, and request routing. Powers SmartStudy Agent, Archiagents, and other downstream products. Custom domain on VPS. | Node.js, Express, VPS |
| [**SmartStudy Agent**](https://github.com/HumphreySun98/Smart-Study-Agent) *([Web](https://huggingface.co/spaces/HumphreySun98/smart-study-agent) · [Chrome Extension](https://chromewebstore.google.com/detail/edbjkpfjonahanfkamlcbobmnplihmik))* | Closed-loop POMDP learning agent with 4-policy benchmark (Random / Rule-based / LinUCB Bandit / Q-learning) over 30 simulated students x 30 sessions. Honestly reported finding: rule-based heuristic +35% over random vs Q-learning +18% — RL is defensible but not dominant in short-horizon regime. Live on Chrome Web Store + HuggingFace; 8-page Streamlit UI; 3 pluggable LLM backends. | Python, Claude API, Streamlit, SQLite, Chrome MV3 |
| [**RepoAgentBench**](https://github.com/HumphreySun98/repoagentbench) | Open-source CLI that mines merged GitHub PRs into reproducible, contamination-free coding-agent benchmarks. Adapters for claude-code and aider; tested with 4 frontier LLMs (Opus 4.7 / GPT-5.5 / Sonnet 4.6 / Gemini 3.1 Pro) using real API spend. | Python, Click, PyPI, JSONL, GitHub API |
| [**NeuroUnfold**](https://github.com/HumphreySun98/physical-informed-Deep-Learning-for-wireless-sensing) | Physics-informed DL recovering 406 kHz LoRa chirps from 5.3x aliased BLE RSSI with **0.986 R2** on chirp recovery. Branch disambiguation enables BLE-only wireless sensing at 5 m. | Python, PyTorch, NumPy |
| [**High-Speed BLE RSSI Firmware**](https://github.com/HumphreySun98/High-speed-BLE-RSSI-sampling-rate) | Custom Zephyr RTOS firmware on nRF54L15 hitting **77 kHz** sampling (3x prior published), bypassing BLE protocol layer for raw energy detection. | C, Zephyr RTOS, DMA |
| [**Agentic Weather Assistant**](https://github.com/HumphreySun98/agentic-weather-assistant) | Full-stack agentic web app with 3-service architecture: React frontend + FastAPI backend (LangChain ReAct agent + LangGraph) + custom MCP microservice wrapping a public REST API. Pydantic-validated typed tool-calling across services. | React, FastAPI, LangChain, LangGraph, MCP |
| [**Dual-Stream Gesture Transformer**](https://github.com/HumphreySun98/dual-stream-gesture-transformer) | Real-time hand gesture recognition via a Dual-Stream Spatiotemporal Transformer on MediaPipe skeletons. **557 FPS GPU** (1.79 ms latency), 88.2% accuracy with 35 labeled samples via Sim-to-Real training. | Python, PyTorch, MediaPipe |
| [**Deep Learning for BLE Sensing**](https://github.com/HumphreySun98/Deep-Learning-for-BLE-Sensing) | End-to-end super-resolution pipeline recovering wideband LoRa channel responses from narrowband BLE RSSI via progressive sub-pixel convolution. | Python, PyTorch, C |

---

### Research & Publications

- **Robotic Manipulation RL — Sim-to-Real on Franka & xArm** *(paper in preparation)*: Contact-rich policy training in Isaac Lab with sim-to-real transfer to physical hardware.
- **Peer Reviewer**, *AgentSkills Workshop*, ACM CAIS 2026 (ACM Conference on AI and Agentic Systems)
- **Peer Reviewer**, *IEEE Wireless Communications Letters*
- **2 Chinese patents accepted** on mixed-signal circuit techniques
- **Provincial Second Prize**, China Undergraduate Mathematical Contest in Modeling
