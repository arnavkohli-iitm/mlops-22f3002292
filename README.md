# MLOps Week-10 Assignment: LLM Fine-Tuning with Vertex AI

This project expands on the MLOps pipeline by integrating **Generative AI** workflows. The core of this week's work involves fine-tuning the **Gemma 3** foundation model using Google Cloud Vertex AI to perform classification on the Iris dataset.

The primary work for this assignment is contained in the new `fine_tuning/` directory.

## 🧠 New Concepts & Tools

* **LLM Fine-Tuning (Vertex AI):** Utilized Vertex AI Model Garden to fine-tune a parameter-efficient version of Gemma 3.
* **Prompt Engineering & Data Formatting:** Converted tabular data into a chat-based JSONL format (`system`, `user`, `assistant` roles) to make it compatible with LLM training.
* **Comparative Analysis (Raw vs. Descriptive):** Trained two distinct model versions to test the LLM's reasoning capabilities:
    * **V1 (Raw):** Uses the original floating-point numbers (e.g., "Sepal Length: 5.1").
    * **V2 (Descriptive):** Uses discretized semantic descriptions (e.g., "Sepal Length is Low") to exploit the LLM's language understanding.

## 📂 Updated Project Structure

A new folder `fine_tuning/` has been added to isolate the GenAI workflow:

```text
├── fine_tuning/
│   ├── 01_data_preparation.ipynb     # Prepares V1 & V2 JSONL datasets for Vertex AI
│   ├── 02_inference_comparison.ipynb # Downloads models, runs local inference & evaluation
│   ├── requirements.txt              # Dependencies for the fine-tuning environment
│   └── ...
├── data/                             # Original Data directory
└── ... (other files)
```

## 🚀 Key Insights & Objectives

The `fine_tuning/` notebooks address the following objectives:

1.  **Data Transformation:** The `01_data_preparation.ipynb` notebook converts the `iris.csv` dataset into the specific `messages` format required by Gemma, creating separate training and testing sets for both experiments.
2.  **Fine-Tuning Workflow:** Successfully submitted and monitored two separate fine-tuning jobs on Vertex AI to adapt Gemma 3 for a classification task.
3.  **Model Evaluation:** The `02_inference_comparison.ipynb` notebook downloads the fine-tuned adapters and runs local inference using the `transformers` library.
      * *Goal:* Compare the Accuracy and F1-scores of the **Raw Numeric** model vs. the **Descriptive Text** model to determine which data representation the LLM handles better.
