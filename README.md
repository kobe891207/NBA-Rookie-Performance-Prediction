# NBA Rookie Performance Prediction

Predicting NBA rookies' future performance using:

- Ensemble Similarity Measures
- Deep Learning (MLP)
- NBA statistical analysis

This project is based on my master's thesis at National Yang Ming Chiao Tung University.

---

# Project Overview

This project predicts NBA rookies' average performance during seasons 4–6 based on their first 3 NBA seasons.

Two prediction methods are proposed:

1. Ensemble Similarity Measures Model
2. Multilayer Perceptron (MLP)

The project compares the proposed methods with:
- Linear Regression
- Support Vector Regression (SVR)

---

# Features

The model uses 16 NBA statistics, including:

- PTS
- REB
- AST
- STL
- BLK
- FG%
- 3P%
- USG%

and other advanced shooting statistics.

---

# Method 1: Ensemble Similarity Model

The similarity model combines four similarity measures:

- WMSE
- PSNR
- UQI
- VIF

The model searches for the most similar historical NBA players and predicts future performance using weighted averages.

---

# Method 2: Deep Learning (MLP)

The MLP model:

- Input dimension: 48
- Hidden layer: 64 nodes
- Activation: ReLU
- Regularization applied to prevent overfitting

---

# Results

Average prediction accuracy reached approximately 88%.

Best performance:
- Similarity model performs well on PTS prediction
- MLP performs best on AST prediction

---

# Technologies Used

- Python
- NumPy
- Pandas
- Scikit-learn
- PyTorch
- OpenPyXL

---

# Thesis

Master Thesis:
"Three-Year Performance Prediction for NBA Rookies Using an Ensemble of Similarity Measures and Deep Learning Models"

---

# Future Improvements

- Add more historical player data
- Improve prediction for big men
- Try Transformer / XGBoost models
- Deploy as a web application
