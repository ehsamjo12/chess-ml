# Chess Game Outcome Prediction

Predicting whether White wins a chess game, using only information that is known before the game starts: the players' ratings, the time control, the time of day and the opening.

## Dataset

20,000 randomly sampled rated games from the Lichess open database (June 2013), released under CC0.

- https://database.lichess.org/
- https://huggingface.co/datasets/Lichess/standard-chess-games

`notebooks/data_prep.ipynb` downloads the raw month of games, removes usernames and game links, and saves the sample to `dataset/chess_games.csv`.

## Project Structure

- `dataset/chess_games.csv` – the cleaned sample used in the project
- `notebooks/data_prep.ipynb` – downloading and preparing the data
- `notebooks/chess.ipynb` – EDA, preprocessing, model training, tuning and evaluation

## Work Done

- Exploratory Data Analysis (EDA)
- Checking the Elo formula against real results
- Finding and removing data leakage (rating change, number of moves, termination)
- Data cleaning and preprocessing
- Feature engineering (rating difference, average rating, ECO group)
- Machine learning: Elo baseline, Decision Tree, Gaussian Naive Bayes, KNN, SGDClassifier and my own logistic regression written with numpy
- Model evaluation (confusion matrices, ROC and precision-recall curves)

## Results

All models end up at around 66% accuracy on the test set, which is about the same as simply predicting that the higher-rated player wins (65.7%). The best model, SGDClassifier, reached 66.1% accuracy and an AUC of 0.723. The rating difference explains almost everything the models can learn before a game starts.

## How to Run

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```
