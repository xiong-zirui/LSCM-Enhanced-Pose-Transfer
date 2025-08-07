# 3D Pose Transfer with Conformal Geometry Priors

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An enhanced 3D pose transfer model based on 'Skeleton-free Pose Transfer', incorporating geometric priors from Conformal Maps (LSCM) via the libigl library.

This project aims to improve the accuracy and robustness of 3D pose transfer by providing the underlying neural network with strong, pose-invariant geometric information calculated through classical geometric processing methods.

---

## Core Idea
This model integrates the strengths of deep learning and computational geometry. It enhances the **[Skeleton-free Pose Transfer](https://github.com/zycliao/skeleton-free-pose-transfer/)** framework by:
1.  **Enhancing the Encoder**: Augmenting input features with pre-computed LSCM UV coordinates to provide a pose-invariant "geometric signature" for each vertex.
2.  **Regularizing the Skinning Weights**: Introducing a consistency loss based on point-to-point correspondence from the conformal map to ensure geometrically plausible skinning weight prediction.

## Tech Stack
* **Python**
* **PyTorch**
* **libigl (via Python bindings)**
* **NumPy**

## Setup & Usage
*(To be filled in later)*

1.  Clone the repository:
    ```bash
    git clone [https://github.com/xiong-zirui/3dPoseTransfer.git](https://github.com/xiong-zirui/3dPoseTransfer.git)
    ```
2.  ...

## TODO
- [ ] Set up project environment and dependencies.
- [ ] Integrate and test `libigl.lscm` functionality.
- [ ] Implement data preprocessing pipeline for UV coordinate generation.
- [ ] Modify model architecture to accept 5D input features (x, y, z, u, v).
- [ ] Train and validate the enhanced model against the baseline.