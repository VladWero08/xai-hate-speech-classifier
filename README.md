# xai-hate-speech-classifier

This repository contains the notebooks for experiments involved in trying to **explain the decisions made by a transformer-based model** trained for Hate Speech classification on *five hate speech categories*: sexuality, origin, gender, religion, and race. The project was developed during my 2nd year of *MSc in Artificial Intelligence at the Faculty of Mathematics and Computer Science, University of Bucharest*. 

## Dataset
- **huggingface:** [ucberkeley-dlab/measuring-hate-speech](https://huggingface.co/datasets/ucberkeley-dlab/measuring-hate-speech)
- 501 English Hate Speech comments
- 5 categories: sexuality, origin, gender, religion, race

## Explainable Features
Multiple explainability features were used to assess the importance of the tokens, and they are: attention weights, LIME, and SHAP scores. For attention weights, each hate speech comment was classified by the [roberta-hate-speech-dynabench-r4-target](https://huggingface.co/facebook/roberta-hate-speech-dynabench-r4-target) model, and the attention was extracted from all the attention heads of the last 4 layers. 

Each explainability feature was normalized per sample to represent a probability distribution of importance for each token. Different measurements were made on these probability distributions: entropy, Gini, and top-5 mass. Moreover, the features were compared between them using ranking methods to see how much they agree on token importance: Spearman, Kendall Tau, and Jaccard intersection.

## Adversarial Examples

After assessing the importance of each token, from each comment, the top-5 tokens were *substituted* based on their importance with semantically similar synonyms, and again, the metrics presented in the previous section were computed for the adversarial examples. More details can be found in the [documentation](https://github.com/VladWero08/xai-hate-speech-classifier/blob/main/documentation/xAI%20in%20Hate%20Speech%20Classifier.pdf).
