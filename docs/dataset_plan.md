# Dataset Plan

## Dataset goals

The project requires data for multiple tasks rather than one single dataset.

### Task 1: Clothing recognition

Need images with clothing categories and, where possible, attributes.

Candidate sources to investigate in M1:

- DeepFashion
- Fashion-MNIST for initial pipeline experiments only

### Task 2: Outfit compatibility

Need examples of clothing items that occur together in complete outfits.

Candidate source to investigate:

- Polyvore / Polyvore Outfits and related fashion compatibility research datasets

### Task 3: Accessories

A smaller curated/custom dataset can be considered later.

## Initial classes

T-shirt, Shirt, Kurta/Kurti, Hoodie, Jeans, Cargo, Trousers, Chinos.

## Data split

Initial target:

- Training: 70%
- Validation: 15%
- Test: 15%

The exact split will be revised if the selected dataset already provides official splits.

## Important data concerns

- Duplicate images
- Broken images
- Class imbalance
- Data leakage between train and test
- Licensing / usage restrictions
- Different image resolutions
- Background variation
- Clothing occlusion
