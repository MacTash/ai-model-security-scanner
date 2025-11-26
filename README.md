HF Model Security Scanner (v0.2.0)

A fast, open-source security scanner for Hugging Face models and datasets — built for red teams, ML security analysts, and governance professionals.

The scanner detects supply-chain threats, unsafe license usage, dataset compliance issues, and unsafe model file artifacts that may impact security, privacy, and commercial deployment of generative AI.

Objective: Help teams identify risks BEFORE integrating a model in production.

Key Features (NEW in v0.2.0)

| Capability                          | Description                                                                                            |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Dataset Security Scanner**        | Evaluates linked Hugging Face datasets for PII, minors/biometric risks, and redistribution constraints |
| **Advanced License Intelligence**   | First-class mapping for Gemma, Llama 3, Qwen 2, OpenRAIL variants, etc.                                |
| **Resolved License Prioritization** | Metadata licenses override HF API parsing to avoid false “No license detected” issues                  |
| **Improved Provenance Scoring**     | Uses downloads, likes, forks, and author trust score                                                   |
| **Correct Risk Classification**     | New severity thresholds: Low, Medium, High, Critical                                                   |
| **Model Card Requirements Check**   | Section-aware scanning for: intended use, risks, limitations                                           |
| **Supply Chain Risk Signals**       | Flags suspicious repos with low usage + executable model files                                         |
| **Enhanced Reporting**              | Dataset scoring now included in JSON & Text reports                                                    |

git clone https://github.com/MacTash/ai-model-security-scanner.git
cd ai-model-security-scanner

If installing for the first time:
pip install -e .

Run it:
hf-scan scan <model name>

If already installed and need to update to the newest version:
pip install --no-deps --force-reinstall -e .

For JSON report:
hf-scan scan <model_id> --json report.json


Risk Scoring

| Overall Score | Category | Meaning                             |
| ------------- | -------- | ----------------------------------- |
| 0.0 – 2.5     | Low      | Minimal security concerns           |
| 2.6 – 5.0     | Medium   | Requires manual review              |
| 5.1 – 7.5     | High     | Security and licensing blockers     |
| 7.6 – 10.0    | Critical | Stop: significant supply-chain risk |


Scores aggregate:

License compliance

Dataset privacy/security violations

Suspicious files & executable scripts in repo

Provenance trustworthiness

Vulnerability patterns

Security Checks Performed
1. License Compliance

Commercial use allowed?

Copyleft / redistribution required?

AI-specific usage restrictions?

Metadata vs. HF API mismatch detection

2. Dataset Safety

PII heuristics detection

GDPR/COPPA risk for minors

Biometric and healthcare sensitivity

Redistribution restrictions

3. Model File Safety

Malicious artifacts (scripts, shell files, binaries)

SafeTensors vs. dangerous formats

Code execution risks

4. Provenance Trust

Creator account age & reputation

Download history

Community validation signals

5. CVE & Vulnerabilities

Dependency risk flags

Unsafe import patterns

'''
OVERALL RISK: 3.10/10.0 — MEDIUM
Reason: License restrictions + minors dataset involvement
Recommendation: Review compliance guidelines before deployment
'''

Contributing

Pull requests are welcome. Please open an issue first to discuss major changes.

License

MIT License
(Scanner is permissively licensed — compatibility checks cover the scanned models, not the scanner itself.)

Maintainer

Developed by: Mayukh/Aka: Mac
Focused on AI Security, Safety & Governance










