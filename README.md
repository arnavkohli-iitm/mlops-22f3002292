# MLOps Week-9 Assignment: Model Fairness & Explainability

This project expands on the previous MLOps pipeline by introducing concepts of **Bias, Fairness, and Explainability**. The core of this week's work involves analyzing the model's behavior using **SHAP** and **Fairlearn** to ensure transparency and detect potential biases.

The primary work for this assignment is contained in `explainability.ipynb`.

## 🛡️ New Concepts & Tools

* **Synthetic "Location" Attribute:** A new random feature (values `0` and `1`) was introduced to the Iris dataset to test the model's robustness against irrelevant features.
* **Fairlearn:** Used to audit the model for bias, treating "location" as a sensitive attribute to ensure predictions remain fair across different groups.
* **SHAP (SHapley Additive exPlanations):** Utilized to explain individual predictions and understand global feature importance, specifically analyzing why the model classifies certain samples as *Virginica*.

## 📂 Updated Project Structure

The project structure remains largely the same, with the addition of the analysis notebook:

```text
├── explainability.ipynb  # New: Contains Fairlearn and SHAP analysis
├── data/                 # Data directory
├── train.py              # Existing training script
└── ... (other files)
````

## 🚀 Key Insights & Objectives

The `explainability.ipynb` notebook addresses the following objectives:

1.  **Fairness Analysis:** Incorporates a `MetricFrame` from Fairlearn to compare metrics (Accuracy, Precision, Recall, Selection Rate) across the randomly assigned "location" groups.
      * *Goal:* Verify that the random "location" attribute does not skew model performance or selection rates.
2.  **Model Explainability:** Generates SHAP summary and force plots to visualize feature contributions.
      * *Observation:* The plots for the **Virginica** class demonstrate that the "location" feature has negligible impact on model output, confirming the model correctly identified it as noise.

<!-- end list -->
