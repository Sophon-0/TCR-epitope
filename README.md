# TCR-epitope binding prediction with pLM embeddings

This notebook uses the MixTCRpred dataset with a "Leave One Epitope Out" cross-validation strategy. For each epitope, both the epitope and its associated TCR sequences are unseen during the model's training phase.

Input Features:

  - Epitope and TCR: pLM embeddings generated using either the 'esm3-small-2024-08' or 'esm2_t6_8M_UR50D' ESM models.
  - VJ genes: Encoded as categorical variables for the TCR
  - HLA and species information: Encoded as categorical variables for the epitope.

Negative Sampling: 

  - Artificial negative samples (non-binding TCR-epitope pairs) are created using a random shuffling strategy to balance the dataset with negative / positive ratio of 5.
  - Max positive cases in test set is set at 1000, since there might not be enough TCR sequences for a ratio of 5.

Finetuning is done using: 

  - Logistic Regression, Random Forest, Multi-layer Perceptron

Evaluation: 

  - Model performance is assessed using the Area Under the ROC Curve (AUC) metric, computed for each epitope individually.

