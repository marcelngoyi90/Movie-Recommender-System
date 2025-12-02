# Movie-Recommender-System
A simple item tem collaborative filtering recommender built using Python and the MovieLens dataset


##  Overview
This project implements a **Movie Recommender System** using a correlation-based collaborative filtering approach.  
The system analyzes user ratings and identifies movies similar to a target movie by computing statistical correlations between rating patterns.

The notebook includes:

- Loading and preprocessing the MovieLens dataset  
- Exploratory data analysis (EDA)  
- Building a user–movie rating matrix  
- Computing similarity using Pearson correlation  
- Filtering recommendations by rating count  
- Example output using the movie **Titanic (1997)**  

This project serves as a beginner-friendly introduction to collaborative filtering.

---

##  Dataset

This system uses the **MovieLens 100K dataset**.

###  1. `Movie_Id_Titles`
A CSV file mapping each movie ID to its corresponding movie title.

###  2. `u.data`
A tab-separated file containing user ratings in the format:
The notebook merges both datasets to associate user ratings with movie titles.

---

##  Approach

###  1. Data Preprocessing
- Load datasets using `pandas`
- Merge movie titles into the ratings dataset
- Analyze rating distributions and movie popularity
- Compute:
  - Mean rating per movie  
  - Rating count per movie  

---

###  2. Build the User–Movie Rating Matrix
Using a pivot table:

- **Rows:** Users  
- **Columns:** Movie Titles  
- **Values:** Ratings  

This creates the foundation for item–item collaborative filtering.

---

###  3. Compute Movie Similarity (Pearson Correlation)

Steps used in the notebook:

1. Select a target movie (e.g., *Titanic*)  
2. Extract its rating vector  
3. Compute correlation with all other movies:

## Limitations

While this recommender system works well for demonstration and educational purposes, it has several important limitations:

### 1. Pearson Correlation Instability  
Pearson correlation becomes unreliable when two movies have very few overlapping ratings.  
This can result in **false high correlations** and noisy recommendations.

### 2. No Personalization  
The system only finds movies similar to a target movie, not to a specific user.  
All users receive the **same recommendations**, regardless of their personal preferences.

### 3. Sparse Data Issues  
The user–item matrix is highly sparse, causing:

- reduced accuracy  
- unstable similarity scores  
- difficulty capturing meaningful relationships  

### 4. Cold Start Problem  
- **New users** cannot be recommended movies until they rate some  
- **New movies** cannot be recommended until enough users rate them  

### 5. No Bias Correction  
Users have different rating behaviors (lenient vs strict).  
The model does not normalize for user-specific tendencies, affecting similarity results.

### 6. Scalability Constraints  
The pivoted user–movie matrix works only for small datasets like MovieLens 100K.  
For larger datasets, this approach becomes:

- slow  
- memory-heavy  
- impractical without sparse matrices or specialized libraries  

### 7. No Train/Test Split or Evaluation  
The system does not include:

- RMSE/MAE  
- Precision@K  
- Recall@K  
- NDCG  

So we cannot quantitatively measure recommendation quality.

### 8. No Hybrid or Content-Based Features  
The recommender relies only on user ratings and ignores valuable metadata such as:

- genre  
- year  
- cast  
- plot  
- embeddings  
