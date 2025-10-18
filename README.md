# Relation Extraction Using BiLSTM and DeBERTa

## 📝 Project Summary
Contributors: Juha Im, Abhishek Das, Nazrin Babayeva

This project investigates and compares the performance of two distinct deep learning architectures, **DeBERTa (Transformer-based)** and **Attention-based BiLSTM (Recurrent)**, for the task of **Relation Extraction (RE)**. The goal is to classify semantic relationships between pairs of nominals within text. The comparative analysis provides insight into the suitability of transformer versus recurrent architectures for structured information retrieval in NLP.

## 🎯 Task & Dataset

### Relation Extraction (RE)
Relation Extraction is an NLP process that involves identifying and classifying relationships between entities in a text. This is crucial for tasks like knowledge graph construction and information retrieval. The focus of this work is classifying nine specific semantic relations between pairs of nominals, such as *Cause-Effect* and *Product-Producer*.

### Dataset: Semeval-2010 Task 8
* **Purpose:** Multi-way classification of semantic relations between pairs of nominals.
* **Size:** The dataset contains 8,000 training examples and 2,717 test examples.
* **Benchmark:** It is a standard benchmark used widely in the NLP community for relation classification.
* **Relation Types:** Covers 19 types of relations, including the nine core semantic relations. The most frequent relation is **Other** (17.4%), followed by **Cause-Effect** (12.4%) and **Component-Whole** (11.7%).

## 🧠 Methodology & Models

We implemented two primary models to test the effect of the presence or absence of a transformer architecture.

### 1. RDEBERTa (Transformer-Based Approach)
* **Base Model:** **DeBERTa** (Decoding-enhanced BERT with Disentangled Attention), an improvement over BERT and RoBERTa.
* **Customization:** Customized using an **entity-aware representation strategy** inspired by the RBERT framework.
* **Feature Vector:** The final representation for classification is formed by concatenating the **\[CLS] token representation** with the **contextualized representations of both entity mentions** (obtained by averaging attention outputs).
* **Hyperparameters:**
    * Learning Rate: $2e^{-5}$ 
    * Dropout: 0.1 
    * Epochs: 7
    * Batch Size: 32

### 2. Attention-Based BiLSTM (Recurrent Approach)
* **Architecture:** A **Bidirectional Long Short-Term Memory (BiLSTM)** with an attention mechanism.
* **Unique Structure:** It uses an **asymmetrical BiLSTM structure** where the backward LSTM has prior knowledge of the first half of the sentence, allowing it to leverage additional contextual information.
* **Embeddings:** Integrated **GloVe 300-dimensional pre-trained embeddings** to enhance semantic understanding.
* **Mechanism:** Attention mechanisms assign weights to LSTM outputs, allowing the model to focus on the most informative words for classification.

## 📈 Results and Performance

The models were evaluated using the **F1-score**, which is the official metric for SemEval-2010 Task 8 and is effective for imbalanced data.

| Model | Key Feature | Final F1-Score |
| :--- | :--- | :--- |
| **RDEBERTa** | Concatenated \[CLS] token with two entity representations| **0.80**|
| **Attention-BiLSTM** | BiLSTM with Attention & GloVe 300-D embeddings| **0.67** |

### Comparative Insights
* **Performance:** The **RDEBERTa** implementation (F1: 0.80) significantly outperformed the best **Attention-BiLSTM** model (F1: 0.67).
* **Computational Cost:** The **Attention-BiLSTM** model's training time was observed to be **three times longer** than the DeBERTa model.
* **Strengths (DeBERTa):** Excels in performance and uses a disentangled attention mechanism for sophisticated contextual representations.
* **Weaknesses (DeBERTa):** Large-scale model, requiring significant computational resources and memory for training and inference.

## Repository structure
• [DeBERTa_Training.ipynb](DeBERTa_Training.ipynb) — DeBERTa training and evaluation experiments
• [DeBERTa_Inference.ipynb](DeBERTa_Inference.ipynb) — Tokenization, data parsing and inference for DeBERTa  
  - key symbols: [`parse_data`](DeBERTa_Inference.ipynb), [`tokenizer`](DeBERTa_Inference.ipynb)
• [LSTM_Training.ipynb](LSTM_Training.ipynb) — BiLSTM training and evaluation experiments  
  - key symbol: [`label_map`](LSTM_Training.ipynb)
• [LSTM_Inference.ipynb](LSTM_Inference.ipynb) — Data parsing and GloVe embedding loading for BiLSTM  
  - key symbols: [`parse_data`](LSTM_Inference.ipynb), [`load_glove_embeddings`](LSTM_Inference.ipynb)
• [requirements.txt](requirements.txt) — Python package dependencies
• [readme.txt](readme.txt) — external resources and notes
• [README.md](README.md) — this file

## Quick start
1. Install dependencies:
```sh
pip install -r [requirements.txt](requirements.txt)
```
2. Open notebooks (Jupyter Lab/Notebook):
```sh
jupyter lab
# or
jupyter notebook
```
3. Follow the notebooks in the order:
   - Data parsing & preprocessing (see [`parse_data`](DeBERTa_Inference.ipynb) and [`parse_data`](LSTM_Inference.ipynb))
   - Prepare dataloaders/inputs
   - Train and evaluate using the training notebooks
   - Run inference notebooks for predictions

## Notes
• Each notebook includes sections for data parsing, preprocessing, dataloader construction, training, and evaluation.
• The DeBERTa notebooks include tokenizer customization and entity-marker handling (`[`tokenizer`](DeBERTa_Inference.ipynb)`).
• The LSTM notebooks include an example of loading pretrained GloVe embeddings (`[`load_glove_embeddings`](LSTM_Inference.ipynb)`).
