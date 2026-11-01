# Movie Recommendation System Using Collaborative Filtering

## Overview
A Python recommendation system that identifies movies with similar user-rating patterns using **item-based collaborative filtering**. Enter a movie title to receive up to 10 recommendations with similarity scores, rating counts, average ratings, and genres.

## Data
The [MovieLens Latest Small dataset](https://grouplens.org/datasets/movielens/latest/) from GroupLens Research contains **100,836 ratings**, **9,742 movies**, and **610 users**. The project uses `data/movies.xlsx` and `data/ratings.xlsx`; the original dataset documentation is preserved in `data/MovieLens_Dataset_README.txt`. Consult that documentation for attribution and terms of use.

## Method
1. Load and inspect movie metadata and ratings.
2. Subtract each user's mean rating from their ratings.
3. Build a sparse movie–user rating matrix using SciPy CSR.
4. Calculate cosine similarity between the selected movie and all rated movies.
5. Exclude the query movie and candidates with fewer than five ratings or nonpositive similarity.
6. Return the 10 highest-ranked recommendations.

## Tools
Python, pandas, NumPy, SciPy, scikit-learn, Jupyter, and openpyxl (for Excel input).

## Run locally
1. Install Python 3.10+.
2. From this project directory, run `python -m pip install -r requirements.txt`.
3. Start Jupyter with `jupyter lab` and open `Movie_Recommendation_System.ipynb`.
4. Run the cells in order. Change `favorite_movie` in the user input cell to search for another movie.

The notebook expects `data/movies.xlsx` and `data/ratings.xlsx` relative to the project folder. If Jupyter starts in a different working directory, open the notebook from this folder.

## Interpretation and limitations
The similarity score measures agreement in rating patterns, **not** the probability that a person will enjoy a film. Sparse ratings, limited user context, and cold-start titles restrict recommendation quality. No held-out recommendation-quality benchmark is reported, so this project demonstrates a working approach rather than validated production performance.

## References
- Harper, F. M., & Konstan, J. A. (2015). *The MovieLens Datasets: History and Context*. https://doi.org/10.1145/2827872
- Sarwar, B., Karypis, G., Konstan, J. A., & Riedl, J. (2001). *Item-based collaborative filtering recommendation algorithms*. https://doi.org/10.1145/371920.372071
