Overview
TransLegalSim is a transformer-based system for legal document similarity analysis that enhances semantic representations using Domain-Adaptive Embedding Refinement (DAERM). The system leverages pretrained transformer models along with structured legal metadata to improve retrieval and clustering of judicial decisions.

The primary dataset used is the Brazilian Court Decisions dataset, with additional validation on Indian Supreme Court judgments to demonstrate generalizability across legal systems.

Objectives
Perform semantic similarity analysis on legal documents
Improve embedding quality using domain-specific metadata
Compare baseline transformer embeddings with DAERM-enhanced embeddings
Enable accurate case retrieval and clustering

Methodology
The system follows a structured pipeline:
Data Loading
   Load datasets using Hugging Face and Pandas
Text Preprocessing
    Clean and normalize legal text
    Remove noise and formatting
Baseline Model
    Generate embeddings using SentenceTransformer (all-MiniLM-L6-v2)
    Use only textual content
DAERM Model
    Inject metadata into text representation
    Selected metadata using Mutual Information:
        orgao_julgador
        unanimity_label
        judge_relator
        judgment_label
        ementa_text
Similarity Computation
     Cosine similarity between embeddings
Clustering
     K-Means for grouping similar cases
Visualization
    UMAP for 2D embedding visualization

Key Concept: DAERM
Instead of modifying the transformer, DAERM enhances input representation by concatenating structured metadata with legal text:
[COURT]
[JUDGE]
[UNANIMITY]
[LEGAL_SUMMARY]
[DESCRIPTION]
This improves domain-awareness without retraining the model.

Results
  DAERM improves retrieval relevance compared to baseline
  Better clustering and separation in embedding space
  Strong performance across multiple legal domains

Dataset
  Brazilian Dataset
    Source: Hugging Face (joelniklaus/brazilian_court_decisions)
    Contains:
       Legal summaries (ementa)
       Decision descriptions
       Metadata (court, judge, labels)

  Indian Dataset
     Supreme Court judgments (https://drive.google.com/file/d/1wyys1cjeKHuTYF3ZUx9FzkvUz63ibPx4/view?usp=sharing)
     Used for cross-domain validation

Technologies Used
  Python
  Pandas
  Scikit-learn
  SentenceTransformers
  Hugging Face Datasets
  UMAP

How to Run
# Install dependencies
pip install pandas scikit-learn sentence-transformers datasets umap-learn
# Run your notebook / script
python main.py


Evaluation
  Cosine similarity for retrieval
  Keyword overlap validation
  Clustering coherence (qualitative analysis)
  Comparison between baseline and DAERM


Contributions
  Introduced DAERM for legal similarity
  Metadata selection using Mutual Information
  Cross-dataset validation (Brazil + India)


License
  This project is for academic and research purposes.

Authors
  Natra Charan
  N.Harshith Varma
  M.Likhith Reddy
  BTPR.Nikhil


