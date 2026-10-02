# AI Outfit Recommender
## ML Pipeline - M0.5

### 1. Purpose

This document defines the machine learning pipeline of the AI Outfit Recommender. It explains how clothing images are processed and converted into final outfit recommendations.

---

## 2. Overall Pipeline

```text
User uploads clothing images
          ↓
    Image Preprocessing
          ↓
  Clothing Classification
          ↓
  Attribute Extraction
          ↓
   Image Embedding
          ↓
 Generate Outfit Pairs
          ↓
 Compatibility Model
          ↓
   Compatibility Score
          ↓
      Ranking
          ↓
 Top Outfit Recommendations
```

---

## 3. Pipeline Stages

### 3.1 Image Preprocessing

The uploaded clothing images are prepared before being given to machine learning models.

Main operations may include:

- Image format validation
- Image resizing
- Pixel normalization
- Basic image quality checks
- Optional background/cropping processing

**Input:** Raw clothing image

**Output:** Preprocessed image

---

### 3.2 Clothing Classification

The classification model identifies the category of the clothing item.

Examples:

```text
Image → Shirt
Image → T-shirt
Image → Kurta
Image → Jeans
Image → Cargo
Image → Trousers
```

This is an ML task.

**Input:** Preprocessed clothing image

**Output:** Clothing category and confidence score

---

### 3.3 Attribute Extraction

The system identifies useful visual properties of the clothing item.

Possible attributes include:

- Color
- Pattern
- Fit
- Style
- Sleeve type
- Material, where applicable

Example:

```text
Category → Shirt
Color → White
Pattern → Striped
Fit → Regular
Style → Casual
```

These attributes can later be used by the compatibility and recommendation systems.

**Input:** Clothing image and/or extracted visual representation

**Output:** Structured clothing attributes

---

### 3.4 Image Embedding

A vision model converts the clothing image into a numerical vector called an embedding.

Example:

```text
Clothing Image
      ↓
Vision Encoder
      ↓
[0.21, -0.43, 0.78, 0.12, ...]
```

The embedding represents useful visual information about the clothing item.

Embeddings allow the system to compare clothing items mathematically.

**Input:** Preprocessed image

**Output:** Clothing embedding vector

The exact embedding model will be selected after dataset and model analysis.

---

### 3.5 Candidate Generation

The system creates possible top-bottom combinations.

For example:

```text
10 Tops × 12 Bottoms = 120 combinations
```

This stage mainly uses normal programming logic rather than machine learning.

**Input:** Available tops and bottoms

**Output:** Candidate outfit pairs

Example:

```text
Candidate 1 → Top 1 + Bottom 1
Candidate 2 → Top 1 + Bottom 2
Candidate 3 → Top 2 + Bottom 1
...
```

---

### 3.6 Compatibility Model

The compatibility model estimates how well a top and bottom work together.

Conceptually:

```text
Top Embedding
      +
Bottom Embedding
      ↓
Compatibility Model
      ↓
Compatibility Score
```

Example:

```text
White Shirt + Blue Jeans → 0.87
Red Shirt + Green Cargo → 0.42
```

The model will learn compatibility patterns from suitable outfit datasets.

This is one of the core ML components of the project.

**Input:** Top and bottom representations

**Output:** Compatibility score

---

### 3.7 Ranking

All candidate outfits are sorted according to their compatibility scores.

Example:

```text
Outfit C → 0.94
Outfit A → 0.87
Outfit B → 0.72
Outfit D → 0.65
```

The system then selects the required number of top recommendations.

Ranking is primarily a recommendation-engine operation and does not necessarily require a separate ML model.

---

## 4. ML Components vs Programming Logic

### Machine Learning Components

```text
Classification Model
Attribute Extraction Model/Method
Embedding Model
Compatibility Model
```

### Normal Programming / Recommendation Logic

```text
Image validation
Candidate generation
Filtering
Ranking
Result formatting
API handling
```

The entire application should not be called "the model". The models are individual components inside the complete recommendation system.

---

## 5. Training Pipeline

Training happens before the model is used by the website.

```text
Dataset
   ↓
Data Preprocessing
   ↓
Train / Validation / Test Split
   ↓
Model Training
   ↓
Validation
   ↓
Evaluation
   ↓
Best Model
   ↓
Save Model
```

The trained models are then used during inference.

---

## 6. Inference Pipeline

Inference means using the trained models to process a user's new input.

```text
User Image
    ↓
Preprocessing
    ↓
Trained Models
    ↓
Clothing Information
    ↓
Embeddings
    ↓
Candidate Outfits
    ↓
Compatibility Scores
    ↓
Ranking
    ↓
Recommendations
```

Training and inference are therefore different processes:

- **Training:** The model learns from existing data.
- **Inference:** The trained model makes predictions on new user data.

---

## 7. Future Extensions

The initial MVP focuses on top-bottom outfit compatibility.

Later, the pipeline can be extended with:

```text
User Photo
    ↓
Personalization

Occasion
Weather
Season
Time
    ↓
Context-aware Recommendation

Accessories
    ↓
Accessory Recommendation

User Feedback
    ↓
Personalized Learning
```

These features will be added after the core recommendation pipeline works reliably.

---

## 8. Important Design Principle

The system should avoid repeatedly processing the same raw images.

Whenever practical:

```text
Raw Image
   ↓
Process Once
   ↓
Structured Attributes + Embedding
   ↓
Reuse During Recommendation
```

This can reduce unnecessary computation and improve response time.

---

## 9. Current Scope

The M0.5 pipeline defines the architecture and data flow only.

The exact:

- Dataset
- Classification model
- Attribute extraction method
- Embedding model
- Compatibility model
- Hyperparameters

will be selected in later milestones after dataset and model analysis.

---

## 10. M0.5 Summary

The complete MVP pipeline is:

```text
Image
  ↓
Preprocessing
  ↓
Classification
  ↓
Attributes
  ↓
Embedding
  ↓
Candidate Generation
  ↓
Compatibility Prediction
  ↓
Ranking
  ↓
Top Outfit Recommendations
```

This pipeline forms the ML foundation of the AI Outfit Recommender.
