# Innovation in Bank Simulation.

# Advanced Bank Management and Simulation System

A C-based banking simulation system with an integrated neural network for customer churn and credit risk prediction — built from scratch without any external ML libraries.

> **Course:** Foundations of Programming (CSE10010)  
> **Institution:** MIT World Peace University, Pune  
> **Team:** Sagnik Das, Parth Gawade, Shreeraj Hujare, Unmesh Shinde, Rajneesh Bandwal

---

## What This Project Does

This project combines two things:

1. **A banking simulation** — a menu-driven C program that lets you create accounts, deposit/withdraw money, take loans, make payments, and apply monthly interest.
2. **A machine learning engine** — a feedforward neural network written in pure C that trains on real bank customer data to predict whether a customer is likely to churn (leave the bank).

The goal was to go beyond basic record-keeping and show that a low-level language like C can handle actual AI-style predictive analytics.

---

## Files

| File | Description |
|------|-------------|
| `bank_simulation.c` | Core banking system with account management and loan features |
| `test.c` | Neural network for churn/credit risk prediction |
| `Bank Customer Churn Prediction.csv` | Dataset used to train and evaluate the model (not included — see below) |

---

## Banking Simulation Features

- Create a bank account
- Deposit and withdraw funds
- Take a loan (with automatic interest calculation)
- Repay loans (with a 10% minimum payment rule)
- Apply monthly interest on outstanding loans
- View full account details

---

## Neural Network — How It Works

The ML model is a custom feedforward network implemented entirely in C using only the standard library.

**Architecture:**
- **Input Layer:** 10 features (Credit Score, Age, Tenure, Balance, etc.)
- **Hidden Layer:** 16 neurons with ReLU activation
- **Output Layer:** 2 neurons with Softmax (Churned / Not Churned)

**Training:**
- Optimizer: Stochastic Gradient Descent (SGD)
- Learning Rate: 0.01
- Batch Size: 32
- Epochs: 300
- Train/Test Split: 80/20

The CSV is parsed using `strtok()`, non-predictive columns (row number, customer ID, name) are skipped, and all features are min-max normalized before training.

---

## How to Run

### Banking Simulation
```bash
gcc bank_simulation.c -o bank
./bank
```

### Neural Network (Churn Predictor)

You'll need the [Bank Customer Churn Prediction dataset](https://www.kaggle.com/datasets/shantanudhakadd/bank-customer-churn-prediction) from Kaggle. Place the CSV in the same directory as `test.c`.
```bash
gcc test.c -o churn_model -lm
./churn_model
```

---

## Results

The model was trained and evaluated on the Kaggle churn dataset:

- **Training Epochs:** 300  
- **Train Split:** 80%  
- **Risk Categories:** High, Average, Low  

Accuracy and loss are printed every 50 epochs during training.

---

## Key Implementation Highlights

- Backpropagation implemented manually with gradient accumulation over mini-batches
- Numerically stable softmax (uses max subtraction before exponentiation)
- He initialization for weights (`sqrt(2/n)` scaling)
- No external ML libraries — pure C with `<math.h>` only

---

## Team

| Name | Roll Number |
|------|------------|
| Sagnik Das | 1262252179 |
| Parth Gawade | 1262252552 |
| Shreeraj Hujare | 1262252072 |
| Unmesh Shinde | 1262251711 |
| Rajneesh Bandwal | 1262250783 |
