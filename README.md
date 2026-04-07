# News Article Clustering by Topic Similarity

## Overview
A large-scale comparative NLP study evaluating six vectorisation-clustering 
pipelines for unsupervised topic detection across 138,115 news articles.

## Key Finding
TF-IDF + HDBSCAN - an under-studied combination - achieved the strongest 
internal validation scores across all six experiments:
- Silhouette Score: 0.6692
- Davies-Bouldin Index: 0.4173
- BIRCH + TF-IDF achieved highest manual validation coherence: 94.9%

## Dataset
Combined corpus of 138,115 articles from:
- BBC News (Kaggle)
- Reuters-21578 (Kaggle)
- AG News Corpus (Kaggle)
- Scraped articles: CNN, The Guardian, TechCrunch

## Methodology Pipeline
1. Data Collection & Preprocessing (SpaCy - tokenisation, 
   lemmatisation, stopword removal, deduplication)
2. Vectorisation - TF-IDF (10,000 features) and S-BERT 
   (all-MiniLM-L6-v2, 384 dimensions)
3. Dimensionality Reduction - UMAP (reduced to 10 dimensions)
4. Clustering - HDBSCAN, K-Means, BIRCH
5. Evaluation - Silhouette Score, Davies-Bouldin Index, 
   Manual Validation

## Results Summary

| Method | Vectorisation | Silhouette | DB Index | Manual Accuracy |
|---|---|---|---|---|
| HDBSCAN | TF-IDF | 0.6692 | 0.4173 | 91.23% |
| HDBSCAN | S-BERT | 0.6174 | 0.4290 | 92.86% |
| K-Means | TF-IDF | 0.4368 | 0.8959 | 74.14% |
| K-Means | S-BERT | 0.4020 | 0.9264 | 87.27% |
| BIRCH | TF-IDF | 0.4109 | 0.8802 | 94.90% |
| BIRCH | S-BERT | 0.4057 | 0.8785 | 91.38% |

## Cluster Visualisation

Comparison of clustering behaviour across different vectorisation and clustering approaches.

![Clustering Comparison](outputs/figures/clustering_comparisons.png)

The visualisations demonstrate clearer cluster separation for HDBSCAN compared to K-Means, while BIRCH produces more compact and well-defined clusters, particularly when combined with TF-IDF representations. This aligns with the quantitative results, reinforcing the effectiveness of density-based clustering for this task.

## Tech Stack
Python · Scikit-learn · HDBSCAN · Sentence-Transformers · 
UMAP-learn · SpaCy · Pandas · NumPy · Matplotlib · 
Seaborn · PaCMAP · Plotly · Google Colaboratory

## Key Conclusions
- TF-IDF remains competitive with modern semantic embeddings 
  on large heterogeneous corpora
- HDBSCAN outperforms K-Means on both internal metrics 
  and cluster interpretability
- Quantitative metrics alone insufficient - manual validation 
  essential for assessing topical coherence
- All methods successfully scaled to 138,115 articles

## Practical Applications
News monitoring · Customer feedback analysis · 
Recommendation systems · Social media trend detection · 
Legal document clustering · Supervised dataset preparation

## Disclosure
Parts of the code were developed with AI-assisted tools. All experimentation, evaluation, and conclusions are the author's own.
