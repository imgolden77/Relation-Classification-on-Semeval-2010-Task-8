# Relation-Classification-on-Semeval-2010-Task-8

This repository compares the performance of DeBERTa (Transformer-based) and a BiLSTM (recurrent) model on the SemEval-2010 Task 8 relation classification dataset. It contains Jupyter notebooks for training and inference for both model types, helper notes, and dependency specifications. 

## Summary
NLP Group project contributor: Juha Im, Abhishek Das, Nazrin Babayeva
•	Investigated the comparative effectiveness of DeBERTa (transformer-based) and BiLSTM (recurrent model).
•	Implemented an entity-aware representation strategy (RDEBERTa) achieving an F1-score of 0.80 
•	Developed Attention based BiLSTM with pretrained word embedding, resulting in a 67.5% increase in F1 score.

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

## Results and logs
• Training metrics (loss, accuracy, F1) and evaluation outputs are recorded in notebook cells. Check the output cells in each notebook for experiment logs.

## Environment
• Dev container: Ubuntu 24.04.2 LTS
• Notebooks can be run in Colab if GPU acceleration is needed.

## Contributing
• Fork the repository, update notebooks or requirements, and submit a pull request.

## License
• No license is specified. Use for research or personal experimentation unless otherwise noted.
