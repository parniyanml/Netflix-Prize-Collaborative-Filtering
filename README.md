# Netflix Prize Collaborative Filtering

## Project Overview

This repository contains an implementation and comprehensive analysis of Modern Collaborative Filtering (CF) techniques designed to address the challenges of the Netflix Prize competition. The project explores the evolution of Recommender Systems from traditional Memory-based approaches to advanced Model-based and Hybrid architectures.

The core objective is to minimize the Root Mean Squared Error (RMSE) on the Netflix dataset, surpassing the original Cinematch algorithm by leveraging Matrix Factorization, Deep Learning, and ensemble methods.

## Table of Contents

- [Introduction](#introduction)
- [Methodology](#methodology)
    - [Memory-Based Techniques](#memory-based-techniques)
    - [Model-Based Techniques](#model-based-techniques)
    - [Hybrid Systems](#hybrid-systems)
- [Advanced Architectures](#advanced-architectures)
    - [Collaborative Deep Learning (CDL)](#collaborative-deep-learning-cdl)
    - [Neural Collaborative Filtering (NCF)](#neural-collaborative-filtering-ncf)
    - [BellKor's Solution](#bellkors-solution)
- [Challenges Addressed](#challenges-addressed)
- [Evaluation Metrics](#evaluation-metrics)
- [Datasets](#datasets)

## Introduction

Recommender systems are essential tools in the modern information era, filtering vast amounts of data to provide personalized content. This project focuses on the Netflix Prize challenge (launched in 2006), which utilized a dataset of over 100 million ratings from 480,000 users on 17,770 movies. The goal was to improve prediction accuracy by at least 10% over existing baselines.

## Methodology

### Memory-Based Techniques
We implemented neighborhood-based algorithms that utilize the entire user-item database to generate predictions.
* **User-Based Filtering:** Predicts ratings based on the preferences of similar users.
* **Item-Based Filtering:** Recommends items similar to those a user has liked in the past.
* **Similarity Metrics:** Pearson Correlation and Cosine Similarity.

### Model-Based Techniques
These techniques use data mining and machine learning algorithms to learn complex patterns and reduce dimensionality.
* **Matrix Factorization:** Singular Value Decomposition (SVD) and Probabilistic Matrix Factorization (PMF).
* **Clustering Models:** Grouping users or items to improve scalability.
* **Bayesian Models:** Utilization of Naive Bayes and advanced Bayesian networks.

### Hybrid Systems
To overcome the limitations of individual techniques (such as the cold-start problem), we implemented hybrid strategies:
* **Weighted Hybrid:** Combining results from multiple recommenders numerically.
* **Switching Hybrid:** Swapping between algorithms based on confidence levels.
* **Content-Boosted CF:** Using content descriptors to fill sparse matrices before applying CF.

## Advanced Architectures

### Collaborative Deep Learning (CDL)
A hierarchical Bayesian model that tightly couples Stacked Denoising Autoencoders (SDAE) with Probabilistic Matrix Factorization (PMF).
* **Mechanism:** Learns deep representations from content information (e.g., movie plots, article abstracts) while simultaneously performing collaborative filtering.
* **Generative Process:** Bayesian SDAE handles the content information, acting as a prior for the latent factors in the rating matrix.
* **Advantage:** significantly outperforms baselines in sparse data conditions.

### Neural Collaborative Filtering (NCF)
A general framework replacing the inner product of Matrix Factorization with a neural architecture.
* **GMF (Generalized Matrix Factorization):** A linear kernel to model user-item interactions.
* **MLP (Multi-Layer Perceptron):** A non-linear kernel to learn complex interaction functions.
* **NeuMF:** A fused model combining GMF and MLP to leverage both linearity and non-linearity, optimized using Log Loss with negative sampling.

### BellKor's Solution
An analysis of the winning team's approach, "BellKor's Pragmatic Chaos."
* **Temporal Dynamics:** Modeling how user biases and movie popularity drift over time.
* **Restricted Boltzmann Machines (RBM):** Using neural networks to model latent factors.
* **Frequency Modeling:** Accounting for the frequency of user ratings in specific time windows.

## Challenges Addressed

The implementation specifically targets common recommender system issues:
* **Sparsity:** Handling the lack of rating data in the user-item matrix.
* **Cold Start:** Generating recommendations for new users or items with no history.
* **Scalability:** Ensuring algorithms perform efficiently as user/item counts grow.
* **Synonymy:** Managing items that are different but semantically similar.

## Evaluation Metrics

The performance of the models is evaluated using the following metrics:
* **RMSE (Root Mean Squared Error):** The primary metric for the Netflix Prize.
* **MAE (Mean Absolute Error):** Measures the average magnitude of errors.
* **Recall@K:** Evaluates the proportion of relevant items found in the top-K recommendations (crucial for implicit feedback scenarios).
* **NDCG (Normalized Discounted Cumulative Gain):** Measures ranking quality.

## Datasets

* **Netflix Prize Dataset:** The primary source for training and evaluation.
* **CiteULike:** Used for evaluating the CDL model on article recommendations.
* **MovieLens & Pinterest:** Used for benchmarking the NCF and NeuMF models.

