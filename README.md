# NBA Rookie Performance Prediction

Predicting NBA rookies' future performance using:

- Ensemble Similarity Measures
- Deep Learning (MLP)
- NBA statistical analysis

This project is based on my master's thesis at National Yang Ming Chiao Tung University (NYCU).

## Project Overview

This project predicts NBA rookies' average performance during seasons 4–6 based on their first 3 NBA seasons.

Two prediction methods are proposed:

1. Ensemble Similarity Measures Model
2. Multilayer Perceptron (MLP)

The project also compares the proposed methods with:

- Linear Regression
- Support Vector Regression (SVR)

The goal is to help evaluate whether rookie players may become future stars.

## Dataset

The player data was collected from **Basketball Reference**.

The project includes:

- 17 rookie players
- 53 historical NBA All-Star players

### All rookie players

- Entered the NBA between 2016–2018
- Played at least 6 seasons
- Had at least one NBA All-Star appearance

### All historical players

- Had at least one NBA All-Star appearance during 2015-2024

## Features

The model uses 16 basketball statistics.

| Feature | Description | Feature | Description |
|---|---|---|---|
| PTS | Points per 36 minutes | FG% | Field goal percentage |
| REB | Rebounds per 36 minutes | FGA | Field goal attempts |
| AST | Assists per 36 minutes | 2P% | 2-point percentage |
| STL | Steals per 36 minutes | 2PA | 2-point attempts |
| BLK | Blocks per 36 minutes | 3P% | 3-point percentage |
| TOV | Turnovers per 36 minutes | 3PA | 3-point attempts |
| PF | Personal fouls per 36 minutes | FT% | Free throw percentage |
| USG% | Usage percentage | FTA | Free throw attempts |

## Method 1: Ensemble Similarity Measures Model

This method compares rookie players with historical NBA players.

Four similarity measures are combined:

- Weighted mean square error (WMSE)
- Peak signal to noise ratio (PSNR)
- Universal quality index (UQI)
- Visual information fidelity (VIF)

The model finds the most similar historical players and predicts future performance using weighted averages.

### Workflow

1. Normalize player statistics
2. Compute similarity scores
3. Combine four similarity measures
4. Select top 5 similar players
5. Predict seasons 4–6 performance

### Similarity Formula

The final similarity score is computed by:

$$
Similarity(X, Y) = a \times WMSE + b \times PSNR + c \times UQI + d \times VIF
$$

The coefficients are computed using least squares.

### Prediction Formula

The final prediction is computed using the rookie player's own statistics and the top 5 most similar historical players.

$$
Prediction =\frac{600 \times X +\sum_{i=0}^{4}\left((5-i)\times top5_i \times A_i\right)}{600+\sum_{i=0}^{4}\left((5-i)\times top5_i\right)}
$$

Where:

| Symbol | Description |
|---|---|
| X | Rookie player's average statistics during the first 3 seasons |
| top5_i | Similarity score of the top 5 historical players |
| A_i | Average statistics of the historical player during seasons 4–6 |

## Method 2: Deep Learning (MLP)

The second method uses a Multilayer Perceptron (MLP).

### Model Structure

| Component | Value |
|---|---|
| Input Dimension | 48 |
| Hidden Layer | 64 nodes |
| Output Dimension | 16 |
| Activation Function | ReLU |
| Regularization | Yes |

The input contains the first 3 seasons of player statistics.

The output predicts the average statistics from seasons 4–6.

## Results

We use MAPE as our error function, the models achieved approximately **88% prediction accuracy**.

### Average Error

| Method | Average MAPE | Standard Deviation |
|---|---|---|
| Similarity Model | 0.1243 | 0.0625 |
| MLP | 0.1205 | 0.0712 |

### Comparison with Other Methods

| Method | PTS | REB | AST |
|---|---|---|---|
| Linear Regression | 0.0802 | 0.1081 | 0.1915 |
| SVR | 0.0892 | 0.1077 | 0.1467 |
| Similarity Model | 0.0859 | 0.1593 | 0.1961 |
| MLP | 0.1088 | 0.1396 | 0.1351 |

- Similarity model performs well on PTS prediction
- MLP performs best on AST prediction

## Example Predictions

### Donovan Mitchell (Similarity Model)

| Type | PTS | REB | AST | STL | BLK | TOV | PF | FG% | FGA | 2P% | 2PA | 3P% | 3PA | FT% | FTA | USG |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Reality | 27.9 | 4.6 | 5.7 | 1.3 | 0.2 | 3.1 | 2.5 | 0.444 | 22.0 | 0.507 | 12.1 | 0.368 | 9.9 | 0.849 | 5.6 | 32.8 |
| Prediction | 26.6 | 4.4 | 4.7 | 1.0 | 0.2 | 3.0 | 2.5 | 0.459 | 20.8 | 0.507 | 11.9 | 0.368 | 8.9 | 0.851 | 5.4 | 32.0 |


### Trae Young (MLP Model)

| Type | PTS | REB | AST | STL | BLK | TOV | PF | FG% | FGA | 2P% | 2PA | 3P% | 3PA | FT% | FTA | USG |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Reality | 27.5 | 3.3 | 10.4 | 1.1 | 0.1 | 4.2 | 1.7 | 0.442 | 19.9 | 0.491 | 12.1 | 0.365 | 7.8 | 0.884 | 8.1 | 32.7 |
| Prediction | 28.4 | 3.3 | 9.7 | 0.9 | 0.0 | 4.2 | 1.9 | 0.461 | 20.5 | 0.512 | 12.4 | 0.347 | 8.0 | 0.870 | 8.3 | 31.9 |

## How to Run
Run the Similarity Measures model
```
python Similarity.ipynb
```
Run Multilayer Perceptron
```
python MLP.ipynb
```
Run Linear Regression and SVR
```
python Linear_SVR.ipynb
```

## Tools

- Python
- NumPy
- Pandas
- Scikit-learn

## Thesis Information

**Title**

Three-Year Performance Prediction for NBA Rookies Using an Ensemble of Similarity Measures and Deep Learning Models

**Author**

Wei-Tse Sun

**University**

National Yang Ming Chiao Tung University, Applied Mathematics
