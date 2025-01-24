# LoRA vs Full Fine-tuning: An Illusion of Equivalence

This repository contains our implementation of the paper *"LoRA vs Full Fine-tuning: An Illusion of Equivalence."* We explored the differences between LoRA (Low-Rank Adaptation) and full fine-tuning by analyzing the singular vectors of weight matrices during fine-tuning.

## What We Did
- **Singular Vector Extraction**: We extracted singular vectors from the query and value weights of both the base model (`W_0`) and the fine-tuned model (`W_tuned`) across all layers, as LoRA specifically modifies these weights.
- **Similarity Matrices**: We created similarity matrices to compare the singular vectors of the base and fine-tuned models.
- **Intruder Dimensions**: From these similarity matrices, we identified intruder dimensions. According to the paper, a singular vector \( y_j \) from \( W_{\text{tuned}} \) is an intruder dimension if and only if:
  \[
  \max_i \left( \cos(y_j, x_i) \right) < \epsilon
  \]
  where \( \epsilon \) is a similarity threshold, and \( x_i \) is a singular vector in \( W_0 \).
- **Visualization**: We visualized the similarity matrices and found that our plots closely resemble those in the paper, providing additional insights into the dimensionality differences introduced by LoRA versus full fine-tuning.

## Repository Overview
- **Code**: Includes scripts for extracting singular vectors, creating similarity matrices, and identifying intruder dimensions.
- **Plots**: Generated visualizations of similarity matrices and intruder dimension counts across layers.
- **Reproducibility**: The results align closely with the findings in the paper.

This repository provides a detailed look into how fine-tuning methods impact the structure of weight matrices, highlighting the subtleties of LoRA’s low-rank updates.

---
Let us know if you find this useful or have any questions!
