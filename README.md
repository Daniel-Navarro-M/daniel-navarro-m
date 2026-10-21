<p align="center">
  <img src="assets/banner.svg" width="100%" alt="Daniel Navarro Madriñán, Data Scientist and AI Engineer in Geneva. Pixel-art agents wave hello in four languages.">
</p>

<p align="center">
  <a href="https://danielnavarro.work/"><img src="https://img.shields.io/badge/Portfolio-danielnavarro.work-a371f7?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Portfolio"></a>
  <a href="https://danielnavarro.work/cv/"><img src="https://img.shields.io/badge/CV-read-2f81f7?style=for-the-badge&logo=readthedocs&logoColor=white" alt="CV"></a>
  <a href="https://www.linkedin.com/in/daniel-navarro-madrinan/"><img src="https://img.shields.io/badge/LinkedIn-connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
</p>

I build **agentic systems that can show their work**: multi-agent workflows, the harnesses they run in, the retrieval that grounds them and the evals that prove they got better. Before agents, it was RAG, knowledge graphs, data pipelines and BI, and quantitative policy methods to test whether things actually work. That habit stayed.

## Now

- **Agent orchestration and harness engineering.** I design and deploy agent harnesses (Claude Code, OpenCode, plain chat and image) with sandboxes, tool allowlists, approval gates and per-agent model tuning, and grade every step with LLM judges.
- **UN OCHA, Geneva.** AI situation analysis and grounded report generation for humanitarian crises, used in the 2026 earthquake responses in the Philippines, Venezuela and Colombia.
- **Instrumental Partners.** Knowledge graphs, document AI, pricing models and BI for US manufacturing and defense-supply clients.

## Featured: Agent Fleet

<p align="center">
  <img src="assets/agent-fleet.svg" width="100%" alt="Agent Fleet architecture: an orchestrator plans a goal, departments of agents run it in sandboxed harnesses, a cross-family judge grades each step, and a Postgres plus pgvector knowledge graph feeds context back in.">
</p>

A software company where every employee is an LLM agent with its own model, harness, skills and knowledge. You give the orchestrator a goal and a pixel-art office shows the team plan it, walk to their desks and work through it. Results land in a folder per goal, per agent. The repo is private for now.

<table>
<tr>
<td width="50%" valign="top">

**Orchestration**

- Orchestrator plans steps as strict JSON; a planner can only reorder them
- Failures go retry, then escalate (depth 3), then fallback model, then replan (max 2), then "needs you"
- Several workflows run at once and build on each other's results
- Auto-resume after restarts, capped so a crash can't loop

**Harnesses and tuning**

- Four harnesses per agent: chat, Claude CLI, OpenCode, image (ComfyUI)
- Per-agent effort, max tokens, temperature, top-p and raw params, mapped to what each harness supports
- Prompt engineering by config: instructions file, skills and MCP tools per agent
- Skills with progressive disclosure: full text under 12k chars, else one-liners plus the 3 best matches

</td>
<td width="50%" valign="top">

**Evaluation**

- Every step graded: deterministic metrics, a rubric per task type and a trajectory score
- Judge comes from another model family than the producer, to avoid self-preference
- A tuning agent changes one thing per agent per day and keeps it only if the next 5 scores beat the last 5
- Calibration plan with Cohen's kappa against human grades

**Security and guardrails**

- Agents run as uid 1000 with a minimal env, write only to `/workspace`, no Docker socket
- API refuses agent processes, foreign origins and DNS rebinding; symlinks resolved with realpath
- Secrets filled at call time, one key per harness, never written to the workspace

**Retrieval and context budget**

- Knowledge graph on Postgres + pgvector with a typed ontology of nodes and edges
- Hybrid recall: binary HNSW + exact rescoring fused with full text (RRF), plus graph hops
- Token control: char budgets, compaction at 40% of the window, near-duplicate pruning, a GPU lane that batches jobs by loaded model

</td>
</tr>
</table>

