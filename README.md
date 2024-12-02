The goal of Task 1 was to implement a user-based collaborative filtering approach using k-Nearest Neighbors to predict movie ratings.
Approach:
I started by creating a user-item matrix, where rows represent users and columns represent movies. Each cell contains the rating given by a user to a movie.
I implemented collaborative filtering using two similarity metrics: cosine and Pearson correlation.
I tested various values for k, the number of nearest neighbors, to find the optimal configuration.

Results:
After evaluating RMSE, I found that the best results were achieved with k=5 and using cosine similarity.
The optimal RMSE with these settings was 2.4978, indicating that lower values of k and the cosine metric offered better prediction accuracy.
Findings:
While KNNCF provided reasonable predictions, its accuracy decreased as k increased.
Limitations of KNNCF include sparsity in the user-item matrix, where many users haven’t rated certain movies, and a cold start problem, which occurs with new users or movies with minimal ratings.

In Task 2, I shifted to a matrix factorization approach using Singular Value Decomposition (SVD) to improve recommendation quality.
Approach:
I decomposed the user-item matrix using SVD to reduce its dimensionality and capture latent factors that represent user and movie features.
I tested two configurations:
An initial model with 20 latent factors (k=20).
An improved model with 50 latent factors (k=50) to see if increasing dimensionality would improve accuracy.

Results:
For k=20, the RMSE was 2.4162 for the full matrix and 2.5044 for a subset of five selected movies.
Increasing to k=50 reduced the RMSE to 2.2374 for the full matrix and 2.3775 for the selected movies.
Findings:
Increasing the number of latent factors helped improve the accuracy, indicating that a higher-dimensional representation can better capture user preferences.
However, sparsity and cold start issues remain limitations. Although matrix factorization is more robust, it still requires a sufficient number of ratings for accurate predictions.

In Task 3, I compared the recommendation quality of the two models—KNNCF from Task 1 and the improved matrix factorization model from Task 2 (IMFR)—using ranking-based metrics.
Approach:
I selected 10 test users who had rated over 100 movies.
I evaluated the models using two metrics:
Average Precision (AP), which measures how relevant the recommendations are.
Normalized Discounted Cumulative Gain (NDCG), which assesses the ranking quality, giving more importance to items at the top of the list.

IMFR outperformed KNNCF across both metrics.AP for KNNCF was significantly lower than IMFR, indicating less precise recommendations.
NDCG for KNNCF was also lower, meaning KNNCF did not rank relevant items as effectively as IMFR.
Bar charts of AP and NDCG comparisons visually highlight the performance gap, where IMFR consistently scored higher.Findings:
IMFR provides better relevance and ranking than KNNCF, making it a stronger recommendation model for this dataset.
The higher AP and NDCG scores indicate that IMFR not only recommends relevant movies but also ranks them more effectively, which is crucial for user satisfaction in recommendation systems.
Limitations of KNNCF:
KNNCF struggled with accuracy due to sparsity in the user-item matrix. The limited overlap in ratings among users reduces the effectiveness of the similarity-based approach.
Additionally, the fixed value of k may not capture the diverse preferences among users as well as IMFR does.
Why IMFR Performs Better:
IMFR leverages latent factors to reveal hidden patterns in user behavior, enabling it to make more informed predictions.
Matrix factorization inherently handles sparse data better than neighbor-based approaches, making it more scalable and effective for large datasets.

