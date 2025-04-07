Design & Architecture Summary:
Objective:
Developed a modular GenAI blue teaming solution to secure LLM applications by detecting prompt injection attacks, output abuse, jailbreak attempts, and enforcing policy compliance in real-time.

System Architecture Components:
1. Prompt Capture Layer
Hooks into LLM API endpoints to log incoming prompts, user context, and source application metadata.

Adds UUID tagging for traceability and audit trails.

2. Threat Evaluation Engine
Combines LLM-based reasoning (GPT-4) with NLP-based static rules to classify inputs as:

Benign

Jailbreak

Prompt Injection

Non-compliant / Offensive

Uses vector embeddings (FAISS) to compare with known adversarial patterns.

3. Attack Simulation Module
Injects adversarial prompts (e.g., DAN, recursive jailbreaks) from a curated dataset.

Scores model responses for vulnerability benchmarking (precision, bypass success rate).

4. Drift & Behavior Monitor
Tracks token-level changes across time and users to detect:

Model drift

Anomalous user behavior (e.g., high-risk prompt frequency)

Alerts on deviations from normal output entropy or sentiment.

5. SIEM + SOAR Integration
Logs unsafe prompt data to Splunk or Azure Sentinel.

Supports alert correlation with EDR or firewall events.

Auto-generates incident tickets with impact summaries from LLM.

6. Visual Dashboard (Streamlit)
Displays real-time unsafe prompt activity, top attacking users, language risk heatmaps.

Graph-based views for jailbreak chain analysis.

🛠️ Tech Stack:
Python, GPT-4 API, FAISS, LangChain, Regex/NLP

Streamlit (dashboard), Docker (deployment), GitHub Actions (CI/CD)

Splunk/Sentinel REST API (integration), MongoDB (prompt logs)
