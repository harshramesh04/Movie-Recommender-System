# Movie-Recommendation-System

- Overview​:

  - The dataset is a product of collaborative efforts from 138,493 users, each having provided ratings for a minimum of 20 movies.​ It is the MovieLens dataset from Kaggle: https://www.kaggle.com/datasets/grouplens/movielens-20m-dataset

- Dataset Insights​

  - Total Ratings: A vast collection comprising 20,000,263 user ratings.​

  - Tag Applications: Users have applied 465,564 tags to movies, reflecting additional layers of categorization and user engagement.​

  - Movies: The dataset encompasses a diverse set of 27,278 movies.​

  - Timeline: Data collection spans a significant period from January 09, 1995, to March 31, 2015, providing a temporal dimension to user interactions.
    
- Files in the dataset:
  - ​Tag.csv:  userId, movieId, tag, timestamp.​
  - Rating.csv: userId, movieId, rating, timestamp​
  - Movie.csv: movieId, title, genres ​
  - Link.csv: imdbId, tmdbId​
  - Genome_scores.csv: movieId, tagId, relevance​
  - Genome_tags.csv:  tagId, tag
 
- Data Preprocessing and Modelling

  - Handling Null Values:​ Checked for null values in all files.​ Removed null values, considering the dataset's size and the negligible amount of missing data.​
  - Timestamp Conversion:​ Converted timestamp columns to datetime format.​ Extracted year and month from the timestamp for better exploratory data analysis (EDA).​
  - Column Exploration  & Processing:​ Explored unique values in columns across all files to gain a deeper understanding of the data.​ In the movies.csv file, genres were separated by pipes ('|').​ Converted the genres column into a list for more effective data analysis.
  - Movie Title Processing:​ Separated movie names from the release date year in the title column to create an additional column for better EDA.​
  - Merging DataFrames:​ Used a left join to merge the movies.csv and rating.csv DataFrames based on the common column 'movieId'.​ Resulted in a new DataFrame that facilitated data analysis and provided insights into movie ratings.​
  - Popular Movie List:​ Created a new DataFrame to count the number of votes each movie received by considering the ratings given.​ Created another DataFrame to calculate the average rating for each movie.​ Merged the two DataFrames, yielding a list of popular movies with the number of ratings given by users and their average ratings.​ These preprocessing steps lay the foundation for subsequent exploratory data analysis and modeling. 

- Proposed Models
  - Matrix Factorization
      - A matrix factorization movie recommendation system predicts user preferences using user-item rating data. The big user-item rating matrix is decomposed into smaller, latent component matrices representing users and objects. ​These latent variables represent fundamental qualities that influence user preferences and item attributes. The method predicts missing ratings by multiplying these matrices, suggesting prospective user interest in unwatched movies.
          - We use the movies dataset and rating dataset, we then merge and check if all the data match. ​
          - We then define a list of movies, It begins by filtering a DataFrame for certain movies, then produces a Surprise dataset and divides it into training and test sets. ​
          - This data is used to train the SVD model, which is then assessed using RMSE. Finally, it predicts a rating for a given user-item pair, illustrating how the model may be employed to predict user preferences for movies.
            
  - Item-based Collaborative Filtering
      - Item-based collaborative filtering is a recommendation system approach that provides individualized recommendations to users based on their preferences and the preferences of other users. It is a type of collaborative filtering that relies on item similarity rather than user preference.​ Item-based collaborative filtering generates suggestions by finding items that are comparable to those that a user has already expressed interest in.
          - Step 1 – Merge movies and rating dataset​
          - Step 2 - Count number of times a movie appear, filter out rare ones​
          - Step 3 - Establish Boolean Mask​
          - Step 4 - Restructure data using Pivot Table​
          - Step 5 – Find similar movies using Correlation​
            
  - Neural Network based Collaborative Filtering
      - The Neural Network-based Collaborative Filtering (CF) model employs a deep learning method for recommendation systems. ​Using implicit feedback, we will train a recommender system. We siimply binarize the ratings such that they are '1' (i.e. positive class) to transform this dataset into an implicit feedback dataset. The number '1' indicates that the user watched the movie.​ This approach represents users and items as embeddings, which are low-dimensional vectors that capture their attributes. ​The embeddings of the user and items are fed into a neural network, which learns to predict ratings based on these embeddings. ​When compared to standard matrix factorization algorithms, our method captures complicated and non-linear interactions between users and things, resulting in more accurate suggestions.​
   
- Results
  - Matrix Factorization – Best Score = 0.891​
  - Item based Collaborative Filtering – As it works based on correlation, we get a different set of recommendations for different users based on the movies that they have watched.
  - Neural Network based Collaborative Filtering - We get a hit of 0.84, which means that 84% of the users got recommended the movie from the top 10 that they have interacted with. Which is a satisfactory score. ​

- References

  - https://towardsdatascience.com/neural-collaborative-filtering-96cef1009401
  - https://www.mygreatlearning.com/blog/matrix-factorization-explained/
  - https://towardsdatascience.com/item-based-collaborative-filtering-in-python-91f747200fab
  - https://medium.com/data-science-in-your-pocket/recommendation-systems-using-neural-collaborative-filtering-ncf-explained-with-codes-21a97e48a2f7
  - https://towardsdatascience.com/fast-ai-season-1-episode-5-1-movie-recommendation-using-fastai-a53ed8e41269


