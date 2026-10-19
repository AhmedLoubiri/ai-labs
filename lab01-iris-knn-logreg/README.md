# Lab 01: Iris classification (KNN vs Logistic Regression)

Explore the Iris dataset, then train and compare two supervised classifiers: **K-Nearest Neighbors** and **Logistic Regression**.

## Data

`data/Iris.csv`: 150 flowers, 3 balanced species (50 each), 4 features (sepal/petal length and width, in cm). No missing values.

Source of the Iris data: https://www.kaggle.com/datasets/uciml/iris

## Method

- `Id` dropped; features `SepalLengthCm`, `SepalWidthCm`, `PetalLengthCm`, `PetalWidthCm`; species encoded 0/1/2.
- One stratified 80/20 train/test split (`random_state=42`), shared by every model.
- KNN with k = 5, then k = 1…20; Logistic Regression (`max_iter=1000`).

## Results (test set, 30 samples)

| Model | Accuracy |
|-------|----------|
| KNN, k = 5 | 1.000 |
| KNN, best k = 3 | 1.000 |
| Logistic Regression | 0.967 |

Setosa is perfectly separable; the only error (Logistic Regression) is a Versicolor predicted as Virginica. With 30 test samples, the 1-sample gap means the two models are practically equivalent.

## Run

See the [root README](../README.md) for setup, then open `lab1.ipynb` and run all cells.