# 3D Pose Transfer with Conformal Geometry Priors

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This project is an enhanced version of the original [Skeleton-free Pose Transfer](https://github.com/zycliao/skeleton-free-pose-transfer) model. The core enhancement is the integration of **Conformal Geometry Priors** using **Least Squares Conformal Maps (LSCM)**, calculated via the powerful [libigl](https://github.com/libigl/libigl) library.

The primary goal is to improve the accuracy and robustness of 3D pose transfer by providing the underlying neural network with strong, pose-invariant geometric information from the beginning.

## Core Idea

Traditional data-driven approaches learn geometric features from scratch, which can sometimes lack robustness and fail to preserve the intrinsic structure of the mesh during deformation.

This project addresses this by computing a **2D UV parameterization** for each 3D model using LSCM. This UV map preserves local angles and represents a "geometric fingerprint" of the mesh's surface, independent of its current pose.

We then concatenate this 2D UV coordinate with the original 3D vertex coordinates (x, y, z) to create a richer **5-dimensional feature vector (x, y, z, u, v)**. This vector is then fed into the network's encoder, giving the model a direct understanding of the mesh's intrinsic geometry.

## Getting Started

To get a local copy up and running, follow these simple steps.

### Cloning the Repository

Because this project uses Git submodules, you need to use the `--recurse-submodules` flag when cloning:

```bash
git clone --recurse-submodules https://github.com/xiong-zirui/LSCM-Enhanced-Pose-Transfer.git
cd LSCM-Enhanced-Pose-Transfer
```

## How to Run

### 1. Dependencies

In addition to the original project's dependencies, you need to install the `libigl` Python bindings:

```bash
pip install igl
```

### 2. Data Preprocessing

Before training or running a demo, you must first preprocess the 3D models to compute and save the LSCM UV coordinates.

- **For standard datasets (AMASS, Mixamo, RigNet):**
  Use the corresponding scripts in the `skeleton-free-pose-transfer/data_proc/` directory (e.g., `amass_preproc.py`). We have already modified them to automatically calculate and save the UV data.

- **For your own custom model (e.g., `.obj`, `.ply`):**
  Use the newly created `proc_custom_data.py` script.

  ```bash
  cd skeleton-free-pose-transfer
  python proc_custom_data.py --in_file path/to/your/model.obj --out_file path/to/your/preprocessed_data.npz
  ```

### 3. Training & Demonstration

After preprocessing, you can run the training or demo scripts as described in the original project. The data loaders and network have been updated to automatically handle the new 5D feature vectors.

## Acknowledgements

This work is built upon the foundational research and implementation of [Skeleton-free Pose Transfer](https://github.com/zycliao/skeleton-free-pose-transfer). We extend our gratitude to the original authors for their contribution to the community.