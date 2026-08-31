# Scientific Article Trend Analysis

An NLP-based project for analyzing trends in scientific article topics using text preprocessing, TF-IDF feature extraction, K-Means clustering, WordCloud visualization, and a graphical user interface.

---

## Overview

The rapid growth of scientific publications makes it increasingly difficult to manually examine large collections of articles and identify emerging research patterns.

This project analyzes scientific article titles and abstracts to identify groups of related topics and explore research trends over time.

The project applies Natural Language Processing (NLP) and unsupervised machine learning techniques to transform textual data into numerical representations and group similar articles into clusters.

The main techniques used in this project are:

- Text preprocessing
- TF-IDF feature extraction
- K-Means clustering
- Silhouette Score evaluation
- Davies-Bouldin Index evaluation
- WordCloud visualization
- Graphical User Interface (GUI)

---

## Objectives

The main objectives of this project are:

- To preprocess scientific article text for analysis.
- To extract important textual features using TF-IDF.
- To identify groups of similar articles using K-Means clustering.
- To analyze keywords associated with each cluster.
- To evaluate the quality of the resulting clusters.
- To visualize research trends using WordCloud and graphical visualizations.
- To provide a graphical interface for exploring article trends.

---

## Dataset

The dataset was obtained from Kaggle and originally contained approximately **5 million scientific article records**.

For this project, a subset of **10,000 articles** was used for analysis.

The original dataset contained 14 columns:

- `id`
- `submitter`
- `author`
- `title`
- `comments`
- `journal-ref`
- `doi`
- `report-no`
- `categories`
- `license`
- `abstract`
- `versions`
- `update-date`
- `author-parsed`

For the analysis, the following information was selected:

- `title`
- `abstract`
- `update-date`

The `update-date` field was converted into an `update-year` variable so that article trends could be analyzed across different years.

---

## Dataset Distribution by Year

The selected dataset contains articles published across multiple years.

| Year | Number of Articles |
|---:|---:|
| 2007 | 3,111 |
| 2008 | 2,069 |
| 2009 | 3,040 |
| 2010 | 359 |
| 2011 | 324 |
| 2012 | 152 |
| 2013 | 82 |
| 2014 | 119 |
| 2015 | 303 |
| 2016 | 182 |
| 2017 | 46 |
| 2018 | 28 |
| 2019 | 129 |
| 2020 | 18 |
| 2021 | 14 |
| 2022 | 14 |
| 2023 | 10 |

The distribution shows that most of the selected articles are concentrated in the earlier years of the dataset, particularly between 2007 and 2009.

---

## Data Preprocessing

Before applying feature extraction and clustering, the textual data was preprocessed to improve its quality and consistency.

The preprocessing steps included:

- Checking for duplicate records.
- Checking for missing values.
- Removing unnecessary columns.
- Removing stopwords.
- Applying stemming.
- Converting text to lowercase.

These steps were performed to reduce noise and create a cleaner textual representation for subsequent analysis.

---

## Feature Extraction

After preprocessing, TF-IDF was applied to transform the article text into numerical features.

### TF-IDF

**Term Frequency-Inverse Document Frequency (TF-IDF)** measures the importance of a word within a document relative to the overall collection of documents.

The process consists of:

1. **Term Frequency (TF)**

   Measures how frequently a word occurs within a document.

2. **Inverse Document Frequency (IDF)**

   Measures how unique a word is across the document collection.

3. **TF-IDF Weighting**

   Combines TF and IDF to produce a weight representing the importance of each word.

Words that occur frequently in a specific document but less frequently across the entire collection receive higher TF-IDF weights.

The resulting TF-IDF representation was used as the input for clustering.

---

## Keyword Analysis

The TF-IDF results were also used to identify important keywords associated with the article clusters.

Words with higher TF-IDF weights were considered more representative of the content within the corresponding cluster.

The project visualized important keywords using WordCloud.

The size of each word in the WordCloud represents its relative importance within the analyzed text.

---

## WordCloud Visualization

WordCloud visualizations were created to provide an intuitive representation of important keywords.

The visualization allows frequently or strongly weighted terms to be identified more easily.

Examples of high-weight terms identified in the analysis include:

- `model`
- `system`
- `field`
- `effect`
- `quantum`
- `galaxi`
- `star`
- `cluster`
- `network`
- `theori`

The WordCloud analysis provides additional context for interpreting the topics represented by each cluster.

---

## K-Means Clustering

After feature extraction, K-Means clustering was applied to group articles based on similarities in their TF-IDF representations.

K-Means is an unsupervised learning algorithm that groups observations into clusters based on their feature similarity.

The clustering process aims to:

- Minimize variation within each cluster.
- Maximize separation between different clusters.
- Identify natural groupings within the textual data.

The project grouped the articles into **3 clusters**.

---

## Clustering Results

The resulting clusters contained the following numbers of articles:

| Cluster | Number of Articles |
|---:|---:|
| 0 | 4,510 |
| 1 | 1,419 |
| 2 | 4,071 |
| **Total** | **10,000** |

Cluster 0 contained the largest number of articles, followed by Cluster 2, while Cluster 1 contained substantially fewer articles.

The cluster distribution was also visualized using a bar chart.

---

## Cluster Keywords

The TF-IDF analysis provided keywords that can be used to interpret the content represented by each cluster.

### Cluster 0

Important terms associated with Cluster 0 included words related to areas such as:

- Physics
- Quantum systems
- Models
- Particles
- Interactions
- Energy
- Materials

Examples of high-weight terms include:

- `model`
- `effect`
- `system`
- `field`
- `energy`
- `quantum`
- `decay`
- `electron`

### Cluster 1

Cluster 1 contained keywords associated with astronomical and observational research.

Examples include:

