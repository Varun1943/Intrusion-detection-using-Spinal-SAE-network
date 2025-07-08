# Intrusion-detection-using-Spinal-SAE-network
this repo is an demonstration for using large datasets for supervised learning  Short Description:
An end-to-end intrusion detection system built with a Spinal Stacked AutoEncoder network trained on the Bot‑IoT dataset. Utilizes efficient Parquet data handling, class imbalance techniques, and a hybrid deep-learning architecture to detect cyber-attacks in IoT environments.

Project Overview
Data Format:
Uses Apache Parquet for efficient large-scale data handling. Parquet saves memory and accelerates I/O operations compared to CSV, essential for datasets with tens of millions of records 

Dataset:
Bot‑IoT consists of ~70 million flows covering DDoS, DoS, reconnaissance, theft, and normal traffic 
github.com

Preprocessing & Feature Engineering:

PCA-based dimensionality reduction for speed and efficiency

Temporal features (e.g., stime, dur) with Chebyshev distance augmentation 

Label encoding of categorical features (e.g., protocol, state)

Class Balancing:

RandomUnderSampler to reduce majority class

ADASYN to oversample minority classes

Combined approach yields ~350k balanced training samples 

Feature Selection:

Random Forest + Lasso regression to keep only the most discriminative features 

Model Architecture (SpinalSAENet):

Combines a Sparse AutoEncoder (for reconstruction & compression) with a SpinalNet-like classifier

Encoders enforce sparsity; classifier uses segmented layers improving gradient flow 
Loss & Optimization:

Uses Focal Loss to handle class imbalance effectively 

Trained via Adam optimizer with learning rate decay and early stopping

Performance:

Achieved 96–99 % accuracy, high precision/recall/F1 across attack categories 
Outperformed traditional ML (Decision Trees, Random Forests, SVMs)

Deployment Ready:
Model serialized with PyTorch (.pt)
Designed for real-time inference, tested on AWS EC2 with <200 ms latency 


Includes Docker/Kubernetes support
