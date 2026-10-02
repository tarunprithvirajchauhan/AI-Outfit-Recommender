# Model Plan

## M2 - Clothing classification

Start with transfer learning rather than training a CNN from scratch.

Candidate models to compare:

- ResNet
- EfficientNet
- Vision Transformer family

## M3 - Attribute extraction

Possible approaches:

- Multi-label classification
- Pretrained vision models
- Classical color analysis for dominant color

Target attributes:

- Category
- Color
- Pattern
- Fit
- Style
- Formality

## M4 - Embeddings

Investigate pretrained visual encoders such as CLIP and modern vision encoders.

Goal:

```text
clothing image -> embedding vector
```

## M5 - Compatibility

Initial baseline:

```text
Top embedding + Bottom embedding
            -> MLP
            -> compatibility score
```

Later experiments may include:

- Siamese networks
- Triplet learning
- Contrastive learning
- Transformer-based fashion compatibility models

## M6 - Recommendation

Generate candidate combinations, score them, then rank them.

Example:

```text
10 tops x 12 bottoms = 120 candidates
                  |
                  v
          compatibility scores
                  |
                  v
              ranking
                  |
                  v
             top K outfits
```

## Evaluation

Classification:

- Accuracy
- Precision
- Recall
- F1

Compatibility:

- ROC-AUC / PR-AUC where appropriate
- F1

Recommendation:

- Precision@K
- Recall@K
- NDCG@K
- Hit Rate@K
