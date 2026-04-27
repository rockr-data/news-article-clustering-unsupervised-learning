# News Article Clustering by Topic Similarity

## Large-Scale Comparative NLP Study on 138,115 News Articles

A flagship unsupervised machine learning project exploring how different text representations and clustering algorithms perform when grouping real-world news articles into meaningful topics at scale.

This project was designed not only to build clusters, but to test important questions in applied NLP:

- Do semantic embeddings always outperform lexical methods?
- Are widely used methods like K-Means always the best choice?
- Can less commonly tested algorithms perform better at scale?
- How should clustering quality be evaluated beyond metrics alone?

---

## Why This Project Matters

Modern organisations generate vast volumes of unstructured text across:

- News platforms
- Customer reviews
- Support tickets
- Research papers
- Legal documents
- Social media

Automatically organising this text into themes can unlock faster decision-making, trend detection, recommendation systems, and downstream supervised learning.

This project demonstrates how scalable unsupervised NLP can support those goals using rigorous experimentation on a large real-world corpus.

---

## Research Motivation

Many published clustering studies are limited by one or more of the following:

- Small datasets
- Over-reliance on K-Means
- Limited comparison across embeddings
- Heavy dependence on internal metrics only
- Minimal focus on interpretability

This project was created to address those gaps through a structured comparative study on **138,115 articles** using six full pipelines.

---

## Why These Methods Were Chosen

### Text Representations

#### TF-IDF

Selected as a strong lexical baseline.

Useful for capturing distinctive keywords and interpretable topic signals.

#### S-BERT

Selected as a modern semantic embedding model.

Useful for recognising conceptual similarity beyond exact word overlap.

---

### Clustering Algorithms

#### HDBSCAN

Chosen because:

- Less frequently tested in news clustering
- Automatically determines cluster structure
- Detects noise and ambiguous articles
- Handles variable-density clusters

#### K-Means

Chosen as the classic benchmark.

- Fast
- Popular in literature
- Full assignment of all data points

#### BIRCH

Chosen because:

- Designed for large-scale efficiency
- Hierarchical clustering behaviour
- Underused in news clustering research

---

## Dataset

Combined corpus of **138,115 real-world news articles** from:

- BBC News
- Reuters-21578
- AG News Corpus
- Scraped sources:
  - CNN
  - The Guardian
  - TechCrunch

This created a realistic mix of:

- short and long articles
- multiple publishers
- varied writing styles
- broad subject diversity

---

## Methodology Pipeline

![Pipeline](outputs/figures/methodology_pipeline.png)

### 1. Preprocessing

- Cleaning and standardisation
- Deduplication
- Tokenisation
- Lemmatisation
- Stopword removal using spaCy

### 2. Vectorisation

- TF-IDF (10,000 features)
- S-BERT embeddings (384 dimensions)

### 3. Dimensionality Reduction

- UMAP to 10 dimensions

### 4. Clustering

- HDBSCAN
- K-Means
- BIRCH

### 5. Evaluation

- Silhouette Score
- Davies-Bouldin Index
- Manual cluster validation
- Visual inspection

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

## Key Experimental Observations

### 1. TF-IDF Remained Highly Competitive

Despite the popularity of transformer embeddings, TF-IDF often produced stronger internal validation scores.

This suggests lexical signals remain powerful on large heterogeneous corpora.

### 2. HDBSCAN Produced the Strongest Internal Metrics

**TF-IDF + HDBSCAN** delivered the best cohesion and separation.

It was especially effective at filtering ambiguous articles as noise.

### 3. BIRCH Produced the Most Interpretable Clusters

Although internal metrics were weaker, **BIRCH + TF-IDF** achieved the highest manual coherence.

This highlights that numerical scores do not always match human judgement.

### 4. K-Means Prioritised Coverage Over Purity

K-Means assigned every article to a cluster, but clusters were often less distinct.

### 5. S-BERT Grouped Broader Themes

Semantic embeddings often grouped conceptually related articles, but sometimes merged distinct topics into wider clusters.

---

## Important Insight

Clustering quality should not be judged using metrics alone.

A method with lower Silhouette Score may still produce clusters that are more meaningful to humans.

This is why manual validation was included.

---

## Cluster Visualisation

![Clustering](outputs/figures/clustering_comparisons.png)

### Visual Findings

- HDBSCAN showed clearer boundaries and visible noise regions
- K-Means produced denser full-assignment partitions
- BIRCH created broader stable groupings
- Large datasets create naturally crowded visualisations, making complementary validation essential

---

## Practical Method Selection Guide

| Use Case | Recommended Approach |
|---------|----------------------|
| Highest topic precision | HDBSCAN + TF-IDF |
| Broad semantic grouping | HDBSCAN + S-BERT |
| Need every document assigned | K-Means |
| Large-scale interpretable clustering | BIRCH + TF-IDF |
| Fast baseline benchmarking | K-Means + TF-IDF |

---

## Practical Applications

- News topic detection
- Trend monitoring
- Recommendation systems
- Customer feedback analysis
- Social media monitoring
- Legal document grouping
- Research paper organisation
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

- Evaluating clustering at **138K+ article scale**
- Comparing six complete NLP pipelines
- Demonstrating the value of underused methods such as HDBSCAN and BIRCH
- Showing TF-IDF remains highly relevant
- Combining metrics with human validation
- Highlighting real-world method trade-offs

---

## Development Note

Parts of the coding workflow were developed with AI assistance for productivity, debugging support, and code refinement.

Problem framing, experiment design, parameter selection, evaluation decisions, interpretation of findings, and conclusions were independently directed and validated by the author.

---

## Author

Developed as an MSc Data Science & AI dissertation project focused on scalable unsupervised NLP, clustering evaluation, and practical machine learning applications.
