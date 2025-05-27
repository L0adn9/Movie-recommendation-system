# 🎬 Movie Recommendation System

This project implements a **movie recommendation engine** using **collaborative filtering** techniques in two separate Jupyter notebooks:

* **Item-Based Collaborative Filtering** (`item_based.ipynb`)
* **User-Based Collaborative Filtering** (`user_based.ipynb`)

Both systems use the **mock data** (`ratings.csv`, `movies.csv`) and compute **cosine similarity** to make recommendations. Each notebook also includes a basic **evaluation using RMSE**.

---

## 📁 Files

* `item_based.ipynb`: Recommender using item-item similarity (movie-based).
* `user_based.ipynb`: Recommender using user-user similarity.
* `ratings.csv`: User ratings dataset (columns: `user_id`, `movie_id`, `rating`, `timestamp`).
* `movies.csv`: Movie metadata (columns: `movie_id`, `title`, `genres`).
* `README.md`: Project documentation.

---

## 📌 Methodology

### 1. Data Preparation

* Load `ratings.csv` and `movies.csv` using Pandas.
* Create a matrix using `pivot_table`.
* Fill missing ratings with `0` for similarity computation.

### 2. Similarity Calculation

* **Item-Based**: Cosine similarity between movie columns (`.T` transpose of the matrix).
* **User-Based**: Cosine similarity between user rows (no transpose).

### 3. Recommendations

* For a given movie/user:

  * Retrieve similarity scores.
  * Sort and pick the top N similar movies/users.
  * Merge with `movies.csv` to get metadata (title, genre).
  * Return a ranked list with similarity scores.

### 4. Evaluation

* A small subset of the ratings data is used.
* Predicted ratings are computed as a weighted average of similar users/items.
* **RMSE (Root Mean Squared Error)** is calculated to evaluate prediction accuracy.

---

## Requirements

* Python 3.x
* Pandas
* scikit-learn
* numpy

Install dependencies with:

```bash
pip install pandas scikit-learn numpy
```

---

## Evaluation Metric: RMSE

I used **RMSE (Root Mean Squared Error)** to compare predicted vs actual ratings.

$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (pred_i - actual_i)^2}
$$

* Lower RMSE = better predictions.
* Evaluated separately in each notebook.

---

## How to Use

1. Place `ratings.csv` and `movies.csv` in the same directory.
2. Open and run the Jupyter notebooks:

   * `item_based.ipynb`
   * `user_based.ipynb`
    
3. Use `recommend_movies(movie_id)` or `recommend_movies(user_id)` in the relavent notebook to get movie recommendations .
4. Run the evaluation cell to compute RMSE.

---

## Concepts Used

* Collaborative Filtering
* Cosine Similarity
* Pandas Pivot Tables
* Recommender Systems
* RMSE Evaluation
