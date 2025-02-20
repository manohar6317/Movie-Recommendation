# Movie Recommendation System

This repository contains a movie recommendation system built using collaborative filtering with Singular Value Decomposition (SVD). It allows users to receive personalized movie recommendations based on their past ratings.

## Overview

The goal of this project is to provide users with accurate and relevant movie recommendations. The system takes into account user ratings and predicts how a user would rate a movie they haven't seen. This is achieved by implementing a matrix factorization approach using SVD.

## Project Structure
movie-recommendation/
movie-recommendation/
├── data/
│   ├── movies.csv
│   ├── ratings.csv
├── models/
│   └── svd_model.pkl
├── notebooks/
│   ├── data_exploration.ipynb
│   ├── model_training.ipynb
│   └── evaluation.ipynb
├── src/
│   ├── data_preprocessing.py
│   ├── recommendation_engine.py
│   └── utils.py
├── requirements.txt
├── README.md
├── app.py
└── Dockerfile
**Explanation of Key Files/Folders:**

*   **`data/`**:  Holds the movie and ratings data.
*   **`models/`**: Stores the trained SVD model.
*   **`notebooks/`**: Jupyter notebooks for exploration, training, and evaluation.
*   **`src/`**:
    *   `data_preprocessing.py`:  Loads, cleans, and transforms data.
    *   `recommendation_engine.py`:  Implements the SVD-based recommendation.
    *   `utils.py`:  Helper functions.
*   **`requirements.txt`**: Lists required Python packages.
*   **`app.py`**: Flask web application.
*    **`Dockerfile`**: Containerizes the application

## Dataset

The recommendation system is trained on the MovieLens 100K dataset. This dataset contains:

*   **`movies.csv`**:  Information about movies:
    *   `movieId`:  Unique identifier for each movie.
    *   `title`:  Movie title.
    *   `genres`:  A pipe-separated list of genres.
*   **`ratings.csv`**:  User ratings for movies:
    *   `userId`: Unique identifier for each user.
    *   `movieId`:  Unique identifier for each movie.
    *   `rating`:  Rating given by the user (on a scale of 1-5).
    *   `timestamp`:  Timestamp of the rating.

**Important Notes about the Dataset:**

*   **Source:** MovieLens 100K dataset (https://grouplens.org/datasets/movielens/100k/).
*   **Size:**  100,000 ratings, 9,742 movies, 610 users.
*   **Preprocessing:**  Missing values were handled (if any), and data types were converted appropriately.  The `ratings.csv` file was used to create a user-item matrix for SVD.
*    **Licensing**: The MovieLens datasets are provided and governed under their own terms of use, as described on the GroupLens website.

## Installation and Setup

1.  **Clone the repository:**

    ```bash
    git clone [https://github.com/manohar6317/Movie-Recommendation.git](https://github.com/manohar6317/Movie-Recommendation.git)
    cd Movie-Recommendation
    ```

2.  **Create a virtual environment (recommended):**

    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Linux/macOS
    venv\Scripts\activate  # On Windows
    ```

3.  **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

## Usage

**Running the Recommendation Engine:**

1.  **Ensure the data is in the `data/` directory.**
2.  **Load the pre-trained model:** The `recommendation_engine.py` script automatically loads the `svd_model.pkl` file from the `models/` directory.
3.  **Run the Flask App:**

    ```bash
    python app.py
    ```
   Then, open your web browser and go to `http://localhost:5000`.  The web application allows you to enter a user ID and get top N movie recommendations.

**Jupyter Notebooks:**

The `notebooks/` directory contains Jupyter notebooks:

*   **`data_exploration.ipynb`**: Explore the dataset.
*   **`model_training.ipynb`**: Train the SVD model.
*   **`evaluation.ipynb`**: Evaluate the model.

To run a notebook:

```bash
jupyter notebook
```

Run `jupyter notebook` and navigate to the `notebooks/` directory.

*   `data_exploration.ipynb`: Data exploration.
*   `model_training.ipynb`: Model training.
*   `evaluation.ipynb`: Model evaluation.

**Running with Docker:**

1.  **Build:**

    ```bash
    docker build -t movie-recommender .
    ```

2.  **Run:**

    ```bash
    docker run -p 5000:5000 movie-recommender
    ```

## Model Evaluation

Evaluated using RMSE on an 80/20 split:

| Metric | Value |
| ------ | ----- |
| RMSE   | 0.87  |

The model significantly outperforms a baseline (RMSE 1.06) that always recommends the average rating. See `evaluation.ipynb` for details.

## Future Improvements

*   Incorporate more user features.
*   Experiment with different algorithms.
*   Improve the UI.
*   Cloud deployment.
*   Address the cold start problem.
*   Add explanations.

## Contributing

Contributions are welcome!  Follow these steps:

1.  Fork the repository.
2.  Create a new branch: `git checkout -b feature/your-feature-name`
3.  Make changes and commit: `git commit -m "Your message"`
4.  Push: `git push origin feature/your-feature-name`
5.  Create a pull request.

## License

This project is licensed under the MIT License
## Acknowledgments

*   MovieLens dataset (GroupLens, University of Minnesota).
*   Scikit-surprise library.
*   Flask framework.
