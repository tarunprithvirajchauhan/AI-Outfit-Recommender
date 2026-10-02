# AI Outfit Recommender - Input/Output Design

## 1. Purpose

This document defines exactly what information enters the AI Outfit
Recommender, how that information is represented internally, and what
the system returns.

The design separates: - User inputs - Image preprocessing - Clothing
item representation - Recommendation request - Recommendation response

------------------------------------------------------------------------

## 2. User Input Types

The system has three categories of inputs.

### 2.1 Wardrobe Inputs - Required

The user provides one or more clothing images.

They are divided into:

``` text
Top Wear
Bottom Wear
```

Example:

``` text
tops/
    shirt_01.jpg
    shirt_02.jpg
    tshirt_01.jpg

bottoms/
    jeans_01.jpg
    cargo_01.jpg
    trouser_01.jpg
```

A wardrobe may contain multiple items in each category.

------------------------------------------------------------------------

### 2.2 User Photograph - Optional

The user may upload a photograph of themselves.

Example:

``` text
user_photo.jpg
```

The photo is not required for the basic recommendation pipeline.

Without a photo: - The system produces wardrobe-based recommendations.

With a photo: - The system may use additional visual information for
personalization.

------------------------------------------------------------------------

### 2.3 Context Inputs - Optional

Future versions may accept:

``` text
Gender
Occasion
Preferred style
Weather
Season
Time of day
```

These inputs should be optional so that the core recommendation system
remains usable without them.

------------------------------------------------------------------------

## 3. Individual Clothing Item Representation

After an image is uploaded, the system should internally represent it as
a clothing item.

Conceptually:

``` json
{
  "item_id": "top_001",
  "image_path": "tops/shirt_01.jpg",
  "category": "shirt",
  "gender_group": "male",
  "attributes": {
    "color": "white",
    "pattern": "striped",
    "fit": "regular",
    "style": "casual"
  }
}
```

The exact attributes will depend on what the final models can reliably
extract.

------------------------------------------------------------------------

## 4. Clothing Image Input Requirements

The initial system should accept common image formats:

-   JPG/JPEG
-   PNG
-   WEBP

The preprocessing stage should eventually handle:

``` text
Image
 ↓
Format validation
 ↓
Resize
 ↓
Normalization
 ↓
Optional background processing
 ↓
Model input
```

The user should receive a clear error if an unsupported or corrupted
image is supplied.

------------------------------------------------------------------------

## 5. Wardrobe Data Structure

The complete wardrobe can conceptually be represented as:

``` json
{
  "tops": [
    {
      "item_id": "top_001",
      "image_path": "tops/shirt_01.jpg"
    },
    {
      "item_id": "top_002",
      "image_path": "tops/tshirt_01.jpg"
    }
  ],
  "bottoms": [
    {
      "item_id": "bottom_001",
      "image_path": "bottoms/jeans_01.jpg"
    },
    {
      "item_id": "bottom_002",
      "image_path": "bottoms/cargo_01.jpg"
    }
  ]
}
```

This is a conceptual schema. The final implementation may use Python
objects, database records, or API request models.

------------------------------------------------------------------------

## 6. Recommendation Request

After the wardrobe has been analyzed, the recommendation engine should
receive a request conceptually similar to:

``` json
{
  "tops": ["top_001", "top_002"],
  "bottoms": ["bottom_001", "bottom_002"],
  "user_photo": null,
  "context": {
    "occasion": null,
    "style": null,
    "weather": null
  },
  "number_of_recommendations": 5
}
```

The important point is that the recommendation engine works with
identified clothing items rather than repeatedly processing raw images.

------------------------------------------------------------------------

## 7. Candidate Generation

If the user provides:

``` text
10 tops
12 bottoms
```

the candidate generator creates:

\[ 10 `\times 12`{=tex} = 120 \]

top-bottom combinations.

Conceptually:

``` text
Top 1 + Bottom 1
Top 1 + Bottom 2
...
Top 10 + Bottom 12
```

Each combination becomes a candidate outfit.

------------------------------------------------------------------------

## 8. Candidate Outfit Representation

Each candidate can conceptually be represented as:

``` json
{
  "candidate_id": "outfit_001",
  "top_id": "top_001",
  "bottom_id": "bottom_004"
}
```

After model evaluation:

``` json
{
  "candidate_id": "outfit_001",
  "top_id": "top_001",
  "bottom_id": "bottom_004",
  "compatibility_score": 0.92
}
```

The compatibility score is a model output. Its exact meaning and
calibration will be defined during model development.

