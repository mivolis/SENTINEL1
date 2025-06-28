# 🧠 SENTINEL
This repository provides a pipeline for collecting PROTAC warhead data, matching compound identifiers across sources, and evaluating machine learning models (GCN, GAT, and Random Forest) for predicting off-target gene interactions.

---

## 📦 Installation

To get started, install the required Python packages:

```bash
pip install torch_geometric deepchem
````

---

## 📊 Data Collection Pipeline

We collect and unify warhead compound information from various data sources using the following steps:

1. **PubChem ID Mapping**

   * After splitting warhead data into different sources, we use a *separate matching method* to map them to their corresponding **PubChem CIDs**.
   * 📍 Refer to **Figure 1** in the paper for a visual overview.

2. **RxCUI Transfer**

   * The RxNorm concept unique identifiers (RxCUI) are collected using:

     ```bash
     rxcui-collect.ipynb
     ```

3. **Compound Matching**

   * Successfully matched compounds across databases are aggregated using:

     ```bash
     pubchem_matching.ipynb
     ```

4. **Deduplication**

   * Gene names associated with the same PubChem ID are deduplicated via:

     ```bash
     deduplicate.ipynb
     ```

---

## 🧪 Model Training and Evaluation

We implement and evaluate several graph-based and classical machine learning models:

* **Graph Neural Networks** (GCN, GAT)
* **Random Forest Classifier**

All models are trained and evaluated with cross-validation (CV) and standard classification metrics (AUC, F1, etc.) in:

```bash
CV_on_different_models_auc_plot_and_test_by_different_metrics.ipynb
```

The trained models are organized in the following directories:

* GAT models: `cv_models_GAT_new/`
* GCN models: `cv_models_GCN_new/`

Final models used in experiments:

* GAT: `cv_models_GAT_new/final_model.pt`
* GCN: `cv_models_GCN_new/final_model.pt`

---

## 📁 Dataset

Datasets are located in the [`datasets/`](./datasets) directory. These include:

* Graph representations of molecules
* Matched gene targets
* Source-specific identifier mappings

---

## 📬 Contact

For questions or collaborations, feel free to reach out via GitHub issues or pull requests.

---

## 📄 License

This project is licensed under the MIT License.
