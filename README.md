# Face Recognition Biometric Security Pipeline

A full biometric authentication pipeline built on the ORL/Olivetti face database, covering
capture, preprocessing, PCA (Eigenfaces) feature extraction, matching, threshold analysis,
FAR/FRR/EER evaluation, multimodal (PCA + LBP) fusion, and template security — built for
CYB 302 (Biometrics Security), Miva Open University.

## Pipeline
1. **Data**: 400 grayscale images, 40 subjects (ORL/Olivetti via scikit-learn), 7:3 enroll/test split
2. **Preprocessing**: normalization, Gaussian denoising, histogram equalization
3. **Feature extraction**: PCA/Eigenfaces (87 components, 95% variance retained)
4. **Matching**: Euclidean distance, verification (1:1) and identification (1:N)
5. **Threshold analysis**: FAR/FRR trade-off sweep, EER computation
6. **Multimodal fusion**: PCA + Local Binary Patterns (LBP), score-level sum fusion
7. **Security**: Fernet (AES) template encryption, cancelable biometrics discussion, NDPA 2023 compliance analysis

## Results
| Metric | PCA (Eigenfaces) | LBP | Fused |
|---|---|---|---|
| EER | 22.87% | 27.39% | **21.35%** |
| Identification accuracy (1:N) | 85.8% | — | — |
| ROC AUC | 0.8551 | — | — |

Fusion of PCA and LBP reduced EER below either individual modality, confirming that
complementary feature descriptors improve overall system reliability.

## Repo structure
