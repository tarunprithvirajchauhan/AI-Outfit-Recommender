# Project Requirements

## 1. Problem statement

The AI Outfit Recommender will analyze clothing items supplied by a user and recommend compatible outfit combinations from the user's own wardrobe. The system will optionally use a user-provided photograph for additional personalization and can recommend complementary accessories.

## 2. Primary users

- Male users
- Female users

The recommendation engine should use a shared representation of clothing rather than maintaining completely separate recommendation systems.

## 3. MVP inputs

### Required

- Multiple top-wear images
- Multiple bottom-wear images

### Optional

- User photograph
- Occasion
- Preferred style
- Season/weather context

## 4. MVP outputs

For each recommended outfit:

- Selected top
- Selected bottom
- Compatibility score
- Rank/order among recommendations

## 5. Advanced outputs

- Watch recommendation
- Bracelet recommendation
- Ring recommendation
- Chain recommendation
- Sunglasses recommendation
- Personalized recommendations using user photo
- Occasion-aware recommendations
- Weather-aware recommendations

## 6. Initial clothing categories

### Tops

- T-shirt
- Shirt
- Kurta/Kurti
- Hoodie

### Bottoms

- Jeans
- Cargo
- Trousers
- Chinos

These categories are intentionally limited for the first model iteration and can be expanded later.

## 7. Functional requirements

### FR-01 Clothing input
The system shall accept multiple clothing images from a user.

### FR-02 Clothing analysis
The system shall identify the category of a clothing item and eventually extract useful visual attributes.

### FR-03 Candidate generation
The system shall generate valid combinations of supplied top and bottom items.

### FR-04 Compatibility scoring
The system shall assign a compatibility score to candidate outfits.

### FR-05 Ranking
The system shall rank candidate outfits according to their compatibility scores.

### FR-06 Recommendations
The system shall return the highest-ranked outfit combinations.

### FR-07 Optional personalization
The system may use a user photograph for additional personalization when supplied.

### FR-08 Accessories
The system may recommend complementary accessories for a selected outfit.

## 8. Non-functional requirements

- Modular architecture
- Reproducible experiments
- Version-controlled code
- Clear separation between training and inference
- Model evaluation using defined metrics
- API-ready inference pipeline
