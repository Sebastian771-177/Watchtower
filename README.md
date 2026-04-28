# Watchtower
◈ Watchtower
Unified Threat Intelligence Platform

A unified dashboard combining Centinela OSINT and Sentinel into a single professional threat intelligence platform — from Spanish-language dark web monitoring to automated IOC triage, all in one place.


🔍 What It Does
Watchtower runs both threat intelligence modules in sequence and renders a unified analyst dashboard with a single command.
Module 1 — Centinela OSINT
Ingests Spanish-language threat feed posts from dark web forums, Telegram channels, and underground marketplaces. Uses Claude to extract structured threat intelligence including severity, MITRE ATT&CK TTPs, targeted sectors, IOCs, and analyst recommendations.
Module 2 — Sentinel IOC Triage
Accepts IP addresses, domains, file hashes, and phishing emails. Queries VirusTotal and AbuseIPDB, then uses Claude to synthesize results into a plain-English analyst verdict with recommended next steps.
Unified Dashboard
A single color-coded HTML dashboard displaying all findings across both modules, with session-level statistics — total indicators analyzed, critical and high severity counts, malicious verdict totals — and a full JSON report export.

🛠 Technologies

Python 3.10+
Anthropic Claude API (claude-opus-4-5) — threat feed analysis, IOC synthesis, phishing detection
VirusTotal API — multi-engine malware and reputation scanning (free tier)
AbuseIPDB API — IP abuse reputation and reporting (free tier)
Google Colab — interactive notebook environment with HTML rendering


🚀 Getting Started
Run in Google Colab (recommended)

Upload watchtower.py to Google Colab or paste cells manually
Click the 🔑 Secrets icon in the left sidebar
Add the following secrets:

Secret NameWhere to get itANTHROPIC_API_KEYconsole.anthropic.comVIRUSTOTAL_API_KEYvirustotal.com → Sign up → API KeyABUSEIPDB_API_KEYabuseipdb.com → Sign up → API Key

Toggle Notebook access ON for each secret
In Cell 9, set use_mock=False
Run all cells top to bottom


No API keys yet? Set use_mock=True in Cell 9 to run a full demo with simulated data — no setup required.

Run locally
bashpip install anthropic requests
export ANTHROPIC_API_KEY=sk-ant-...
export VIRUSTOTAL_API_KEY=your-key
export ABUSEIPDB_API_KEY=your-key
python watchtower.py

📊 Dashboard Output
The Watchtower dashboard renders two sections:
◈ Centinela — Spanish-Language Threat Intelligence

Severity-coded cards for each threat feed item
Raw post (Spanish) + English analyst summary
TTPs, targeted sectors, IOC pills, TLP classification

◈ Sentinel — IOC Triage & Analysis

Verdict badge (MALICIOUS / SUSPICIOUS / CLEAN) per indicator
VirusTotal engine count breakdown
AbuseIPDB abuse score, country, ISP, Tor detection
Key findings, recommended actions, MITRE TTPs

Session Summary Header

Total indicators analyzed
Critical / High severity counts
Malicious verdict count
Threat feeds processed vs IOCs triaged


📁 Project Structure
watchtower/
├── watchtower.py           # Main script (paste into Colab cells)
├── README.md               # This file
└── watchtower_report.json  # Generated after running — full session export

💡 Why I Built This
Centinela and Sentinel were built as standalone tools, each solving a specific problem. Watchtower unifies them into a single platform because real SOC workflows don't operate in silos — analysts need both threat feed intelligence and IOC triage in the same view.
The session-level statistics layer also reflects how SOC teams actually measure their work: not just individual verdicts, but aggregate threat posture over a monitoring period.

🔗 Full Portfolio
This is the third project in a cybersecurity AI portfolio built on the Anthropic Claude API:
ProjectDescriptionCentinela OSINTSpanish-language threat feed monitorSentinelIOC triage and analysis assistantWatchtowerUnified platform combining both tools

🔮 Roadmap

 AlienVault OTX integration for additional IOC enrichment
 Shodan lookup for IP infrastructure profiling
 STIX 2.1 export for SIEM ingestion
 Bulk IOC input from CSV
 Scheduled monitoring mode with alerting
 Web UI built with Streamlit or Gradio


👤 Author
Sebastian Guerrero
CompTIA Security+ | Google Cybersecurity Certificate
B.A. International Relations | Fluent in Spanish
Based in Miami, FL
GitHub · LinkedIn

⚠️ Disclaimer
This tool uses simulated threat feed data for demonstration purposes. No real dark web sources are accessed. This project is intended solely for educational and portfolio purposes.
