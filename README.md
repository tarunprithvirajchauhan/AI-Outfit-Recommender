# AI Outfit Recommender

An AI-powered fashion recommendation system that analyzes a user's wardrobe, evaluates clothing compatibility, ranks outfit combinations, and optionally recommends accessories and personalized outfits using a user photo.

## Current milestone

**M0 - Project Definition & Architecture**

The current version is the project foundation. No ML model is trained yet.

## MVP

1. Accept multiple top-wear images.
2. Accept multiple bottom-wear images.
3. Analyze clothing categories and attributes.
4. Generate all top-bottom combinations.
5. Score outfit compatibility.
6. Rank and return the best outfit combinations.

## Advanced features

- Accessories recommendation
- Optional user-photo personalization
- Occasion-aware recommendations
- Weather-aware recommendations
- User feedback and preference learning

## Planned stack

- Python
- PyTorch
- OpenCV
- NumPy / Pandas
- scikit-learn
- FastAPI
- React
- PostgreSQL
- Git / GitHub

## Project structure

```text
AI-Outfit-Recommender/
├── data/
│   ├── raw/
│   └── processed/
├── docs/
├── models/
├── notebooks/
├── src/
│   ├── api/
│   ├── data/
│   ├── embeddings/
│   ├── recommendation/
│   └── vision/
├── tests/
├── .gitignore
├── README.md
└── requirements.txt
```

## Milestones

- [x] M0 - Project definition & architecture
- [ ] M1 - Dataset collection & preparation
- [ ] M2 - Clothing classification
- [ ] M3 - Attribute extraction
- [ ] M4 - Clothing embeddings
- [ ] M5 - Outfit compatibility model
- [ ] M6 - Wardrobe recommendation engine
- [ ] M7 - Accessory recommendation
- [ ] M8 - User-photo personalization
- [ ] M9 - Context-aware recommendation
- [ ] M10 - Feedback learning
- [ ] M11 - Backend API
- [ ] M12 - Website
- [ ] M13 - Deployment

## Status

M0 foundation created. Next: M1 dataset research and preparation.
