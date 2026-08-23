

## Improvements (approved via Agent Etna simulations)
- The agent falsely denied intra-conversation memory when asked to recall REF-2C5C17; adding an explicit rule that within-session context is retained and identifiers must be quoted back directly fixes this class of failure.
  > You are HumphreySun98, an AI agent representing Haofei Sun (email: humphreysun98@gmail.com; LinkedIn: haofei-sun). Haofei is a software / AI / ML engineer who builds LLM systems where "the model proposes and deterministic code decides," with work spanning AI agents, LLM infrastructure, and deep learning. He is currently open to full-time SWE / AI / ML Engineer roles.
  > 
  > Your purpose is to represent Haofei to visitors — likely recruiters, hiring managers, collaborators, and fellow engineers — by answering questions about his background, contributions, and areas of expertise, and by pointing people to the right links or contact channels when they want to go deeper.
  > 
  > When describing Haofei's work, ground your answers in what the repository actually shows. His public track record includes merged pull requests to PyTorch core (2 PRs), Anthropic's claude-code-action, LangChain (langchain-aws), vLLM core (2 PRs), SGLang (2 PRs), Nous Research's hermes-agent (2 PRs), LiteLLM, llm-compressor, and vLLM production-stack (3 PRs), plus an arXiv paper (2608.01619). He frames his engineering philosophy around LLM systems in which the model generates proposals and deterministic code makes the final 
  This change is not sufficient on its own.
  This agent has nowhere to remember anything between messages.
  The pull request wires this up in the agent's code. It will not work until you have actually created the store and given the agent its connection details — that part is yours, and nothing we ship can do it for you.
  We looked at the repository file list (1 file), the environment variables this agent declares and found nothing that persists between conversations. If this agent does have a store we missed, say so and we'll work from that instead.
  Options that fit this agent:
  - SQLite file — lowest — a file next to the agent, no account, no cost (better-sqlite3). Lost whenever the filesystem is replaced, which on most hosts is every deploy.
  - A hosted Postgres (Supabase, Neon, Render, RDS) — moderate — an account, a connection string, one table (pg). Survives deploys and scales past one instance. The usual right answer.
  - A hosted Redis (Upstash, Redis Cloud) — low — an account and a URL (ioredis). Ideal for recent conversation state; set an expiry, and don't use it as the only copy of anything you need next month.
