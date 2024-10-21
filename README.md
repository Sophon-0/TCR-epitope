# TCR-epitope binding affinity prediction

Data: 

  - The notebook uses the MixTCRpred dataset and focuses on a "Leave One Epitope Out" cross-validation strategy. This means that for each epitope, both the epitope and its associated TCR sequences are unseen during the model's training phase.

Input Features:

  - Epitope and TCR Embeddings: Generated using either the 'esm3-small-2024-08' or 'esm2_t6_8M_UR50D' ESM models.
  - TCR VJ genes: Encoded as categorical variables.
  - HLA and species information: Encoded as categorical variables for the epitope.

Negative Sampling: 

  - Artificial negative samples (non-binding TCR-epitope pairs) are created using a random shuffling strategy to balance the dataset. Computationally generated negative / positive ratio set at 5. Max positive cases in test set is set at 1000, since there might not be enough TCR sequences for a ratio of 5.

Machine Learning Models: finetuning is done using: 

  - Logistic Regression, Random Forest, Multi-layer Perceptron

Evaluation: 

  - Model performance is assessed using the Area Under the ROC Curve (AUC) metric, computed for each epitope individually.

