# Mental Health Survey Clustering Analysis (OSMI 2014)

This project applies **unsupervised machine learning** to the **Mental Health in Tech Survey (OSMI, 2014)** dataset to discover latent groups of employees with similar workplace mental-health patterns. The analysis covers preprocessing, clustering with multiple algorithms, evaluation, visualization (PCA), and saving the final best-performing model.

---

## Project Goals

- Clean and preprocess mixed survey data (numeric + categorical)
- Compare multiple clustering algorithms
- Evaluate clusters using internal metrics
- Visualize clusters using PCA (2D projection)
- Save the final best model for reuse

---

## Dataset

- Source: [**Kaggle – “Mental Health in Tech Survey” (OSMI, 2014)**](https://github.com/shivakumarmurarishetti/mental-health-survey-clustering-analysis/blob/main/survey.csv)
- Data includes demographic information, work environment, and attitudes toward mental health in the workplace. 

---

## Workflow Summary

### 1) Data Understanding & EDA
- Data types were inspected to identify categorical vs numerical variables before preprocessing.

### 2) Feature Selection
Columns dropped as non-informative for clustering (e.g., free-text/geo/time fields):
- `Timestamp`, `state`, `Country`, `comments`

### 3) Preprocessing (Scaling + Encoding)
- **Numerical features** → `StandardScaler`
- **Categorical features** → `OneHotEncoder(drop="if_binary", handle_unknown="ignore")`
- Final preprocessed feature matrix shape:
  - **(1258, 58)**

---

## Clustering Models Compared

Five algorithms were trained and compared: 

- **KMeans** (centroid-based)
- **Agglomerative Clustering** (hierarchical)
- **DBSCAN** (density-based)
- **Birch** (incremental clustering)
- **Spectral Clustering** (graph-based)

For fair comparison, most models used **n_clusters = 3** (DBSCAN determines clusters automatically). 

---

## Evaluation Metrics

Models were evaluated using:
- **Silhouette Score** (higher is better)
- **Davies–Bouldin Index** (lower is better)

### Best Model
**KMeans (k=3, random_state=42)** performed best overall:
- Silhouette: **0.131670**
- Davies–Bouldin: **1.698955**

---

## Final Model + Saving

After evaluation, **KMeans (k=3)** was selected as the final model and saved using **joblib** for reproducibility. 

Saved model file:
- `final_kmeans_model.joblib`

---

## Files in This Repository

- [`MentalHealthSurveyClusteringAnalysis.ipynb`](https://github.com/shivakumarmurarishetti/mental-health-survey-clustering-analysis/blob/main/MentalHealthSurveyClusteringAnalysis.ipynb) — full analysis notebook
- [`MentalHealthSurveyClusteringAnalysis.html`](https://github.com/shivakumarmurarishetti/mental-health-survey-clustering-analysis/blob/main/MentalHealthSurveyClusteringAnalysis.html) — HTML export of the notebook/report 
- [`final_kmeans_model.joblib`](https://github.com/shivakumarmurarishetti/mental-health-survey-clustering-analysis/blob/main/final_kmeans_model.joblib) — saved KMeans clustering model 
- [`requirements.txt`](https://github.com/shivakumarmurarishetti/mental-health-survey-clustering-analysis/blob/main/requirements.txt) — required Python libraries and versions 
- [Survey spreadsheet](https://github.com/shivakumarmurarishetti/mental-health-survey-clustering-analysis/blob/main/survey.csv) — dataset used in the notebook (original/source file)

---
## 📄 Project Report (PDF)

A complete project report (converted from the analysis notebook) is available as a PDF:

- [`MentalHealthSurveyClusteringAnalysis.pdf`](https://github.com/shivakumarmurarishetti/mental-health-survey-clustering-analysis/blob/main/MentalHealthSurveyClusteringAnalysis.pdf)

The report includes:
- Data preprocessing steps
- Clustering methodology
- Model comparison and evaluation
- Final conclusions and visualizations

## How to Run

### Option A: Run the notebook
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
