# AI Outfit Recommender
## Project Structure - M0.7

### 1. Purpose

This document defines the folder and file organization of the AI Outfit Recommender project.

The structure is designed to keep datasets, machine learning models, source code, tests, experiments, and documentation separated and easy to maintain.

---

## 2. Project Structure

```text
AI-Outfit-Recommender/
│
├── .venv/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
│
├── models/
│
├── notebooks/
│
├── src/
│   ├── vision/
│   ├── embeddings/
│   ├── recommendation/
│   ├── personalization/
│   ├── api/
│   └── config.py
│
├── tests/
│
├── docs/
│
├── .gitignore
├── README.md
└── requirements.txt
```

---

## 3. Folder Responsibilities

### 3.1 `.venv/`

Contains the Python virtual environment used by the project.

It contains the project's installed Python packages and environment configuration.

This folder should not be committed to GitHub.

---

### 3.2 `data/`

Contains datasets used by the project.

```text
data/
├── raw/
├── processed/
└── external/
```

- `raw/` → Original datasets without modification.
- `processed/` → Cleaned and prepared datasets.
- `external/` → External/reference data that may be used by the project.

---

### 3.3 `models/`

Contains trained and saved machine learning models.

Possible future files include:

```text
classifier.pt
embedding_model.pt
compatibility_model.pt
```

The exact model files will be created after the corresponding models are developed.

---

### 3.4 `notebooks/`

Contains Jupyter notebooks used for:

- Dataset exploration
- Data analysis
- Experiments
- Visualization
- Model experimentation

Notebooks are mainly for experimentation. The reusable application code should eventually be placed inside `src/`.

---

### 3.5 `src/`

Contains the main source code of the project.

```text
src/
├── vision/
├── embeddings/
├── recommendation/
├── personalization/
├── api/
└── config.py
```

#### `vision/`

Responsible for:

- Image preprocessing
- Clothing classification
- Attribute extraction

#### `embeddings/`

Responsible for:

- Loading the embedding model
- Generating clothing embeddings
- Embedding-related operations

#### `recommendation/`

Responsible for:

- Candidate generation
- Compatibility prediction
- Ranking
- Accessory recommendation

#### `personalization/`

Responsible for features related to user-specific recommendations.

This will be developed later after the core recommendation system.

#### `api/`

Contains the FastAPI backend.

It will connect the frontend with the AI and recommendation system.

#### `config.py`

Contains shared project configuration where required.

---

## 4. `tests/`

Contains tests for project code.

Examples:

```text
test_preprocessing.py
test_recommendation.py
test_api.py
```

Test files will be created when the corresponding functionality is implemented.

---

## 5. `docs/`

Contains project documentation.

Current documentation includes:

```text
project_requirements.md
input_output_design_M0.3.md
system_architecture_M0.4.md
ml_pipeline_M0.5.md
technology_stack_M0.6.md
project_structure_M0.7.md
```

Future documentation can be added when new milestones require it.

---

## 6. Root Files

### `.gitignore`

Defines files and folders that Git should not track.

Important examples include:

```text
.venv/
__pycache__/
*.pyc
```

Large datasets and model files may also be excluded when appropriate.

---

### `README.md`

Provides an overview of the project.

It can contain:

- Project description
- Features
- Setup instructions
- Usage instructions
- Project structure
- Technologies used

---

### `requirements.txt`

Contains Python package dependencies required by the project.

Packages will be added as the project develops.

---

## 7. Important Development Rule

The complete structure is defined now, but all folders and files do not need to be created immediately.

New source files should be created when their corresponding development stage begins.

For example:

```text
M2 → Classification code
M4 → Embedding code
M5 → Compatibility code
M11 → FastAPI code
M12 → React frontend
```

This keeps the project organized without creating unnecessary empty files.

---

## 8. Project Organization Principle

The project follows a separation-of-responsibilities approach:

```text
Data
 ↓
Models
 ↓
Source Code
 ↓
API
 ↓
Frontend
```

Documentation, experiments, and tests remain separated from the main application code.

---

## 9. M0.7 Summary

The project structure is now formally defined.

Main areas:

```text
data/          → Dataset
models/        → Trained models
notebooks/     → Experiments
src/           → Main code
tests/         → Testing
docs/          → Documentation
```

This structure can be expanded later without changing the overall organization.
