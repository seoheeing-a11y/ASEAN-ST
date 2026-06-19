# ASEAN-ST
NLP-based analysis of policy-academic alignment in ASEAN S&amp;T


This repository contains replication materials for the NLP Course Paper of "Do Policies Follow Research? Mapping the Alignment Between Academic Publication Trends and Policy Priorities in ASEAN Science and Technology"

## Abstract
This study examines whether national science and technology (S&T) policy priorities in ASEAN member states align with observed academic research output trends. Using OpenAlex as a source of 1.73 million S&T publications (2015-2025) and Overton as a repository of 200,044 policy documents, this paper applies a fine-tuned SciBERT classifier to categorize both corpora into 21 S&T fields defined by the OECD Frascati Manual. Country-level field distributions are then compared using cosine similarity and Pearson correlation to quantify the degree of policy-academic alignment. Results reveal substantial variation across ASEAN nations. Indonesia and Laos demonstrate relatively high alignment (cosine similarity = 0.749 and 0.659, respectively), while Cambodia shows the greatest divergence (0.353). These findings suggest that evidence-based policymaking remains inconsistently practiced across the region and that structural factors including development stage and international aid dependency may shape the science-policy interface. The SciBERT classifier achieved an overall accuracy of 0.764 and a macro-averaged F1 of 0.766 across 21 S&T fields. This paper contributes both a novel methodology for cross-domain NLP-based alignment measurement and empirical insights into S&T governance in Southeast Asia.

## Data Sources

The academic publication corpus is based on the OpenAlex database, accessed through the OpenAlex API. All works published between 2015 and 2025 by authors affiliated with institutions in the 11 ASEAN member states were retrieved, filtered to journal articles and conference proceedings with English abstracts and DOI identifiers (1,735,028 records).

The policy document corpus is based on the Overton database, which indexes government reports, think tank publications, and intergovernmental organization documents. Documents were collected using two strategies: a source_country filter for ASEAN governmental sources, and keyword queries combining ASEAN geographic terms with S&T field keywords (200,044 records after deduplication).

Processed and aggregated data files used for analysis are included in the data/ folder. Raw OpenAlex and Overton records are not included due to size and database licensing terms; they can be retrieved via the respective APIs using the queries described in the paper (Section 3.1).

## Structure
```

code/
  1_scibert_finetune_colab.ipynb       # SciBERT fine-tuning on OpenAlex data
  2_scibert_evaluation.ipynb           # Model evaluation (test set metrics, confusion matrix)
  3_policy_classification.ipynb        # Applies the fine-tuned classifier to Overton policy documents
  4_alignment_analysis.ipynb           # Field distributions, cosine similarity, Pearson correlation, figures
data/
  country_field_distributions.csv      # Country x field distribution (academic and policy)
  scibert_per_class_f1.csv             # Per-field classifier performance (Appendix A)
figures/
  figure1_heatmap.png                  # Academic and policy field distribution heatmap
  figure2_radar.png                    # Radar charts

```
