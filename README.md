# News Article Clustering by Topic Similarity

## Large-Scale Comparative NLP Study on 138,115 News Articles

A flagship unsupervised machine learning project exploring how modern and traditional NLP techniques perform when clustering real-world news articles into meaningful topics at scale.

This study evaluated six end-to-end pipelines across lexical and semantic text representations using three clustering paradigms. The results challenge common assumptions by showing that simpler methods such as TF-IDF can remain highly competitive against modern embeddings, while underused clustering algorithms can outperform conventional baselines.

---

## Why This Project Matters

Large volumes of unstructured text are generated every day across news, customer feedback, legal documents, research papers, and social media.

Organisations need scalable ways to automatically group unlabelled text into themes, detect emerging topics, and organise information efficiently.

This project demonstrates how unsupervised NLP can solve that problem using production-relevant methods, rigorous evaluation, and large-scale experimentation.

---

## Executive Summary

Most published clustering studies use relatively small datasets and rely heavily on traditional methods such as K-Means.

This project moved beyond that by testing six combinations of:

- **TF-IDF** (lexical representation)
- **S-BERT** (semantic embeddings)
- **HDBSCAN** (density-based clustering)
- **K-Means** (centroid-based clustering)
- **BIRCH** (hierarchical clustering)

on a combined corpus of **138,115 real-world news articles**.

The outcome showed that:

- **HDBSCAN + TF-IDF** achieved the strongest internal validation performance
- **BIRCH + TF-IDF** achieved the highest human-evaluated topical coherence
- **TF-IDF remained highly competitive with S-BERT at scale**

---

## Key Findings

### Best Quantitative Performance

**HDBSCAN + TF-IDF**

- Silhouette Score: **0.6692**
- Davies-Bouldin Index: **0.4173**

This combination delivered the strongest balance of cluster cohesion and separation.

### Best Human Interpretability

**BIRCH + TF-IDF**

- Manual topical coherence: **94.9%**

Clusters were highly aligned with human judgement.

### Strategic Insight

Despite the popularity of transformer embeddings, **TF-IDF proved exceptionally strong on a large heterogeneous corpus**, offering both performance and interpretability.

---

## Dataset

Combined corpus of **138,115 news articles** from multiple sources:

- BBC News
- Reuters-21578
- AG News Corpus
- Scraped live news sources:
  - CNN
  - The Guardian
  - TechCrunch

This created a realistic mix of:

- short-form headlines
- long-form journalism
- multiple writing styles
- diverse subject domains

---

## Methodology Pipeline

![Pipeline](outputs/figures/methodology_pipeline.png)

### 1. Data Preparation

- Cleaning and standardisation
- Deduplication
- Tokenisation
- Lemmatisation
- Stopword removal using spaCy

### 2. Text Representation

- TF-IDF (10,000 features)
- S-BERT embeddings (384 dimensions)

### 3. Dimensionality Reduction

- UMAP to 10 dimensions for clustering efficiency

### 4. Clustering Algorithms

- HDBSCAN
- K-Means
- BIRCH

### 5. Evaluation Framework

- Silhouette Score
- Davies-Bouldin Index
- Manual cluster validation
- Visual cluster inspection

---

## Results Summary

| Method | Representation | Silhouette | DB Index | Manual Accuracy |
|--------|----------------|-----------|----------|----------------|
| HDBSCAN | TF-IDF | **0.6692** | **0.4173** | 91.23% |
| HDBSCAN | S-BERT | 0.6174 | 0.4290 | 92.86% |
| K-Means | TF-IDF | 0.4368 | 0.8959 | 74.14% |
| K-Means | S-BERT | 0.4020 | 0.9264 | 87.27% |
| BIRCH | TF-IDF | 0.4109 | 0.8802 | **94.90%** |
| BIRCH | S-BERT | 0.4057 | 0.8785 | 91.38% |

---

## Cluster Visualisation

![Clustering](outputs/figures/clustering_comparisons.png)

### Observations

- **HDBSCAN** created clearer cluster separation and filtered noisy articles
- **K-Means** assigned every article but produced weaker separation
- **BIRCH** created stable and interpretable clusters at scale

---

## Technical Trade-Offs

| Method | Strength | Limitation |
|--------|----------|-----------|
| HDBSCAN | Strong separation and noise filtering | Leaves some points unassigned |
| K-Means | Fast and complete assignment | Lower cohesion |
| BIRCH | Scalable and interpretable | Lower internal metric scores |

---

## Practical Applications

This framework can be extended beyond news articles into:

- News topic detection
- Trend monitoring
- Recommendation systems
- Customer feedback analysis
- Social media monitoring
- Legal document organisation
- Research paper grouping
- Dataset labelling for supervised learning

---

## Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- HDBSCAN
- Sentence-Transformers
- spaCy
- UMAP
- PaCMAP
- Plotly
- Matplotlib
- Seaborn
- Google Colab

---

## Research Contribution

This project contributes by:

- Benchmarking clustering on **138K+ documents**
- Comparing six full NLP pipelines
- Testing underused methods such as **HDBSCAN** and **BIRCH**
- Combining quantitative metrics with human validation
- Demonstrating that simpler lexical methods remain highly relevant

---

## Development Note

Parts of the coding workflow were developed with AI assistance for productivity, debugging support, and code refinement.

Problem framing, experimental design, evaluation decisions, interpretation of findings, and conclusions were independently directed and validated by the author.

---

## Author

Developed as an MSc Data Science & AI dissertation project focused on scalable unsupervised NLP, clustering evaluation, and practical machine learning applications.
