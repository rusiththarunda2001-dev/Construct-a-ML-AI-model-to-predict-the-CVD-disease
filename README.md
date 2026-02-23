

# CVD-Detection-via-Multimodal-Transfer-Learning

## Overview

This project builds upon the state-of-the-art **MuFuBP-Net** architecture—a multimodal fusion network originally designed for cuffless Blood Pressure (BP) estimation. Our implementation expands the original dual-pipeline (ECG and PPG) into a **triple-signal pipeline** by integrating **respiratory signals** to enhance physiological context.

The system is trained in two phases:

1. 
**Pre-training:** Leveraging the **MIMIC-II dataset** to train the core MuFuBP-Net architecture for robust feature extraction from physiological waveforms.


2. **Transfer Learning:** Utilizing the pre-trained weights to perform downstream classification for the identification of various **Cardiovascular Diseases (CVD)**.

## Key Features

* 
**Expanded Triple-Signal Pipeline:** While the original MuFuBP-Net focuses on ECG and PPG , this project introduces a third channel for **respiratory signals** to capture a more holistic view of the user's autonomic regulation.


* 
**Hierarchical & Modality-Specific Learning:** Utilizes **Residual Self-Encoding (ReSE)** to extract high-fidelity features while preventing signal degradation.


* 
**Cascading Cross-Feature Enhancer (CCFE):** Integrates multimodal features using an adaptive squeeze-and-excitation (SE) mechanism for dynamic re-weighting of signal importance.


* 
**Probabilistic Feature Encoder (PFE):** A VAE-inspired module that compresses aggregated features into a 64-dimensional latent space, eliminating redundancy while preserving discriminative characteristics for CVD detection.


* 
**Sequence Context Network (SCN):** Employs bidirectional LSTM layers to capture long-range temporal dependencies across multiple cardiac and respiratory cycles.



## Architecture

The model architecture is composed of seven interactive modules adapted for triple-signal input:

1. 
**ReSE Block:** Independent residual blocks for ECG, PPG, and Respiratory signals.


2. 
**CCFE Module:** Cross-modal learning and channel-wise attention.


3. 
**SCN Module:** Global sequential feature extraction.


4. 
**MoTFE Module:** Captures local morphological and short-term temporal patterns.


5. 
**Multi-Scale Fusion:** Concatenates hierarchical and modality-specific features.


6. 
**Probabilistic Encoder:** Maps features to a compact latent space using the reparameterization trick.


7. **CVD Classifier:** Replaces the original BP regressor with a classification head for disease identification.

## Dataset & Preprocessing

* 
**Source:** MIMIC-II Waveform Database.


* 
**Windowing:** 8-second non-overlapping segments.


* 
**Synchronization:** Peak-wise alignment relative to ECG R-peaks to ensure temporal coherence across all three modalities.


* 
**Filtering:** Butterworth bandpass filtering for noise reduction and baseline wander correction.



## Technical Stack

* 
**Language:** Python 3.8 


* 
**Framework:** PyTorch 1.7.1 


* 
**Signal Processing:** BioSPPy and SciPy 



---

Would you like me to generate a specific **Installation** or **Usage** section for this README based on the Python and PyTorch requirements mentioned?
