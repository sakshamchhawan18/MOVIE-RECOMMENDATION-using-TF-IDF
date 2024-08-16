# MOVIE-RECOMMENDATION-using-TF-IDF
Here's a more visually engaging version of the explanation, suitable for a GitHub README, using emojis and formatting:

---

# 🎥 Movie Recommendation System (2024) using TF-IDF

Welcome to the **Movie Recommendation System** project! This repository demonstrates how to build a basic movie recommendation engine using **TF-IDF** and **cosine similarity**. Let's dive into the step-by-step process! 🚀

## 📚 1. Importing Libraries:
- **NumPy & Pandas**: For numerical operations and data manipulation. 🧮
- **JSON & Matplotlib**: Handling JSON data and creating visualizations (though not used here). 🖼️
- **OS & ZipFile**: Managing file paths and extracting compressed files. 📂
- **Sklearn**: For machine learning tasks. We use `TfidfVectorizer` to convert text into numerical features and `cosine_similarity` to calculate movie similarities. 🤖
- **Pickle**: For saving and loading models. 🥒

## 📥 2. Downloading the Dataset:
- A Kaggle dataset containing data on 930,000 movies is downloaded. This dataset is your playground! 🎬

## 📦 3. Extracting the Dataset Files:
- The dataset, stored in `madhurima.zip`, is extracted to make it ready for analysis. 🗂️

## 📝 4. Loading the Dataset:
- The dataset is loaded into a Pandas DataFrame called `moviedata` from the file `TMDB_movie_dataset_v11.csv`. 🧑‍💻

## 🔍 5. Inspecting the Dataset:
- `moviedata.head(5)`: Displays the first five rows of the dataset.
- `moviedata.dtypes`: Shows the data types of each column in the dataset.
- `row1=moviedata.iloc[0]`: Takes a closer look at the first row of data, helping us understand the structure. 🧐

## 🏷️ 6. Creating a 'tags' Column:
- A new column `tags` is created by combining key columns like `title`, `genres`, `overview`, `original_title`, and `keywords`. This text data will be used to generate the TF-IDF matrix. ✍️

## 🔗 7. Mapping Movie Titles to Their Index:
- We create a mapping `movie2idx` where each movie title is linked to its index in the DataFrame. This makes finding a movie's index easier when generating recommendations. 🗺️

## 🧠 8. Instantiating and Fitting the TF-IDF Vectorizer:
- **`TfidfVectorizer(max_features=6000)`**: Converts the `tags` column into a matrix of TF-IDF features, limiting the vocabulary to 6000 terms. 🛠️
- **`M1 = tfvectorizer.fit_transform(moviedata['tags'].values.astype('U'))`**: The vectorizer is fitted to the `tags` column, transforming it into a sparse matrix where each row represents a movie and each column represents a term. 🧬

## 💾 9. Storing the Model Using Pickle:
- The TF-IDF matrix `M1` is saved as `M1.pkl` using Pickle, allowing easy loading and reuse without reprocessing the text. 📀

## 🔄 10. Loading the Model:
- The saved model is loaded from `M1.pkl` using Pickle, making it ready for use in recommendations. 🚀

## 🎯 11. Getting Movie Recommendations:
- **`get_recommendations(model, movie)`**: This function takes a TF-IDF model and a movie title, finds the movie’s index, and computes the cosine similarity between this movie and all others in the dataset.
   - **`idX=find_index(movie)`**: Finds the index of the movie in the DataFrame.
   - **`result= (-(cosine_similarity(model[idX],model).flatten())).argsort()[1:6]`**: Computes the cosine similarity of the target movie with all others, sorts them, and returns the top 5 most similar movies. 🎯
   - **`print(moviedata['title'].iloc[result])`**: Prints the titles of the recommended movies. 📽️

## 🔍 12. Example Usage:
- **`get_recommendations(loaded_vectorizer,'Toy Story')`**: Try this function to see the top 5 movies most similar to *Toy Story*! 🍿

## 📝 Summary:
This project is a simple yet effective implementation of a content-based movie recommendation system. Using **TF-IDF** to represent movies as numerical vectors based on their text data, and **cosine similarity** to find and recommend movies that are most similar to a given movie. 

Happy coding! 💻✨
