# Hi, I'm Haofei Sun

*Embedded & Applied ML Engineer · Full-Stack Agent Developer · Signal Processing + Deep Learning*


[![LinkedIn](https://img.shields.io/badge/LinkedIn-haofei--sun-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/haofei-sun)
[![Email](https://img.shields.io/badge/Email-humphreysun98@gmail.com-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:humphreysun98@gmail.com)
[![SmartStudy on Chrome Web Store](https://img.shields.io/badge/Chrome_Web_Store-SmartStudy_Live-4285F4?style=flat&logo=googlechrome&logoColor=white)](https://chromewebstore.google.com/detail/edbjkpfjonahanfkamlcbobmnplihmik)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-Live_Demo-FFD21E?style=flat&logo=huggingface&logoColor=black)](https://huggingface.co/spaces/HumphreySun98/smart-study-agent)

---

### About Me

Engineer who connects hardware signals to intelligent software, and who ships systems honestly — including when the simple baseline wins. I've shipped embedded RTOS firmware sampling RF at **77 kHz** (3× prior published rates), deep-learning models that **recover signals lost to aliasing** at 98.6% accuracy, full-stack LLM agents live on the Chrome Web Store, and an open-source benchmarking toolkit for AI coding agents.

- Built a **physics-informed neural network** on NVIDIA B200 reconstructing aliased RF signals at **98.6% accuracy**
- Custom **Zephyr RTOS firmware** on nRF54L15 hitting **77 kHz BLE RSSI** sampling with <0.01% drop rate
- Deployed a **Claude-powered learning agent** live on **Chrome Web Store** + HuggingFace, with a 4-policy benchmark and an honestly-reported finding that a rule-based heuristic outperformed Q-learning on short-horizon tasks
- Shipped **RepoAgentBench**, an open-source toolkit that mines merged PRs into reproducible coding-agent benchmarks; tested 4 frontier LLMs across claude-code and aider with real API spend
- **Summer 2026** intern at Halo Microelectronics on AI-assisted analog IC design and verification flows

Interests: edge AI, wireless sensing, LLM agents, agent observability, signal processing, sim-to-real for robotics.

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
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat&logo=gnubash&logoColor=white)

**AI / ML**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-D97757?style=flat&logo=anthropic&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat)
![MCP](https://img.shields.io/badge/MCP-000000?style=flat)
![Transformers](https://img.shields.io/badge/Transformers-FFD21E?style=flat&logo=huggingface&logoColor=black)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)

**Backend & Web**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)

**Infrastructure**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![OpenMP](https://img.shields.io/badge/OpenMP-0070D1?style=flat)
![MPI](https://img.shields.io/badge/MPI-003594?style=flat)

**Embedded & Hardware**

![Zephyr](https://img.shields.io/badge/Zephyr_RTOS-512BD4?style=flat)
![nRF](https://img.shields.io/badge/nRF54L15-00A9CE?style=flat&logo=nordicsemiconductor&logoColor=white)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=flat&logo=mathworks&logoColor=white)
![Isaac Lab](https://img.shields.io/badge/Isaac_Lab-76B900?style=flat&logo=nvidia&logoColor=white)

---

### Featured Projects

| Project | Description | Stack |
| --- | --- | --- |
| [**SmartStudy Agent**](https://github.com/HumphreySun98/Smart-Study-Agent) *([Web](https://huggingface.co/spaces/HumphreySun98/smart-study-agent) · [Chrome Extension](https://chromewebstore.google.com/detail/edbjkpfjonahanfkamlcbobmnplihmik))* | Closed-loop POMDP learning agent with 4-policy benchmark (Random / Rule-based / LinUCB Bandit / Q-learning) over 30 simulated students × 30 sessions. Honestly reported finding: rule-based heuristic +35% over random vs Q-learning +18% — RL is defensible but not dominant in short-horizon regime. Live on Chrome Web Store + HuggingFace; 8-page Streamlit UI; 3 pluggable LLM backends. | Python, Claude API, Streamlit, SQLite, Chrome MV3 |
| [**RepoAgentBench**](https://github.com/HumphreySun98/repoagentbench) | Open-source CLI that mines merged GitHub PRs into reproducible, contamination-free coding-agent benchmarks. Adapters for claude-code and aider; tested with 4 frontier LLMs (Opus 4.7 / GPT-5.5 / Sonnet 4.6 / Gemini 3.1 Pro) using real API spend. Cites recent benchmark-contamination research (arxiv 2510.08996, 2512.10218). | Python, Click, PyPI, JSONL, GitHub API |
| [**NeuroUnfold**](https://github.com/HumphreySun98/physical-informed-Deep-Learning-for-wireless-sensing) | Physics-informed DL recovering 406 kHz LoRa chirps from 5.3× aliased BLE RSSI. Branch disambiguation enables BLE-only wireless sensing at 5 m. | Python, PyTorch, NumPy |
| [**High-Speed BLE RSSI Firmware**](https://github.com/HumphreySun98/High-speed-BLE-RSSI-sampling-rate) | Custom Zephyr RTOS firmware on nRF54L15 hitting **77 kHz** sampling (3× prior published), bypassing BLE protocol layer for raw energy detection. | C, Zephyr RTOS, DMA |
| [**Agentic Weather Assistant**](https://github.com/HumphreySun98/agentic-weather-assistant) | Full-stack agentic web app: LangChain ReAct agent + custom MCP microservice wrapping a public REST API. 4 Docker services with typed tool-calling. | React, FastAPI, LangChain, MCP, Docker |
| [**Dual-Stream Gesture Transformer**](https://github.com/HumphreySun98/dual-stream-gesture-transformer) | Real-time hand gesture recognition via a Dual-Stream Spatiotemporal Transformer on MediaPipe skeletons. **557 FPS** CPU, 88.2% with 35 labeled samples. | Python, PyTorch, MediaPipe |
| [**Deep Learning for BLE Sensing**](https://github.com/HumphreySun98/Deep-Learning-for-BLE-Sensing) | End-to-end super-resolution pipeline recovering wideband LoRa channel responses from narrowband BLE RSSI via progressive sub-pixel convolution. | Python, PyTorch, C |

---

### Research & Publications

- **Robotic Manipulation RL — Sim-to-Real on Franka & xArm** *(paper in preparation)*: Contact-rich policy training in Isaac Lab with sim-to-real transfer to physical hardware.
- **Peer Reviewer**, *IEEE Wireless Communications Letters*
- 2 Chinese patents accepted on mixed-signal circuit techniques
- First Prize, Ministry of Education Scientific Research Achievement

---

Open to **Dec 2026 / 2027 full-time roles** · F-1 OPT/CPT/STEM-OPT eligible · Based in DFW
