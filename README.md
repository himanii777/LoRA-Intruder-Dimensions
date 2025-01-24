# LoRA vs Full Fine-tuning: An Illusion of Equivalence

This repository contains our implementation of the paper *"LoRA vs Full Fine-tuning: An Illusion of Equivalence"* (link=https://arxiv.org/abs/2410.21228). 

## What We Did
- **Singular Vector Extraction**: We extracted singular vectors from the query and value weights of both the base model (`W_0`) and the fine-tuned model (`W_tuned`) across all layers, as LoRA specifically modifies these weights.
- **Similarity Matrices**: We created similarity matrices to compare the singular vectors of the base and fine-tuned models.
- **Intruder Dimensions**: From these similarity matrices, we identified intruder dimensions. According to the paper, a singular vector \( y_j \) from W_tuned is an intruder dimension if and only if:
  \[
  max_i(cos(y_j, x_i)) < epsilon
  \]
  where epsilon is a similarity threshold, and \( x_i \) is a singular vector in W_0. For our experiment, we set epsilon to 0.6.
- **Visualization**: We visualized the similarity matrices and found that our plots closely resemble those in the paper, providing additional insights into the dimensionality differences introduced by LoRA versus full fine-tuning.

## Repository Overview
- **Code**: Includes scripts for extracting singular vectors, creating similarity matrices, and identifying intruder dimensions. We used Roberta as a base model and finetuned it for Mnli task.
- **Plots**: Generated visualizations of similarity matrices and intruder dimension counts across layers.
- **Reproducibility**: The results align closely with the findings in the paper.

Some of the similar matrices plot we retrieved were:

<img width="479" alt="image" src="https://github.com/user-attachments/assets/d6d769b7-f4a4-4afb-9aa7-13d7b84de7d5" />

**Figure: Similarity matrix plot for layer 4 query weights (rank = 64)**

<img width="469" alt="image" src="https://github.com/user-attachments/assets/32f8c5bf-9558-4f65-a2b2-d24fb191de66" />

**Figure: Similarity matrix plot for layer 4 query weights (rank = 128)**

<img width="467" alt="image" src="https://github.com/user-attachments/assets/7bebf78a-cbe5-40a5-a0d6-fcfc7026c6b7" />

**Figure: Similarity matrix plot for layer 4 query weights (rank = 256)**

Similarly, we also plotted the number of intruder dimensions per each experiment(increasing ranks). The number of intruder dimensions were similar in each experiment. 

![image](https://github.com/user-attachments/assets/6844e560-107d-41f6-9a64-e89afd0f779b)

**Figure: Number of Intruder dimensions in each layer (rank=64)**









