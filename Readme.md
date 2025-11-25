# Network Inversion for Training-Like Data Reconstruction

This repository explores how architectural and loss-design choices affect the ability of neural networks to leak training-like information through **network inversion**.  
The work extends the *Training-Like Data Reconstruction (TLDR)* framework by evaluating pooling types, loss formulations, and classifier families.

##  Overview

Neural networks trained for classification can unintentionally encode structured information about their training data. By optimizing a generator against a frozen classifier, it becomes possible to reconstruct *training-like* images—even without access to the original dataset.

This project provides a systematic study of factors that influence such reconstruction, including:

- **Pooling strategies** (Max Pooling vs. Average Pooling)  
- **Loss setups**, including a simplified **KKT-inspired consistency loss**  
- **Impact of model depth**  
- **CNNs vs. MLPs** under inversion  
- **Perturbation-consistency objectives** for stability

Experiments were conducted on **MNIST** and **FashionMNIST**.

##  Key Findings

- **Average Pooling leaks more structure** than Max Pooling, enabling significantly better reconstructions.  
- The **KKT-inspired loss** stabilizes training and reduces mode collapse.  
- **Shallow CNNs leak more information** than expected—sometimes outperforming deeper models in reconstructibility.  
- Even **MLPs**, despite lacking spatial priors, reveal surprising structural information during inversion.

##  Method Summary

### Generator
- Transposed-convolution architecture  
- Dual conditioning pathways:
  - Softmax-based vector conditioning  
  - Matrix-conditioning (class-indicator matrices)  
- Total objective combines CE, KL, cosine diversity, orthogonality, TV, pixel-range, perturbation consistency, and KKT losses.

### Classifiers
- Shallow CNNs (with either average or max pooling)  
- Multilayer perceptrons (MLPs)  
- Networks are **pretrained and frozen** during inversion.

##  Paper

This README summarizes the paper included in the repository:  
**“Network Inversion for Training-Like Data Reconstruction: Effects of Pooling and Loss Design”** :contentReference[oaicite:1]{index=1}

.

