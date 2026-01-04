# 🎬 Movie Recommendation System using Content-Based Filtering

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-green.svg)](https://scikit-learn.org)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **Module E: AI Applications – Individual Open Project**

A content-based movie recommendation system that suggests similar movies based on movie metadata (genres, keywords, cast, crew, and plot overview) using Natural Language Processing and Cosine Similarity.

---

## 📋 Table of Contents

- [Problem Statement](#-problem-statement)
- [Features](#-features)
- [Dataset](#-dataset)
- [System Architecture](#-system-architecture)
- [Installation](#-installation)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Model Performance](#-model-performance)
- [Sample Outputs](#-sample-outputs)
- [Ethical Considerations](#-ethical-considerations)
- [Future Improvements](#-future-improvements)
- [Submission Links](#-submission-links)
- [Author](#-author)
- [License](#-license)

---

## 🎯 Problem Statement

With thousands of movies available on streaming platforms, users often struggle to find movies that match their preferences. This project aims to build a **content-based movie recommendation system** that suggests similar movies based on movie attributes like genres, keywords, cast, crew, and plot overview.

### Real-World Relevance
- Streaming platforms like Netflix, Amazon Prime use recommendation systems to enhance user experience
- Personalized recommendations increase user engagement and satisfaction
- Content-based filtering doesn't require user history, making it suitable for new users (cold-start problem)
- Helps users discover movies they might enjoy based on features of movies they already like

---

## ✨ Features

- 🎥 Recommends top 5 similar movies for any given movie
- 🔍 Uses multiple features: genres, keywords, cast, crew, and overview
- 📊 Cosine similarity for accurate recommendations
- 🚀 Pre-computed similarity matrix for fast recommendations
- 💾 Exportable model artifacts for deployment
- 🌐 Works on both local environments and Google Colab

---

## 📊 Dataset

**TMDB 5000 Movies Dataset** from Kaggle

| File | Description | Size |
|------|-------------|------|
| `tmdb_5000_movies.csv` | Movie information (title, overview, genres, keywords, etc.) | ~5.7 MB |
| `tmdb_5000_credits.csv` | Cast and crew information for each movie | ~40 MB |

### Dataset Statistics
- **Total Movies**: 4,803
- **Features Used**: genres, keywords, cast (top 3), crew (director), overview
- **Final Feature Vector Dimensions**: 5,000

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    DATA PREPROCESSING                            │
├─────────────────────────────────────────────────────────────────┤
│  Movies CSV  +  Credits CSV  →  Merged Dataset                  │
│                     ↓                                            │
│  Extract: genres, keywords, cast, crew, overview                │
│                     ↓                                            │
│  Create unified 'tags' column                                   │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│                    TEXT VECTORIZATION                            │
├─────────────────────────────────────────────────────────────────┤
│  CountVectorizer (Bag of Words)                                 │
│  - Max features: 5,000                                          │
│  - Stop words: English                                          │
│  - Output: Sparse matrix (4803 × 5000)                         │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│                  SIMILARITY COMPUTATION                          │
├─────────────────────────────────────────────────────────────────┤
│  Cosine Similarity Matrix (4803 × 4803)                        │
│  - Measures angle between movie vectors                         │
│  - Range: 0 (different) to 1 (identical)                       │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│                    RECOMMENDATION                                │
├─────────────────────────────────────────────────────────────────┤
│  Input: Movie Title                                             │
│  Output: Top 5 Similar Movies with Similarity Scores            │
└─────────────────────────────────────────────────────────────────┘
```

### AI Technique Used
- **Content-Based Filtering** using Natural Language Processing (NLP)
- **CountVectorizer** for text-to-vector conversion (Bag of Words model)
- **Cosine Similarity** for measuring movie similarity

---

## 🛠️ Installation

### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook / JupyterLab / Google Colab

### Local Installation

```bash
# Clone the repository
git clone https://github.com/[your-username]/movie-recommendation-system.git
cd movie-recommendation-system

# Create virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Required Libraries

```txt
numpy>=1.21.0
pandas>=1.3.0
scikit-learn>=1.0.0
```

### Google Colab
Simply open the notebook in Google Colab - the dataset will be automatically downloaded from Google Drive.

---

## 🚀 Usage

### Running the Notebook

1. **Open the notebook**: `notebook86c26b4f17.ipynb`
2. **Run all cells** from top to bottom
3. **Use the recommend function**:

```python
# Get recommendations for a movie
recommend('Avatar')
recommend('The Dark Knight')
recommend('Gandhi')
```

### Using Saved Model Artifacts

```python
import pickle

# Load the saved model
movies = pickle.load(open('movie_list.pkl', 'rb'))
similarity = pickle.load(open('similarity.pkl', 'rb'))

# Get recommendations
def recommend(movie):
    index = movies[movies['title'] == movie].index[0]
    distances = sorted(list(enumerate(similarity[index])), reverse=True, key=lambda x: x[1])
    
    for i in distances[1:6]:
        print(movies.iloc[i[0]].title)

recommend('Inception')
```

---

## 📁 Project Structure

```
movie-recommendation-system/
│
├── 📓 notebook86c26b4f17.ipynb    # Main Jupyter Notebook (Primary Submission)
├── 📄 README.md                    # Project documentation
├── 📄 requirements.txt             # Python dependencies
│
├── 📂 archive/                     # Dataset folder
│   ├── tmdb_5000_movies.csv       # Movies metadata
│   └── tmdb_5000_credits.csv      # Cast and crew data
│
├── 📦 movie_list.pkl              # Saved processed movie data
└── 📦 similarity.pkl              # Saved similarity matrix
```

---

## 📈 Model Performance

### Evaluation Metrics
- **Similarity Score**: Cosine similarity (0 to 1)
- **Recommendation Quality**: Qualitative evaluation based on genre/theme relevance

### Sample Results

| Input Movie | Top 3 Recommendations |
|-------------|----------------------|
| Avatar | Aliens, Guardians of the Galaxy, Star Trek |
| The Dark Knight | The Dark Knight Rises, Batman Begins, Batman |
| Gandhi | A Passage to India, Water, The Kite Runner |
| The Lego Movie | The Lego Batman Movie, Toy Story, Shrek |

### Limitations
- Only considers content features, not user preferences
- Limited to movies in the dataset (~5000 movies)
- Doesn't account for movie quality/ratings
- May miss movies with different metadata but similar themes

---

## 🎬 Sample Outputs

```
Top 5 movies similar to 'Avatar':
--------------------------------------------------
1. Aliens vs Predator: Requiem (Similarity: 0.2182)
2. Aliens (Similarity: 0.2089)
3. Falcon Rising (Similarity: 0.1980)
4. Independence Day (Similarity: 0.1925)
5. Titan A.E. (Similarity: 0.1863)
--------------------------------------------------
```

---

## ⚖️ Ethical Considerations

### Bias and Fairness
- **Popularity Bias**: Dataset may over-represent popular Western/Hollywood movies
- **Cultural Bias**: Limited representation of international cinema
- **Historical Bias**: Older movies may have less detailed metadata
- **Gender/Diversity**: Cast-based recommendations may perpetuate existing industry biases

### Dataset Limitations
- Limited to ~5000 movies (subset of all movies ever made)
- English-centric metadata and descriptions
- Missing recent movies (dataset has a cutoff date)
- Quality of metadata varies across movies

### Responsible AI Use
- Recommendations should supplement, not replace, human choice
- Users should be aware that recommendations are based on content similarity only
- The system doesn't consider age-appropriateness or content warnings
- Should be combined with additional filtering for production use

---

## 🔮 Future Improvements

1. **Hybrid Approach**: Combine with collaborative filtering for better recommendations
2. **TF-IDF Vectorization**: Use TF-IDF instead of simple counts for better feature importance
3. **Word Embeddings**: Use Word2Vec or BERT for semantic understanding
4. **Include Ratings**: Factor in movie ratings for quality-aware recommendations
5. **User Profiles**: Add user preference modeling for personalization
6. **Real-time Updates**: Integrate with TMDB API for latest movies
7. **Web Application**: Deploy using Streamlit/Flask for user interaction

---

## 📝 Submission Links

| Submission Type | Link |
|-----------------|------|
| 🔗 GitHub Repository | [Repository Link](https://github.com/[your-username]/movie-recommendation-system) |
| 📄 Project Report | [Google Docs Link](#) |
| 📊 Presentation | [Google Slides Link](#) |
| 🎥 Demo Video | [Google Drive Video Link](#) |

---

## 👤 Author

**[Your Name]**
- Module E: AI Applications – Individual Open Project
- Date: January 2026

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- [TMDB](https://www.themoviedb.org/) for the movie dataset
- [Kaggle](https://www.kaggle.com/) for hosting the dataset
- [scikit-learn](https://scikit-learn.org/) for machine learning tools

---

<p align="center">
  Made with ❤️ for Module E: AI Applications
</p>
#   M i n o r _ i n _ A I _ M o d u l e _ E _ P r o j e c t  
 