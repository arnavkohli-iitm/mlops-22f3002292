# MLOps Week-11 Assignment: LLM Governance & Guardrails

This project builds upon the fine-tuning work from Week 10 by focusing on **LLM Governance** and security. The core of this week's work involves evaluating the fine-tuned **Gemma 2** pipeline for vulnerabilities—specifically prompt injection and leakage—and implementing guardrails to safeguard the model.

The primary work for this assignment is contained in the notebook `MLOPS_GA11.ipynb`.

## 🛡️ New Concepts & Tools

  * **LLM Governance Evaluation:** Systematically tested the fine-tuned model against adversarial inputs to identify security risks.
  * **Adversarial Testing:**
      * **Prompt Injection:** Attempted to override system instructions to force the model to output unauthorized classes (e.g., "Rose").
      * **Prompt Leakage:** Attempted to trick the model into revealing its underlying system prompt and instructions.
  * **Guardrails Implementation:** Developed a pre-inference filtering layer using regex-based blacklists to detect and block malicious inputs before they reach the LLM.
  * **MLflow Tracing:** utilized `@mlflow.trace` to instrument the inference pipeline, allowing for detailed observation of input tokens, model responses, and guardrail intervention events.

## 📂 Project Structure

The work is consolidated in the following notebook:

```text
├── MLOPS_GA11.ipynb              # Main notebook for Governance & Guardrails
│   ├── Governance Evaluation     # Tests for Injection and Leakage
│   └── Guardrail Implementation  # Regex filtering and secure inference logic
├── local_gemma2_model/           # Directory containing the downloaded fine-tuned adapter
└── ... (other files)
```

## 🚀 Key Insights & Objectives

The `MLOPS_GA11.ipynb` notebook addresses the following objectives:

1.  **Vulnerability Assessment:**

      * Demonstrated that without protection, the fine-tuned model was susceptible to **Prompt Injection** (successfully outputting "Rose" instead of a valid Iris class) and **Prompt Leakage** (revealing internal classification instructions).

2.  **Guardrail Logic:**

      * Implemented a `apply_guardrails` function that scans user input for adversarial keywords (e.g., "ignore previous," "system prompt," "override").
      * Integrated this logic into a `protected_run` wrapper ensuring that unsafe prompts are rejected immediately with a `[REJECTED]` status.

3.  **Secure Inference Pipeline:**

      * Verified the efficacy of the guardrails by re-running the attack vectors.
      * **Result:** The pipeline successfully blocked both the injection and leakage attempts while maintaining correct functionality for standard classification requests.