## Case studies

<details open>
<summary><b>AI and data engineering</b></summary>

- [OCHA-RAG: earthquake responses and the reporting module](https://danielnavarro.work/work/ocha-rag/)
- [Company intelligence with a knowledge graph and RAG](https://danielnavarro.work/work/knowledge-graph-company-intelligence/)
- [AI review of quality clauses in purchase orders](https://danielnavarro.work/work/purchase-order-clause-reviewer/) (about $0.02 per order)
- [Machine learning for bid pricing on defense contracts](https://danielnavarro.work/work/bid-price-prediction/)
- [Procurement intelligence with RAG and ML](https://danielnavarro.work/work/procurement-intelligence/)
- [From ERP to dashboards for a manufacturer](https://danielnavarro.work/work/erp-manufacturing-dashboards/)
- [US aviation repair station market map](https://danielnavarro.work/work/aviation-repair-station-market-map/)

</details>

<details>
<summary><b>Policy research and data science</b></summary>

- [Did Colombia's Total Peace policy reduce violence?](https://danielnavarro.work/work/paz-total-colombia/) (MA thesis) · [code](https://github.com/Daniel-Navarro-M/-I-m-Paz-Total_replication)
- [Parental investment and learning gaps in the Western Balkans](https://danielnavarro.work/work/world-bank-timss-balkans/) (World Bank) · [code](https://github.com/Daniel-Navarro-M/World_Bank_CEU)
- [Haitian migration discourse in the Dominican Republic, an NLP study](https://danielnavarro.work/work/dominican-migration-nlp/) · [code](https://github.com/Daniel-Navarro-M/dialectical_identity_in_RD)
- [Corruption risk in Rail Baltica procurement](https://danielnavarro.work/work/rail-baltica-corruption-risk/) · [code](https://github.com/Daniel-Navarro-M/rail_baltika_corruption_replication)
- [Blackpolis: mapping structural racism in Cali](https://danielnavarro.work/work/blackpolis-cali/) · [code](https://github.com/Daniel-Navarro-M/blackpolis_replication)
- [K-means clustering of Cali's metropolitan vote](https://danielnavarro.work/work/cali-electoral-clustering/)
- [Pesticides and Parkinson's disease: geospatial ML](https://danielnavarro.work/work/parkinsons-geospatial-ml/)

</details>

## Tech stack

<p align="center">
  <img src="assets/tech-stack.svg" width="100%" alt="Tech stack. Agents and LLMs: Claude, OpenAI API, Nemotron, Hugging Face, MCP, RAG, Neo4j. Languages: Python, SQL, R, Rust, Node.js. Data and ML: scikit-learn, XGBoost, pandas, MLflow, Plotly, Power BI, Preset, QGIS. Infra: Docker, AWS, Azure, FastAPI, PostgreSQL with pgvector, SQLite, MongoDB.">
</p>

## About

I work across the whole data lifecycle: scraping and APIs, ETL, databases, models, dashboards, and the report someone reads at the end. Most of my projects sit where data engineering meets AI, with an evidence trail behind every answer.

I hold an MA in Public Policy (quantitative policy analysis) from Central European University and a BA in Anthropology from Universidad Icesi. That mix is why I care about who uses a system and whether its numbers can be trusted.

I've worked with the World Bank, UN OCHA, the Organization of American States, the European Union and private-sector clients, in humanitarian response, public procurement, manufacturing, education and security.

**Publications.** Milanese, J. P. & Navarro, D. (2025). *Más allá de los límites municipales: análisis de la metropolización del comportamiento electoral en Cali utilizando K-Means Clustering.* **GEOgraphia**, Brazil. First prize, FLACSO Ecuador TechPolítica contest (2024).

**Languages.** Spanish (native) · English (C1) · Italian (B1) · French (A2)

<p align="center">
  <img src="assets/footer.svg" width="100%" alt="Pixel-art agents waving goodbye.">
</p>
