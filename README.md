# SEO Compass: Query Performance & Opportunity Mapper

**SEO Compass** is an AI-driven data science pipeline designed to analyze Search Engine Optimization (SEO) query data. By leveraging state-of-the-art Natural Language Processing (NLP), it groups raw search queries into semantic clusters to reveal high-level topics, identifying content opportunities and risks across different time periods.

## Project Overview

This tool moves beyond basic keyword analysis by using **Semantic Clustering**. Instead of grouping queries by matching words (e.g., "shoe" vs. "shoes"), it groups them by user intent (e.g., "running gear" and "jogging sneakers" would be clustered together). It then compares performance metrics between two periods to visualize growth or decline.

## Key Features

* **Semantic Embeddings:** Uses the `all-mpnet-base-v2` Sentence Transformer model to convert queries into vector embeddings, capturing deep semantic meaning.
* **Automated Clustering:** Implements **K-Means clustering** with an auto-tuning function (using Silhouette Scores) to determine the optimal number of topics dynamically.
* **Performance Comparison:** Analyzes "Period A" vs. "Period B" data to calculate deltas in Clicks, Impressions, CTR, and Weighted Average Position.
* **Smart Labeling:** Automatically names clusters based on the centroid (most representative) query within the group.
* **Opportunity & Risk Scoring:**
    * **Opportunity Score:** Identifies clusters where rankings are improving, and traffic is growing.
    * **Risk Score:** Flags clusters where rankings are dropping, and traffic is bleeding.
* **Advanced Visualizations:**
    * **UMAP Projection:** 2D semantic map of the query landscape.
    * **Quadrant Analysis:** Visual scatter plot separating "Opportunities" from "Risks."
    * **Trajectory Plot:** Shows the movement of topics in ranking vs. traffic over time.

## Tech Stack

* **Python 3**
* **NLP/ML:** `sentence-transformers`, `scikit-learn` (KMeans, Silhouette Score)
* **Data Manipulation:** `pandas`, `numpy`
* **Visualization:** `seaborn`, `matplotlib`, `umap-learn`

## Workflow

1.  **Data Ingestion:** Loads GSC (Google Search Console) data containing queries, clicks, impressions, and positions (supports both synthetic mock data and real CSV uploads).
2.  **Preprocessing:** Cleans data, filters brand terms via Regex, and removes low-volume queries.
3.  **Vectorization & Clustering:** Embeds queries and groups them into thematic clusters.
4.  **Metric Aggregation:** Calculates weighted average positions and traffic shifts per cluster.
5.  **Visualization:** Generates interactive and static charts to guide SEO strategy.

## Usage

The project is structured as a Jupyter Notebook. To run it:

1.  **Install dependencies:**
    ```bash
    pip install sentence-transformers scikit-learn umap-learn seaborn matplotlib pandas numpy
    ```

2.  **Open the notebook.**

3.  **Configure Data:**
    Toggle `USE_SYNTHETIC_DATA = True` to test with mock data, or set to `False` and provide your own `period_a.csv` and `period_b.csv`.

4.  **Run:**
    Execute all cells to generate the clustering report and visualizations.
