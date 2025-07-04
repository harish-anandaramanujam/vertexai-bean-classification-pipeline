# Vertex AI Bean Classification Pipeline

This project demonstrates how to build an end-to-end machine learning pipeline on Google Cloud Vertex AI using the UCI Dry Beans dataset. The pipeline covers dataset creation, AutoML model training, evaluation, conditional deployment, and metrics visualization.

---

## 📖 Overview

- **Dataset:** UCI Dry Beans dataset  
- **Goal:** Build a Kubeflow pipeline to classify beans into 7 types using tabular features and deploy the model if it meets evaluation thresholds.

---

## 🚀 Pipeline Steps

1. **Environment Setup**
   - Installs required Python packages (`google-cloud-aiplatform`, `kfp`, `google-cloud-pipeline-components`, etc.).
   - Sets up environment variables for project, region, and GCS bucket.

2. **Import Libraries**
   - Imports KFP, Vertex AI SDK, and supporting libraries.

3. **Custom Model Evaluation Component**
   - Defines a custom component to fetch and log evaluation metrics (ROC curve, confusion matrix).
   - Compares evaluation metrics to user-defined thresholds to decide on deployment.

4. **Pipeline Definition**
   - **Dataset Creation:** Loads data from BigQuery into Vertex AI as a tabular dataset.
   - **AutoML Training:** Trains a classification model using AutoML.
   - **Model Evaluation:** Evaluates the trained model using the custom component.
   - **Conditional Deployment:** Deploys the model to an endpoint only if evaluation metrics meet the threshold.

5. **Pipeline Compilation & Execution**
   - Compiles the pipeline to a JSON spec.
   - Runs the pipeline using the Vertex AI Pipelines client.

6. **Metrics Visualization**
   - Retrieves and displays pipeline run metrics for comparison.

---

## 📝 Usage

### 1. Clone the Repository

```sh
git clone https://github.com/harish-anandaramanujam/vertexai-bean-classification-pipeline.git
cd vertexai-bean-classification-pipeline
```

### 2. Open the Notebook

Open `vertexai-advanced.ipynb` in JupyterLab or Google Cloud Vertex AI Workbench.

### 3. Set Up Google Cloud

- Ensure you have a Google Cloud project with Vertex AI enabled.
- Set your `PROJECT_ID` and `REGION` in the notebook.
- Authenticate with Google Cloud (`gcloud auth login`).

### 4. Run the Notebook

- Execute all cells in order.
- The pipeline will be compiled and submitted to Vertex AI Pipelines.
- Monitor the pipeline run in the [Vertex AI Console](https://console.cloud.google.com/vertex-ai/pipelines).

---

## Pipeline
![Vertex AI Bean Classification Pipeline](assets/bean-training.png)

---

## 📊 References

- [Vertex AI Documentation](https://cloud.google.com/vertex-ai/docs)
- [Kubeflow Pipelines SDK](https://www.kubeflow.org/docs/components/pipelines/sdk/sdk-overview/)
- [UCI Dry Beans Dataset](https://archive.ics.uci.edu/ml/datasets/Dry+Bean+Dataset)

---

## 🛠️ Requirements

- Python 3.7+
- Google Cloud account with Vertex AI enabled
- Jupyter Notebook or Vertex AI Workbench

---

## ✨ Future Improvements

- Add hyperparameter tuning steps.
- Integrate model explainability components.
- Automate pipeline triggers on new