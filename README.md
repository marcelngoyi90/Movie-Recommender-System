# Movie Recommender System

An item-based collaborative-filtering project built with Python and the MovieLens 100K dataset.

## Overview

The system finds movies similar to a selected title by comparing user-rating patterns. It includes:

- loading and preprocessing MovieLens data;
- exploratory analysis of ratings and popularity;
- construction of a user–movie ratings matrix;
- similarity calculation with Pearson correlation;
- filtering recommendations by rating count;
- an example workflow using *Titanic (1997)*.

## Dataset

- `u.data` contains user, movie, rating, and timestamp records.
- `Movie_Id_Titles` maps movie identifiers to titles.

## Method

1. Calculate each movie's average rating and number of ratings.
2. Build a pivot table with users as rows and movies as columns.
3. Select a target movie and extract its ratings vector.
4. Compute Pearson correlations with other movies.
5. Remove candidates with insufficient rating support.
6. Rank the remaining titles by similarity.

## Technology

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Jupyter Notebook

## Limitations

- Correlations based on few overlapping ratings can be unstable.
- Recommendations are item-to-item rather than user-personalized.
- Sparse data creates reliability and cold-start problems.
- A dense ratings matrix does not scale well.
- Quality is not yet measured with Precision@K, Recall@K, or NDCG.
- Genres, plots, and semantic embeddings are not currently used.

## Next steps

- add a fixed evaluation protocol;
- compare cosine similarity and matrix factorization;
- build personalized top-N recommendations;
- incorporate metadata in a hybrid model;
- expose recommendations through an interactive application.