------------------------------------------------------------------------

## 9. Ranking Flow

The recommendation pipeline should work conceptually as:

``` text
Wardrobe
   ↓
Analyze clothing
   ↓
Generate candidates
   ↓
Evaluate compatibility
   ↓
Assign scores
   ↓
Sort/rank candidates
   ↓
Select Top-K
```

For example:

``` text
Candidate A → 0.92
Candidate B → 0.71
Candidate C → 0.88
Candidate D → 0.95

Ranking:

1. Candidate D → 0.95
2. Candidate A → 0.92
3. Candidate C → 0.88
4. Candidate B → 0.71
```

The actual recommendation system should later consider diversity so that
the Top-K results are not nearly identical.

------------------------------------------------------------------------

## 10. Final Recommendation Output

The API should eventually return structured information similar to:

``` json
{
  "recommendations": [
    {
      "rank": 1,
      "top_id": "top_004",
      "bottom_id": "bottom_003",
      "compatibility_score": 0.95
    },
    {
      "rank": 2,
      "top_id": "top_001",
      "bottom_id": "bottom_005",
      "compatibility_score": 0.92
    }
  ]
}
```

The website can then use these IDs to display the corresponding clothing
images.

------------------------------------------------------------------------

## 11. Accessory Output

Accessories are an additional recommendation layer.

Conceptually:

``` json
{
  "outfit": {
    "top_id": "top_004",
    "bottom_id": "bottom_003"
  },
  "accessories": {
    "watch": "silver",
    "bracelet": "minimal",
    "ring": "silver",
    "chain": "thin silver"
  }
}
```

Accessory recommendation will initially be separate from the core
compatibility model.

------------------------------------------------------------------------

## 12. Personalized Recommendation Flow

When a user photo is not provided:

``` text
Wardrobe
   ↓
Clothing analysis
   ↓
Compatibility
   ↓
Ranking
   ↓
Recommendations
```

When a user photo is provided:

``` text
Wardrobe ───────────────┐
                        ↓
                 Base Recommendation
                        ↑
User Photo → Personalization Features
                        │
                        ↓
                 Personalized Ranking
                        ↓
                 Recommendations
```

The exact personalization model will be decided later.

------------------------------------------------------------------------

## 13. Invalid Input Handling

The system should handle cases such as:

### Unsupported file

``` text
Error:
Unsupported image format.
Please upload JPG, PNG, or WEBP.
```

### Corrupted image

``` text
Error:
The uploaded image could not be processed.
```

### No tops

``` text
Error:
Please provide at least one top-wear item.
```

### No bottoms

``` text
Error:
Please provide at least one bottom-wear item.
```

### Too many images

A configurable maximum should eventually be defined based on performance
testing.

------------------------------------------------------------------------

## 14. Data Flow Summary

The complete MVP data flow is:

``` text
USER
 │
 ├── Top images ─────────────┐
 │                           │
 ├── Bottom images ──────────┤
 │                           ▼
 └── Optional photo     INPUT VALIDATION
                              │
                              ▼
                       IMAGE PREPROCESSING
                              │
                              ▼
                      CLOTHING ANALYSIS
                              │
                              ▼
                      FEATURE EXTRACTION
                              │
                              ▼
                         EMBEDDINGS
                              │
                              ▼
                    CANDIDATE GENERATION
                              │
                              ▼
                   COMPATIBILITY MODEL
                              │
                              ▼
                          RANKING
                              │
                    ┌─────────┴─────────┐
                    ▼                   ▼
              Accessories        Personalization
                    │                   │
                    └─────────┬─────────┘
                              ▼
                    FINAL RECOMMENDATIONS
                              │
                              ▼
                           WEBSITE
```

------------------------------------------------------------------------

## 15. Important Design Principle

Raw images should not be passed through every component repeatedly.

Instead:

``` text
Raw Image
    ↓
Analysis
    ↓
Structured Clothing Item
    ↓
Embedding
    ↓
Reusable Representation
```

This makes the eventual system more efficient and easier to maintain.

------------------------------------------------------------------------

## 16. M0.3 Completion Criteria

M0.3 is complete when:

-   Required inputs are defined.
-   Optional inputs are defined.
-   Clothing item representation is defined.
-   Wardrobe structure is defined.
-   Candidate generation is defined.
-   Compatibility output is defined.
-   Ranking flow is defined.
-   Final recommendation format is defined.
-   Accessory output is defined.
-   Personalization flow is defined.
-   Invalid input cases are identified.
-   Complete data flow is documented.
