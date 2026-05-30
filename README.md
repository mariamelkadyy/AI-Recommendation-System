# 🎬 Movie Recommendation System

A content-based movie recommendation engine built using
TF-IDF vectorization and Cosine Similarity.
Given a movie title, the system returns the most
similar movies based on genres, keywords, and plot overview.

---

## 📌 Project Overview

This project is part of the DecodeLabs AI Industrial Training Kit (Project 3).
The goal is to move from passive data classification to active prediction —
building a system that understands user intent and returns relevant recommendations.

**Type:** Content-Based Filtering  
**Algorithm:** TF-IDF + Cosine Similarity  
**Dataset:** TMDB 5000 Movies (Kaggle)

---

## 🧠 How It Works

```
User Input (movie title)
        ↓
Feature Engineering (genres + keywords + overview → one text string)
        ↓
TF-IDF Vectorization (text → weighted numerical vectors)
        ↓
Cosine Similarity (compare input vector against all movie vectors)
        ↓
Sort & Filter (Top-N highest scoring matches)
        ↓
Output: Ranked list of recommended movies
```

---

## 📁 Project Structure

```
Task-1-MariamAhmed/
│
├── tmdb_5000_movies.csv              # TMDB dataset (download from Kaggle)
├── recommendation_system.ipynb       # Full project notebook
├── app.py                            # Streamlit web app
├── requirements.txt
├── outputs/
│   └── recommendations.csv           # Saved recommendation results
└── README.md
```

---

## ⚙️ Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/mariamelkadyy/Task-1-MariamAhmed.git
cd Task-1-MariamAhmed
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Download the dataset**

Go to [TMDB Movie Metadata on Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)  
Download `tmdb_5000_movies.csv` and place it in the **same folder as `app.py`** (the root of the repo).

**4. Run the Streamlit app**
```bash
streamlit run app.py
```

**5. Or run the notebook**
```bash
jupyter notebook recommendation_system.ipynb
```

---

## 🧪 Example Output

Input: `The Fast and the Furious`

| Rank | Title                                    | Score  |
|------|------------------------------------------|--------|
| 1    | 2 Fast 2 Furious                         | 0.2648 |
| 2    | The Fast and the Furious: Tokyo Drift    | 0.2466 |
| 3    | Need for Speed                           | 0.2225 |
| 4    | Stone Cold                               | 0.2142 |
| 5    | Point Break                              | 0.2039 |

---

## 📐 Key Concepts

### TF-IDF (Term Frequency — Inverse Document Frequency)
Converts text into weighted numbers.
- **TF:** Words that appear often in one movie get higher weight
- **IDF:** Words that appear in every movie (like "the", "and") get penalized
- Result: Specific, meaningful words matter more than generic ones

### Cosine Similarity
Measures the angle between two vectors — not their size.
- Score **1.0** → movies are very similar
- Score **0.0** → movies share nothing in common
- Preferred over Euclidean distance because it is magnitude-invariant:
  a movie with a long description won't unfairly outscore one with a short description

### Content-Based Filtering vs Collaborative Filtering

| | Content-Based | Collaborative |
|---|---|---|
| Based on | Item attributes | User behavior |
| Needs user history? | No | Yes |
| Cold start problem? | Partial | Yes |
| This project uses | ✅ | ❌ |

---

## ⚠️ Limitations

- **Cold Start (User):** Cannot personalize for a brand new user with no history
- **Popularity Bias:** Common genres like Action/Drama may dominate results
- **No rating data:** Does not account for movie quality or user ratings
- **Keyword dependency:** Movies with sparse or missing keywords return weaker results

---

## 🔧 Possible Improvements

- Merge cast/director data from `tmdb_5000_credits.csv` for richer features
- Add a weighted scoring system (genres weighted higher than overview words)
- Build a hybrid system combining content-based + collaborative filtering
- Deploy as a web app using Streamlit

---

## 📦 Requirements

- pandas
- numpy
- scikit-learn
- streamlit
- jupyter

---

## 👩‍💻 Author

**Mariam**  
AI Student — Galala University  
Industrial Training @ DecodeLabs, Batch 2026

[![GitHub](https://img.shields.io/badge/GitHub-mariamelkadyy-black?logo=github)](https://github.com/mariamelkadyy)
