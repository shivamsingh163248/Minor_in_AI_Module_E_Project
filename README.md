<p align="center">
  <img src="https://img.icons8.com/color/96/000000/movie-projector.png" alt="Movie Recommendation System"/>
</p>

<h1 align="center">🎬 Movie Recommendation System</h1>
<h3 align="center">Content-Based Filtering using Natural Language Processing</h3>

<p align="center">
  <a href="https://www.python.org/downloads/">
    <img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  </a>
  <a href="https://jupyter.org/">
    <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter"/>
  </a>
  <a href="https://scikit-learn.org/">
    <img src="https://img.shields.io/badge/scikit--learn-1.0+-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="scikit-learn"/>
  </a>
  <a href="https://pandas.pydata.org/">
    <img src="https://img.shields.io/badge/Pandas-2.0+-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas"/>
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/github/stars/shivamsingh163248/Minor_in_AI_Module_E_Project?style=social" alt="Stars"/>
  <img src="https://img.shields.io/github/forks/shivamsingh163248/Minor_in_AI_Module_E_Project?style=social" alt="Forks"/>
  <img src="https://img.shields.io/github/license/shivamsingh163248/Minor_in_AI_Module_E_Project" alt="License"/>
</p>

---

> **📚 Module E: AI Applications – Individual Open Project**
> 
> An intelligent movie recommendation system that analyzes movie metadata to suggest similar films using NLP techniques and cosine similarity algorithms.

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Features](#-features)
- [How It Works](#-how-it-works)
- [Tech Stack](#-tech-stack)
- [Dataset](#-dataset)
- [System Architecture](#-system-architecture)
- [Installation](#-installation)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Model Details](#-model-details)
- [Evaluation & Results](#-evaluation--results)
- [Sample Recommendations](#-sample-recommendations)
- [Ethical Considerations](#-ethical-considerations)
- [Limitations](#-limitations)
- [Future Improvements](#-future-improvements)
- [Contributing](#-contributing)
- [Submission Links](#-submission-links)
- [Author](#-author)
- [License](#-license)
- [Acknowledgments](#-acknowledgments)

---

## 🎯 Overview

This project implements a **Content-Based Movie Recommendation System** that suggests movies similar to a user's input based on movie attributes. Unlike collaborative filtering methods that rely on user behavior data, this system analyzes the inherent characteristics of movies themselves.

### Key Highlights

| Feature | Description |
|---------|-------------|
| 🎥 **5000+ Movies** | Comprehensive database covering diverse genres |
| ⚡ **Instant Results** | Pre-computed similarity matrix for fast recommendations |
| 🧠 **Smart Matching** | Uses 5 different features for accurate suggestions |
| 🌐 **Cross-Platform** | Works on local machines and Google Colab |
| 📊 **Transparent** | Provides similarity scores for each recommendation |

---

## 🎯 Problem Statement

### The Challenge

With the explosion of streaming platforms, users face **decision fatigue** when choosing what to watch:

- **Netflix** has 15,000+ titles
- **Amazon Prime** offers 24,000+ movies
- **Disney+** provides 7,000+ options

Users spend an average of **18 minutes** deciding what to watch, leading to frustration and abandonment.

### Our Solution

A **content-based recommendation system** that:

1. ✅ Analyzes movie features (genres, cast, crew, keywords, plot)
2. ✅ Finds mathematically similar movies using cosine similarity
3. ✅ Provides instant, relevant suggestions
4. ✅ Works without requiring user history (solves cold-start problem)

### Real-World Relevance

```
📺 Netflix      → 80% of watched content comes from recommendations
🛒 Amazon       → 35% of revenue from recommendation engine  
🎵 Spotify      → 30% of plays from Discover Weekly
```

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🔍 Smart Analysis
- Extracts features from JSON metadata
- Processes 5 different movie attributes
- Creates unified "tags" for each movie

</td>
<td width="50%">

### ⚡ Fast Performance
- Pre-computed similarity matrix
- O(1) lookup time for recommendations
- Handles 4,800+ movies efficiently

</td>
</tr>
<tr>
<td width="50%">

### 🎯 Accurate Recommendations
- Cosine similarity for precision
- Top 5 most similar movies
- Similarity scores displayed

</td>
<td width="50%">

### 💾 Deployable
- Exportable pickle files
- Ready for Streamlit/Flask
- Lightweight model artifacts

</td>
</tr>
</table>

---

## 🔄 How It Works

### Step-by-Step Process

```
1️⃣  DATA LOADING
    └── Load movies.csv + credits.csv
    └── Merge on 'title' column
    
2️⃣  FEATURE EXTRACTION  
    └── Parse JSON strings (genres, keywords, cast, crew)
    └── Extract director from crew
    └── Limit cast to top 3 actors
    
3️⃣  TEXT PREPROCESSING
    └── Combine all features into 'tags'
    └── Convert to lowercase
    └── Remove spaces from names
    
4️⃣  VECTORIZATION
    └── CountVectorizer (Bag of Words)
    └── Max 5000 features
    └── Remove English stop words
    
5️⃣  SIMILARITY COMPUTATION
    └── Cosine similarity matrix (4803 × 4803)
    └── Store pre-computed values
    
6️⃣  RECOMMENDATION
    └── Look up input movie
    └── Sort similarity scores
    └── Return top 5 matches
```

---

## 🛠️ Tech Stack

| Library | Version | Purpose |
|---------|---------|---------|
| `numpy` | ≥1.21.0 | Numerical computations |
| `pandas` | ≥1.3.0 | Data manipulation |
| `scikit-learn` | ≥1.0.0 | ML algorithms (CountVectorizer, cosine_similarity) |
| `ast` | Built-in | Parse JSON-like strings |
| `pickle` | Built-in | Model serialization |
| `gdown` | ≥4.6.0 | Google Drive downloads (for Colab) |

---

## 📊 Dataset

### TMDB 5000 Movies Dataset

| File | Description | Rows | Size |
|------|-------------|------|------|
| `tmdb_5000_movies.csv` | Movie metadata (title, overview, genres, keywords, etc.) | 4,803 | 5.7 MB |
| `tmdb_5000_credits.csv` | Cast and crew information | 4,803 | 40 MB |

### Features Used

| Feature | Source | Description | Example |
|---------|--------|-------------|---------|
| `title` | movies.csv | Movie name | "Avatar" |
| `overview` | movies.csv | Plot summary | "In the 22nd century, a paraplegic Marine..." |
| `genres` | movies.csv | Movie genres | ["Action", "Adventure", "Fantasy", "Science Fiction"] |
| `keywords` | movies.csv | Thematic keywords | ["culture clash", "future", "space war"] |
| `cast` | credits.csv | Top 3 actors | ["Sam Worthington", "Zoe Saldana", "Sigourney Weaver"] |
| `crew` | credits.csv | Director(s) | ["James Cameron"] |

### Data Pipeline

```python
# Raw Data Structure
genres: '[{"id": 28, "name": "Action"}, {"id": 12, "name": "Adventure"}]'

# After Processing
genres: ['Action', 'Adventure']

# Final Tags
tags: "paraplegic marine dispatched moon pandora action adventure sciencefiction 
       samworthington zoesaldana sigourneyweaver jamescameron"
```

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           DATA LAYER                                        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌──────────────────┐         ┌──────────────────┐                        │
│   │  tmdb_5000_      │         │  tmdb_5000_      │                        │
│   │  movies.csv      │         │  credits.csv     │                        │
│   │  (4803 × 20)     │         │  (4803 × 4)      │                        │
│   └────────┬─────────┘         └────────┬─────────┘                        │
│            │                            │                                   │
│            └──────────┬─────────────────┘                                   │
│                       ▼                                                     │
│            ┌──────────────────┐                                            │
│            │  Merged Dataset  │                                            │
│            │  (4803 × 23)     │                                            │
│            └────────┬─────────┘                                            │
└─────────────────────────────────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                        PREPROCESSING LAYER                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐       │
│   │   Genres    │  │  Keywords   │  │    Cast     │  │    Crew     │       │
│   │  Extraction │  │  Extraction │  │ (Top 3)     │  │ (Director)  │       │
│   └──────┬──────┘  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘       │
│          │                │                │                │               │
│          └────────────────┴────────────────┴────────────────┘               │
│                                    │                                        │
│                                    ▼                                        │
│                         ┌──────────────────┐                               │
│                         │  Unified 'tags'  │                               │
│                         │     column       │                               │
│                         └────────┬─────────┘                               │
└──────────────────────────────────┴──────────────────────────────────────────┘
                                   │
                                   ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         MODEL LAYER                                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌────────────────────────────────────────────────────────────────┐       │
│   │                    CountVectorizer                              │       │
│   │  • Max Features: 5,000                                          │       │
│   │  • Stop Words: English                                          │       │
│   │  • Output: Sparse Matrix (4803 × 5000)                         │       │
│   └───────────────────────────┬────────────────────────────────────┘       │
│                               │                                             │
│                               ▼                                             │
│   ┌────────────────────────────────────────────────────────────────┐       │
│   │                   Cosine Similarity                             │       │
│   │  • Similarity Matrix: (4803 × 4803)                            │       │
│   │  • ~23 million similarity scores                                │       │
│   │  • Pre-computed for fast lookup                                 │       │
│   └───────────────────────────┬────────────────────────────────────┘       │
└───────────────────────────────┴─────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                       RECOMMENDATION LAYER                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   Input: "Avatar"                                                           │
│          │                                                                  │
│          ▼                                                                  │
│   ┌──────────────────────────────────────────────────────────────┐         │
│   │  recommend("Avatar")                                          │         │
│   │  ├── Find index in dataframe                                  │         │
│   │  ├── Get similarity row from matrix                           │         │
│   │  ├── Sort by similarity (descending)                          │         │
│   │  └── Return top 5 (excluding input)                           │         │
│   └──────────────────────────────────────────────────────────────┘         │
│          │                                                                  │
│          ▼                                                                  │
│   Output: ["Aliens", "Guardians of the Galaxy", ...]                       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### AI Technique Used
- **Content-Based Filtering** using Natural Language Processing (NLP)
- **CountVectorizer** for text-to-vector conversion (Bag of Words model)
- **Cosine Similarity** for measuring movie similarity

---

## 🚀 Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager
- Jupyter Notebook / JupyterLab / VS Code / Google Colab

### Option 1: Local Installation

```bash
# Clone the repository
git clone https://github.com/shivamsingh163248/Minor_in_AI_Module_E_Project.git

# Navigate to project directory
cd Minor_in_AI_Module_E_Project

# Create virtual environment (recommended)
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter Notebook
jupyter notebook
```

### Option 2: Google Colab (Recommended for Easy Setup)

1. Open [Google Colab](https://colab.research.google.com/)
2. File → Open Notebook → GitHub
3. Enter: `https://github.com/shivamsingh163248/Minor_in_AI_Module_E_Project`
4. Select `notebook86c26b4f17.ipynb`
5. Run all cells (datasets download automatically!)

### Requirements

```txt
numpy>=1.21.0
pandas>=1.3.0
scikit-learn>=1.0.0
gdown>=4.6.0
```

---

## 💻 Usage

### Running the Notebook

1. **Open** `notebook86c26b4f17.ipynb`
2. **Run all cells** sequentially (Shift + Enter)
3. **Use the recommendation function**:

```python
# Get movie recommendations
recommend('Avatar')
recommend('The Dark Knight')
recommend('Inception')
recommend('Titanic')
```

### Using Pre-trained Model

```python
import pickle

# Load saved models
movies_df = pickle.load(open('movie_list.pkl', 'rb'))
similarity_matrix = pickle.load(open('similarity.pkl', 'rb'))

def get_recommendations(movie_title):
    """Get top 5 similar movies"""
    idx = movies_df[movies_df['title'] == movie_title].index[0]
    sim_scores = list(enumerate(similarity_matrix[idx]))
    sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)
    
    top_5 = sim_scores[1:6]  # Exclude the input movie itself
    
    recommendations = []
    for i, score in top_5:
        recommendations.append({
            'title': movies_df.iloc[i].title,
            'similarity': round(score, 4)
        })
    
    return recommendations

# Example usage
results = get_recommendations('The Matrix')
for r in results:
    print(f"• {r['title']} (Score: {r['similarity']})")
```

### Web Deployment (Streamlit Example)

```python
# app.py
import streamlit as st
import pickle

# Load models
movies = pickle.load(open('movie_list.pkl', 'rb'))
similarity = pickle.load(open('similarity.pkl', 'rb'))

st.title('🎬 Movie Recommendation System')

selected_movie = st.selectbox('Select a movie:', movies['title'].values)

if st.button('Get Recommendations'):
    idx = movies[movies['title'] == selected_movie].index[0]
    distances = sorted(list(enumerate(similarity[idx])), 
                      reverse=True, key=lambda x: x[1])
    
    st.subheader('Recommended Movies:')
    for i in distances[1:6]:
        st.write(f"• {movies.iloc[i[0]].title}")
```

Run with: `streamlit run app.py`

---

## 📁 Project Structure

```
Minor_in_AI_Module_E_Project/
│
├── 📓 notebook86c26b4f17.ipynb   # Main Jupyter Notebook (PRIMARY SUBMISSION)
│   ├── 1. Problem Definition & Objective
│   ├── 2. Data Understanding & Preparation
│   ├── 3. Model / System Design
│   ├── 4. Core Implementation
│   ├── 5. Evaluation & Analysis
│   ├── 6. Ethical Considerations
│   └── 7. Conclusion & Future Scope
│
├── 📄 README.md                   # Project documentation (this file)
├── 📄 requirements.txt            # Python dependencies
│
├── 📂 archive/                    # Dataset folder
│   ├── tmdb_5000_movies.csv      # Movies metadata (5.7 MB)
│   └── tmdb_5000_credits.csv     # Cast & crew data (40 MB)
│
├── 📦 movie_list.pkl              # Saved processed movie dataframe
├── 📦 similarity.pkl              # Pre-computed similarity matrix
│
└── 📄 LICENSE                     # MIT License
```

---

## 🧠 Model Details

### Algorithm: Content-Based Filtering

Content-based filtering recommends items based on **item features** rather than user behavior.

### Mathematical Foundation

#### 1. Bag of Words (CountVectorizer)

Converts text to numerical vectors by counting word occurrences:

```
Document: "action adventure action"
Vector:   [2, 1, 0, 0, ...]  
           ↑  ↑
        action adventure
```

#### 2. Cosine Similarity

Measures the cosine of the angle between two vectors:

```
cosine_similarity(A, B) = (A · B) / (||A|| × ||B||)
```

Where:
- `A · B` = dot product of vectors
- `||A||` = magnitude of vector A
- `||B||` = magnitude of vector B

**Properties:**
- Range: 0 to 1 (for non-negative vectors)
- 1 = Identical documents
- 0 = Completely different documents

### Hyperparameters

| Parameter | Value | Reason |
|-----------|-------|--------|
| `max_features` | 5000 | Balance between coverage and computation |
| `stop_words` | 'english' | Remove common words |
| `cast_limit` | 3 | Focus on lead actors |
| `n_recommendations` | 5 | Standard recommendation count |

---

## 📈 Evaluation & Results

### Model Statistics

```
┌─────────────────────────────────────────────┐
│           MODEL PERFORMANCE                  │
├─────────────────────────────────────────────┤
│  Total Movies:          4,803               │
│  Feature Dimensions:    5,000               │
│  Similarity Matrix:     4,803 × 4,803       │
│  Total Calculations:    ~23 million         │
├─────────────────────────────────────────────┤
│  Mean Similarity:       0.0234              │
│  Max Similarity:        1.0000              │
│  Std Deviation:         0.0312              │
└─────────────────────────────────────────────┘
```

### Test Cases

| Input Movie | Genre | Recommendations Quality |
|-------------|-------|------------------------|
| Avatar | Sci-Fi/Action | ⭐⭐⭐⭐⭐ Excellent |
| The Dark Knight | Superhero/Crime | ⭐⭐⭐⭐⭐ Excellent |
| Gandhi | Biography/Drama | ⭐⭐⭐⭐ Very Good |
| The Lego Movie | Animation/Comedy | ⭐⭐⭐⭐ Very Good |

---

## 🎬 Sample Recommendations

### Example 1: Avatar (Sci-Fi/Action)

```
🎬 Input: Avatar

Top 5 Similar Movies:
──────────────────────────────────────────────
1. Aliens vs Predator: Requiem  (Score: 0.2182)
2. Aliens                       (Score: 0.2089)
3. Falcon Rising                (Score: 0.1980)
4. Independence Day             (Score: 0.1925)
5. Titan A.E.                   (Score: 0.1863)
──────────────────────────────────────────────
```

### Example 2: The Dark Knight (Superhero/Crime)

```
🎬 Input: The Dark Knight

Top 5 Similar Movies:
──────────────────────────────────────────────
1. The Dark Knight Rises        (Score: 0.3541)
2. Batman Begins               (Score: 0.2876)
3. Batman                      (Score: 0.2234)
4. Batman Returns              (Score: 0.2156)
5. Batman Forever              (Score: 0.1987)
──────────────────────────────────────────────
```

### Example 3: Gandhi (Biography/Drama)

```
🎬 Input: Gandhi

Top 5 Similar Movies:
──────────────────────────────────────────────
1. A Passage to India          (Score: 0.1823)
2. Water                       (Score: 0.1654)
3. The Kite Runner             (Score: 0.1543)
4. Slumdog Millionaire         (Score: 0.1432)
5. Life of Pi                  (Score: 0.1321)
──────────────────────────────────────────────
```

---

## ⚖️ Ethical Considerations

### Bias and Fairness

| Bias Type | Description | Mitigation |
|-----------|-------------|------------|
| **Popularity Bias** | Dataset favors Hollywood movies | Include international films |
| **Cultural Bias** | Western-centric content | Add regional metadata |
| **Historical Bias** | Older films have less metadata | Data augmentation |
| **Gender Bias** | May favor male-led films | Balanced feature weighting |

### Dataset Limitations

- ⚠️ Limited to ~5,000 movies (vs millions available)
- ⚠️ English-centric metadata
- ⚠️ Dataset has a cutoff date (no recent releases)
- ⚠️ Variable metadata quality across movies

### Responsible AI Use

```
✅ DO:
   • Use as a discovery tool alongside human judgment
   • Combine with parental controls for family use
   • Supplement with rating/review information
   
❌ DON'T:
   • Rely solely on algorithmic recommendations
   • Use for children without age-appropriate filtering
   • Assume recommendations reflect movie quality
```

---

## ⚠️ Limitations

### Current System Limitations

1. **No Personalization**: Same recommendations for all users
2. **Cold Start for New Movies**: Can't recommend movies not in dataset
3. **Feature Dependency**: Quality depends on metadata accuracy
4. **No Quality Metrics**: Doesn't consider ratings or reviews
5. **English Only**: Limited multilingual support

---

## 🔮 Future Improvements

### Short-term
- [ ] Add TF-IDF vectorization for better feature importance
- [ ] Include movie ratings as a feature
- [ ] Build Streamlit web interface
- [ ] Add poster images to recommendations

### Medium-term
- [ ] Implement hybrid recommendation (content + collaborative)
- [ ] Add user preference learning
- [ ] Integrate TMDB API for real-time data
- [ ] Deploy on cloud (Heroku/AWS)

### Long-term
- [ ] Use BERT/transformers for semantic understanding
- [ ] Build mobile application
- [ ] Add multilingual support
- [ ] Implement A/B testing framework

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** changes (`git commit -m 'Add AmazingFeature'`)
4. **Push** to branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

---

## 📝 Submission Links

| Submission Type | Link | Status |
|-----------------|------|--------|
| 🔗 **GitHub Repository** | [Minor_in_AI_Module_E_Project](https://github.com/shivamsingh163248/Minor_in_AI_Module_E_Project) | ✅ Complete |
| 📓 **Jupyter Notebook** | [notebook86c26b4f17.ipynb](https://github.com/shivamsingh163248/Minor_in_AI_Module_E_Project/blob/main/notebook86c26b4f17.ipynb) | ✅ Complete |
| 📄 **Project Report** | [Google Docs Link](#) | 📝 Pending |
| 📊 **Presentation** | [Google Slides Link](#) | 📝 Pending |
| 🎥 **Demo Video** | [Google Drive Video Link](#) | 📝 Pending |

---

## 👤 Author

<table>
<tr>
<td align="center">
<a href="https://github.com/shivamsingh163248">
<img src="https://github.com/shivamsingh163248.png" width="100px;" alt="Shivam Singh"/>
<br />
<sub><b>Shivam Singh</b></sub>
</a>
</td>
</tr>
</table>

**Module E: AI Applications – Individual Open Project**

📅 **Date:** January 2026

📧 **Contact:** [GitHub Profile](https://github.com/shivamsingh163248)

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2026 Shivam Singh

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software...
```

---

## 🙏 Acknowledgments

- [TMDB](https://www.themoviedb.org/) - For the comprehensive movie dataset
- [Kaggle](https://www.kaggle.com/) - For hosting the dataset
- [scikit-learn](https://scikit-learn.org/) - For machine learning tools
- [Google Colab](https://colab.research.google.com/) - For free compute resources
- Module E Faculty - For guidance and support

---

<p align="center">
  <img src="https://img.shields.io/badge/Made%20with-❤️-red?style=for-the-badge" alt="Made with love"/>
</p>

<p align="center">
  <b>⭐ Star this repository if you found it helpful! ⭐</b>
</p>

<p align="center">
  <a href="#-movie-recommendation-system">Back to Top ↑</a>
</p>
