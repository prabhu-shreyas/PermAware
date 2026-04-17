# 🔐 PermAware: Context-Aware Android Permission Justification

PermAware is a context-aware system designed to analyze Android application permissions and determine whether they are **Justified** or **Unjustified** based on the application's category. For example, a Social Media application requesting Camera permission is labeled as **"Justified"**, whereas a Gaming app requesting the same permission may be flagged as **"Unjustified"**.

Unlike traditional approaches that rely on fixed static rules or simple malware detection, PermAware leverages a fine-tuned **BERT (Bidirectional Encoder Representations from Transformers)** model to understand the deep semantic relationship between permission requests and app categories, enabling a more intelligent and privacy-focused analysis.

---

## 📊 Performance & Key Results
* **Accuracy:** 92.5% on a held-out validation set.
* **F1-Score:** 0.88, demonstrating robust performance on imbalanced datasets.
* **Explainability:** Token-level attention heatmaps are used to visualize the contextual relationships between specific permissions and app categories.

## 🛠️ System Pipeline
The framework operates through a structured four-stage modular pipeline:

1. **Input:** Accepts manual permission-category pairs or automated metadata scraping using an Application ID.
2. **Scraper & Normalizer:** Uses **BeautifulSoup** for scraping publicly available Play Store metadata.
   * Normalizes heterogeneous or noisy permission text into canonical labels (e.g., mapping various audio-related strings to `RECORD_AUDIO`).
3. **BERT Classifier:** * Performs binary classification (Justified / Unjustified) using structured natural-language prompts for contextual understanding.
   * Utilizes the `bert-base-uncased` architecture.
4. **Interface:** Provides real-time predictions via a lightweight **Streamlit** web application.

## 📂 Dataset Details
* **Source:** Custom rule-based synthetic dataset (developed due to the lack of suitable public datasets).
* **Size:** 980 permission–category pairs.
  * 308 Justified.
  * 672 Unjustified.
* **Scope:** Covers 10 well-known application categories and 14 canonical permission types.

## 🚀 How to Run (Google Colab)
This project is optimized for **Google Colab** using an **NVIDIA T4 GPU**.

### 1. Run Cells Sequentially
Execute all cells from top to bottom:
* **Install dependencies:** `transformers`, `streamlit`, `pyngrok`.
* **Load Model:** Initialize the fine-tuned BERT model.
* **Launch:** Deploy the Streamlit interface.

### 2. Ngrok Authentication
To access the web interface:
* Enter your **Ngrok Auth Token** in 3rd cell by replacing "Add your ngrok authentication token here".

### 3. Research vs. Implementation
* **Implementation Cells:** Required to launch and run the application.
* **Research Cells (below pyngrok code):**
  * Contains code for the **ablation study** and performance benchmarking.
  * These are optional and can be skipped for normal prototype usage.

## 🤝 Contributors
* **Shreyas Prabhu** – St. John College of Engineering and Management
* **Sharvareesh Upadhyay** – St. John College of Engineering and Management
* **Jayesh Sutar** – St. John College of Engineering and Management
* **Pooja Gharat** (Advisor) – St. John College of Engineering and Management

## 📄 License
This project is licensed under the **MIT License**.

---
⭐ *If you found this project useful, consider giving it a star!*
