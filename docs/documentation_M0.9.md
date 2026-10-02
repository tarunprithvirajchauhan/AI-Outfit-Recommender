# AI Outfit Recommender
## Documentation Plan - M0.9

### 1. Purpose

This document defines how the AI Outfit Recommender project will be documented throughout development.

Good documentation will make the project easier to understand, reproduce, maintain and present.

---

## 2. Current Documentation

The `docs/` folder contains:

```text
docs/
├── project_requirements.md
├── input_output_design_M0.3.md
├── system_architecture_M0.4.md
├── ml_pipeline_M0.5.md
├── technology_stack_M0.6.md
├── project_structure_M0.7.md
└── documentation_M0.9.md
```

Additional planning documents may also exist as the project develops.

---

## 3. Documentation Categories

### 3.1 Project Documentation

These documents explain what the project is and how it is designed.

Examples:

- Project requirements
- Input/output design
- System architecture
- ML pipeline
- Technology stack
- Project structure

---

### 3.2 Dataset Documentation

For every important dataset, documentation should record:

- Dataset name
- Source
- Purpose
- Number of samples
- Classes/categories
- Important attributes
- License or usage restrictions
- Preprocessing performed
- Train/validation/test split

This will be created during the dataset stage.

---

### 3.3 Model Documentation

Each major ML model should document:

- Model name
- Purpose
- Input
- Output
- Dataset used
- Training procedure
- Important parameters
- Evaluation metrics
- Final performance
- Saved model location

Example:

```text
Compatibility Model
    ↓
Purpose
    ↓
Input / Output
    ↓
Training
    ↓
Evaluation
    ↓
Saved Model
```

---

### 3.4 Experiment Documentation

Experiments should record:

- What was tested
- Why it was tested
- Dataset/configuration used
- Model used
- Results
- Observations
- Final decision

This prevents useful experiment results from being lost.

---

### 3.5 API Documentation

When the FastAPI backend is developed, documentation should include:

- Endpoint
- HTTP method
- Input
- Output
- Required parameters
- Error responses
- Example request/response

---

### 3.6 User Documentation

The final project should explain:

- How to install the project
- How to start the application
- How to upload clothing
- How to request recommendations
- How to interpret recommendation results

This information will primarily be maintained in `README.md`.

---

## 4. README.md

The root `README.md` should eventually contain:

```text
Project Overview
        ↓
Features
        ↓
Technology Stack
        ↓
Project Structure
        ↓
Installation
        ↓
Usage
        ↓
Model Information
        ↓
Results
        ↓
Future Improvements
```

The README will be updated as the project becomes functional.

---

## 5. Documentation Rules

The project will follow these rules:

1. Document important design decisions.
2. Keep documentation synchronized with the implementation.
3. Record dataset sources and licenses.
4. Record model experiments and results.
5. Avoid documenting features that have not actually been implemented as completed features.
6. Use simple and consistent terminology.
7. Keep technical details where they are most relevant.
8. Update the README when major user-facing functionality is added.

---

## 6. Documentation and Git

Documentation changes should be tracked using Git.

Example:

```text
Change documentation
      ↓
git add .
      ↓
git commit
      ↓
git push
```

This keeps documentation history alongside the code.

---

## 7. Documentation Status

### Completed

- Project requirements
- Input/output design
- System architecture
- ML pipeline
- Technology stack
- Project structure
- Git/GitHub setup

### Future

- Dataset documentation
- Model documentation
- Experiment reports
- API documentation
- Final user documentation
- Model evaluation results

---

## 8. M0.9 Summary

The documentation strategy is now defined.

The project will maintain documentation for:

```text
Requirements
Architecture
ML Pipeline
Technology
Project Structure
Datasets
Models
Experiments
API
User Guide
```

Documentation will evolve together with the project instead of being written only at the end.
