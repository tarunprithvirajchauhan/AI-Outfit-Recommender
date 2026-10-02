# AI Outfit Recommender
## Technology Stack - M0.6

### 1. Purpose

This document defines the main technologies planned for the AI Outfit Recommender project and explains their roles.

---

## 2. Technology Stack

| Project Part | Technology | Purpose |
|---|---|---|
| Programming Language | Python 3.12 | ML, computer vision, data processing and backend logic |
| Deep Learning | PyTorch | Training and running deep learning models |
| ML Utilities | Scikit-learn | Metrics, preprocessing and traditional ML utilities |
| Computer Vision | OpenCV | Image processing and computer vision operations |
| Data Processing | NumPy | Numerical and array operations |
| Data Analysis | Pandas | Dataset loading, cleaning and analysis |
| Image Embeddings | CLIP / suitable vision model | Extract visual feature representations |
| Backend | FastAPI | Provide APIs between the frontend and AI system |
| Frontend | React | Build the web interface |
| Styling | Tailwind CSS | Style the web interface |
| Database | PostgreSQL | Store users, clothing metadata, wardrobes and feedback |
| Version Control | Git | Track code and project changes |
| Remote Repository | GitHub | Store and collaborate on the project |
| Deployment | To be decided | Host the final application |

---

## 3. Technology Roles

### 3.1 Python

Python is the primary programming language.

It will be used for:

- Machine learning
- Computer vision
- Data processing
- Model inference
- Recommendation logic
- Backend development

The project environment uses Python 3.12.

---

### 3.2 PyTorch

PyTorch will be used for deep learning.

Potential uses include:

- Training vision models
- Fine-tuning pretrained models
- Training the outfit compatibility model
- Running trained models during inference

The exact model architecture will be selected later.

---

### 3.3 Scikit-learn

Scikit-learn will mainly be used for:

- Data preprocessing
- Evaluation metrics
- Dataset splitting
- Traditional machine learning utilities
- Experimentation

It may also be useful for evaluating recommendation and classification results.

---

### 3.4 OpenCV

OpenCV will be used for image processing tasks such as:

- Reading images
- Resizing images
- Image format handling
- Basic image transformations
- Computer vision preprocessing

---

### 3.5 NumPy

NumPy provides numerical operations needed throughout the project.

It will be useful for:

- Embedding vectors
- Numerical calculations
- Arrays
- Model input/output processing

---

### 3.6 Pandas

Pandas will be used mainly during dataset preparation and analysis.

Examples:

- Loading CSV files
- Cleaning datasets
- Exploring dataset information
- Managing labels and metadata
- Preparing training data

---

### 3.7 CLIP / Vision Model

A suitable pretrained vision model will be used to generate image embeddings.

The current direction is to evaluate CLIP or another suitable vision encoder.

The final choice will be made after studying the available datasets and testing model suitability.

Therefore, CLIP is a planned candidate, not a permanently fixed decision at M0.6.

---

### 3.8 FastAPI

FastAPI will act as the backend API.

Its main role will be:

```text
React Website
      ↓
   FastAPI
      ↓
AI / Recommendation System
      ↓
   Response
      ↓
React Website
```

It will handle things such as:

- Image uploads
- Recommendation requests
- Model inference
- Returning recommendation results

---

### 3.9 React

React will be used to build the frontend website.

It will provide interfaces for:

- Uploading clothing
- Viewing wardrobe items
- Selecting context
- Requesting recommendations
- Displaying recommended outfits

---

### 3.10 Tailwind CSS

Tailwind CSS will be used to style the React interface.

It will help create:

- Responsive layouts
- Buttons
- Cards
- Forms
- Outfit recommendation displays

---

### 3.11 PostgreSQL

PostgreSQL will store structured application data.

Possible data includes:

- User information
- Clothing metadata
- Wardrobe information
- Recommendation history
- User preferences
- Feedback

Images themselves may be stored separately, while their paths or references can be stored in PostgreSQL.

---

### 3.12 Git and GitHub

Git will track changes in the project.

GitHub will be used as the remote repository.

Basic workflow:

```text
Make changes
    ↓
Git add
    ↓
Git commit
    ↓
Git push
    ↓
GitHub
```

---

## 4. Training vs Production Technologies

The project has two environments conceptually.

### Training

```text
Python
PyTorch
OpenCV
NumPy
Pandas
Scikit-learn
        ↓
Train Models
        ↓
Save Models
```

### Production Application

```text
React
   ↓
FastAPI
   ↓
Saved ML Models
   ↓
Recommendation Engine
   ↓
PostgreSQL
```

The same trained models can then be used by the application for inference.

---

## 5. Technology Selection Principle

Technologies should be selected based on project requirements rather than adding tools unnecessarily.

Important principles:

- Prefer mature and well-supported tools.
- Avoid unnecessary dependencies.
- Keep the ML pipeline reproducible.
- Keep frontend and backend separate.
- Keep model code separate from application code.
- Select the final ML models only after dataset analysis and experiments.

---

## 6. Technologies Not Yet Fixed

The following decisions will be made later:

- Exact clothing classification model
- Exact attribute extraction approach
- Exact embedding model
- Exact compatibility model
- Image storage provider
- Deployment platform
- GPU/cloud infrastructure, if required

These should not be finalized before the relevant experiments.

---

## 7. M0.6 Summary

The planned technology stack is:

```text
Python 3.12
├── PyTorch
├── Scikit-learn
├── OpenCV
├── NumPy
└── Pandas

Backend
└── FastAPI

Frontend
├── React
└── Tailwind CSS

Database
└── PostgreSQL

Version Control
├── Git
└── GitHub
```

The exact AI models will be selected later based on dataset suitability, performance, computational requirements and project goals.
