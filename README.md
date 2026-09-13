# Hybrid Movie Recommendation System

This repository contains the project developed for the course **Numerical Analysis for Machine Learning** (NAML), taught by **Prof. Edie Miglio** at **Politecnico di Milano** (A.Y. 2024-2025). The project received **full marks**.

## Authors
* Simone Mauro
* Lorenzo Meroi

---

## Project Overview
The project implements and evaluates the hybrid recommendation framework described in the research paper *"Hybrid Movie Recommendation System with User Partitioning and Log Likelihood Content Comparison"* (published in IEEE Access). The system is designed to provide movie recommendations while overcoming the cold-start problem (for both new users and new items) and dealing with rating matrix sparsity.

The model is built on three core pillars:

1. **Collaborative Filtering via Matrix Factorization**: 
   * Decomposes the rating matrix using Alternating Least Squares (ALS) to extract user and item latent feature representations.
   * Utilizes L2 regularization to prevent overfitting and K-Fold Cross-Validation for hyperparameter validation.
2. **User Demographic Partitioning (User Cold-Start Resolution)**:
   * Groups users based on demographic traits: age (binned category distance), gender (binary matching), and genre preferences (Jaccard similarity on top-rated genres).
   * Combines these vectors into an aggregated demographic similarity matrix.
   * Employs **Particle Swarm Optimization (PSO)** to compute the optimal weight configurations for demographic vs. collaborative latent similarity.
3. **Content-Based Movie Similarity (Item Cold-Start Resolution)**:
   * Dynamically mines movie descriptions using the Wikipedia API.
   * Computes statistical weights for words using **Log-Likelihood (LL)** weighting rather than traditional TF-IDF to capture distinct corpus characteristics.
   * Generates Continuous Bag-of-Words (CBOW) Word2Vec embeddings (vector size 300, window 10) to map textual data to low-dimensional vector representations.
   * Evaluates item similarities using a combined score of Cosine similarity and RV coefficients.

---

## Evaluation Results
The combined prediction matrix merges Matrix Factorization, demographic user similarities, and content-based item similarities. The weights for ensembling were optimized using a grid search:
* **MovieLens 100K Dataset**: Reached a final Root Mean Square Error (RMSE) of **1.0158** (using weights $\alpha = 0.5$, $\beta = 0.5$).
* **MovieLens 1M Dataset**: Reached a final RMSE of **0.9189** (using weights $\alpha = 0.6$, $\beta = 0.4$).

---

## Deliverables and Repository Structure
* **[Meroi_Mauro.ipynb](./Meroi_Mauro.ipynb)**: The complete project implementation notebook in Python. It details data wrangling, ALS matrix factorization, demographic similarity computation, PSO implementation, Wikipedia web scraping, Word2Vec modeling, Log-Likelihood text weighting, evaluation loops, and tables.
* **[Meroi_Mauro.pdf](./Meroi_Mauro.pdf)**: The detailed LaTeX-compiled project report, detailing the mathematical formulations, algorithms, and empirical analyses.
* **[Hybrid_Movie_Recommendation_System_with_User_Parti 1.pdf](./Hybrid_Movie_Recommendation_System_with_User_Parti\s1.pdf)**: The original reference paper by Yangyong Mao, Kampol Woradit, and Kenneth Cosh.
* **[LICENSE](./LICENSE)**: MIT License.

---

## Policy on Original Paper Inclusion
The original paper **[Hybrid_Movie_Recommendation_System_with_User_Parti 1.pdf](./Hybrid_Movie_Recommendation_System_with_User_Parti\s1.pdf)** is included in this repository. 

**Copyright & License Compliance**:
This article was accepted for publication in **IEEE Access** and is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. Under this license, sharing and redistributing the PDF is permitted as long as appropriate credit is given to the authors (Yangyong Mao, Kampol Woradit, and Kenneth Cosh) and the original DOI (`10.1109/ACCESS.2025.3529515`) and license conditions are preserved. Thus, the file can legally be kept in this public GitHub repository.

---

## License
This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.
