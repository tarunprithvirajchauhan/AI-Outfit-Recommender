# System Architecture

## High-level pipeline

```text
User
  |
  v
Wardrobe Upload
  |
  v
Image Preprocessing
  |
  v
Clothing Analysis
  |----> Category
  |----> Color
  |----> Pattern / Fit / Style
  |
  v
Visual Feature / Embedding Generation
  |
  v
Candidate Outfit Generation
  |
  v
Compatibility Model
  |
  v
Ranking Engine
  |
  +--------------------+
  |                    |
  v                    v
Accessory Engine    Personalization
  |                    |
  +---------+----------+
            |
            v
   Final Recommendations
```

## Core ML pipeline

```text
Top image       Bottom image
    |               |
    v               v
Vision encoder  Vision encoder
    |               |
    v               v
Top embedding   Bottom embedding
    \               /
     \             /
      v           v
       Compatibility model
               |
               v
       Compatibility score
```

## Training vs inference

### Training

```text
Dataset -> preprocessing -> model training -> validation -> trained model
```

### Inference

```text
User image -> preprocessing -> trained model -> prediction
```

The website will eventually communicate with the trained inference pipeline through a backend API.