- `star`
- `galaxi`
- `observ`
- `cluster`
- `xray`

These terms indicate that this cluster contains article topics related to astronomy and astrophysics.

### Cluster 2

Cluster 2 contained terms related to mathematical, theoretical, and computational concepts.

Examples include:

- `quantum`
- `field`
- `theori`
- `function`
- `network`
- `system`
- `model`
- `equat`

These keywords indicate that the cluster contains articles involving theoretical and mathematical concepts.

---

## Clustering Evaluation

Two evaluation metrics were used to assess the quality of the K-Means clustering:

- **Silhouette Score**
- **Davies-Bouldin Index**

### Silhouette Score

The Silhouette Score measures how similar an observation is to its own cluster compared with other clusters.

The score ranges from **-1 to 1**.

A higher score generally indicates better-defined clusters.

The obtained scores were:

| Cluster | Silhouette Score |
|---:|---:|
| 0 | 0.003020 |
| 1 | 0.015141 |
| 2 | 0.002838 |
| **Average** | **0.004666** |

The average Silhouette Score was:

**0.004666**

The relatively low score indicates that the resulting clusters have limited separation.

### Davies-Bouldin Index

The Davies-Bouldin Index evaluates the similarity between clusters based on their compactness and separation.

A lower value generally indicates better clustering quality.

The resulting Davies-Bouldin Index was:

**13.475784046594464**

The relatively high value provides additional evidence that the resulting clusters have limited separation.

---

## Trend Visualization

The project also analyzed the distribution of scientific articles across different years.

The `update-date` information was converted into an `update-year` variable to support temporal analysis.

The year-based visualization provides an overview of how the number of articles changes across the available publication years.

The analysis shows that the selected data is highly concentrated in the earlier years, particularly:

- 2007
- 2008
- 2009

The number of articles decreases substantially in subsequent years.

This temporal distribution should be considered when interpreting research trends because the available observations are not evenly distributed across years.

---

## Graphical User Interface

A **Graphical User Interface (GUI)** was developed to provide users with a more accessible way to explore the results of the analysis.

The GUI integrates the analysis results into a user-facing interface and allows users to interact with the available information without directly working with the underlying analysis process.

The interface supports exploration of the scientific article trend analysis and visualization results.

---

## Results

The project successfully implemented a text mining and clustering workflow for analyzing scientific article data.

The main results are:

- Approximately **5 million records** were available in the original dataset.
- **10,000 articles** were selected for the project analysis.
- Text preprocessing was applied to the article data.
- TF-IDF was used to convert textual information into numerical features.
- K-Means was used to group articles into **3 clusters**.
- WordCloud was used to visualize important keywords.
- Silhouette Score was used to evaluate cluster quality.
- Davies-Bouldin Index was used as an additional clustering evaluation metric.
- A graphical user interface was developed to support exploration of the analysis results.

The final cluster distribution was:

| Cluster | Number of Articles |
|---:|---:|
| Cluster 0 | 4,510 |
| Cluster 1 | 1,419 |
| Cluster 2 | 4,071 |

The clustering evaluation produced:

| Evaluation Metric | Result |
|---|---:|
| Average Silhouette Score | 0.004666 |
| Davies-Bouldin Index | 13.475784046594464 |

The results indicate that the clustering process successfully generated groups of articles, although the relatively low Silhouette Score and high Davies-Bouldin Index suggest that the clusters are not strongly separated.

---

## Key Findings

### 1. TF-IDF can represent scientific article text numerically

TF-IDF transformed article titles and abstracts into numerical feature vectors that could be processed by an unsupervised machine learning algorithm.

### 2. Three clusters were identified

K-Means grouped the 10,000 selected articles into three clusters:

- Cluster 0: 4,510 articles
- Cluster 1: 1,419 articles
- Cluster 2: 4,071 articles

### 3. The clusters contain different keyword patterns

The keyword analysis revealed differences in the dominant terms associated with the clusters.

For example, astronomical terms such as `star`, `galaxi`, and `observ` were prominent in one cluster, while other clusters contained terms related to quantum physics, systems, models, networks, and theoretical concepts.

### 4. Cluster separation was limited

The average Silhouette Score was only **0.004666**, indicating weak separation between the resulting clusters.

The Davies-Bouldin Index of **13.475784046594464** also indicates that the clusters have relatively high similarity.

### 5. The dataset has an uneven temporal distribution

Most selected articles came from 2007–2009, while substantially fewer articles were available in later years.

Therefore, temporal trend interpretation should take the uneven distribution into account.

### 6. Visualization improves interpretation

WordClouds, cluster distribution charts, and the GUI make the results easier to explore and interpret compared with examining numerical clustering results alone.

---

## Limitations

Several limitations should be considered when interpreting the results of this project.

### Dataset Sampling

The original dataset contained approximately 5 million records, while only 10,000 articles were selected for the analysis.

Therefore, the resulting clusters may not fully represent the characteristics of the complete dataset.

### Cluster Quality

The clustering evaluation produced a low Silhouette Score and a relatively high Davies-Bouldin Index.

This indicates that the identified clusters have limited separation.

### Number of Clusters

The analysis used **3 clusters** for K-Means.

Different values of K may produce different groupings and potentially more meaningful topic structures.

### Feature Representation

The project uses TF-IDF as the textual representation.

TF-IDF focuses on word frequency and importance but does not fully capture semantic relationships, context, or word order.

### Temporal Distribution

The article data is unevenly distributed across years.

The large concentration of articles in earlier years may influence the interpretation of research trends.

### Missing Original Notebooks

The original analysis was developed using multiple separate notebooks rather than a single consolidated notebook.

Those original notebooks are no longer available in their complete form.

Therefore, this repository preserves the available project outputs and documentation rather than presenting a reconstructed notebook as if it were the original implementation.

---


