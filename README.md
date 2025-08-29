# 🚀 Improved Adversarial Stickers

[![Python](https://img.shields.io/badge/python-3.8-blue.svg)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)]()
[![Paper](https://img.shields.io/badge/Paper-TPAMI%202022-orange)](https://ieeexplore.ieee.org/abstract/document/9779913)

This repository provides an improved implementation of the paper:
👉 *Adversarial Stickers: A Stealthy Attack Method in the Physical World* (TPAMI 2022)(https://ieeexplore.ieee.org/abstract/document/9779913)

The original paper proposes a stealthy physical-world adversarial attack by embedding meaningful stickers onto faces. Our curreent version is built upon the official codebase [Adv-Stickers\_RHDE](https://github.com/jinyugy21/Adv-Stickers_RHDE) with several fixes and improvements for easier setup and use.

---

## 🔧 Improvements Over Original

* ✅ Fixed bugs (e.g., missing pretrained face recognition model → replaced with [FaceNet](https://github.com/timesler/facenet-pytorch)).
* ✅ Updated deprecated libraries/functions.
* ✅ Clearer environment & installation guide.
* ✅ Cleaned unsupported datasets/models → focus on FaceNet + LFW.

---

## ⚙️ Quick Start

### 1. Environment Setup

Make sure you have [conda](https://docs.conda.io/) installed, then run:

```bash
conda create -n adv_sticker python=3.8.11
conda activate adv_sticker
pip install -r requirements.txt
```

### 2. Data Preparation

Download the [LFW dataset](https://drive.google.com/file/d/0B7EVK8r0v71pZDFOOGxhbm1oakE/view?usp=share_link&resourcekey=0-OvdR0Gk5lY7a8r5FjKIYhA).
Place it under `./datasets/` and rename the folder to `lfw_images`.

Example directory structure:

```
datasets
└── lfw_images
    ├── AJ_Cook
    │   └── AJ_Cook_0001.jpg
    ├── AJ_Lamas
    │   └── AJ_Lamas_0001.jpg        
```

### 3. Model Preparation

We use [FaceNet](https://github.com/timesler/facenet-pytorch) for face recognition. Download the pretrained model and place it in `./models/`.

If you use another model, please modify `./utils/predict.py` accordingly.

### 4. Other Dependencies

* [Face3D](https://github.com/YadiraF/face3d/tree/master/face3d) (already included in this repo).

* Due to file size limits, some required models must be downloaded manually:

  * **BFM Model**: [Download here](https://drive.google.com/file/d/1sTNEi7MGMe-azOkAtc5bg6QuEwFI1XvT/view?usp=share_link) → place under `./BFM/`
  * **Shape Predictors for Face Landmarks**:

    * [68 landmarks](https://github.com/r4onlyrishabh/facial-detection/tree/master/dataset)
    * [81 landmarks](https://github.com/codeniko/shape_predictor_81_face_landmarks)

*  Note: place the two shape predictors in the project root directory (same as `attack_single.py`).*

Example directory structure:

```
.
 └── face3d
     ├── mesh
     ├── mesh_numpy
     ├── morphable_model
     └── __init__.py
 └── BFM
     └── BFM.mat
 └── shape_predictor_68_face_landmarks.dat
 └── shape_predictor_81_face_landmarks.dat
```

---

## 🎯 Attack

### Hyperparameters

Configuration file: `./utils/config.py`

### Run Attack

To attack a single image:

```bash
python attack_single.py
```

Results will be saved in `./results_img/`.

---

## 🚩 Future Work

* Reduce queries (Bayesian/Hybrid optimization).
* Multi-sticker & noise-robust attacks.
* Stealthier sticker designs (natural/logos).

---

## 📚 References

* Paper: [Adversarial Stickers: A Stealthy Attack Method in the Physical World (TPAMI 2022)](https://ieeexplore.ieee.org/abstract/document/9779913)
* Code: [Adv-Stickers](https://github.com/jinyugy21/Adv-Stickers_RHDE) | [Face3D](https://github.com/yfeng95/face3d/tree/master/face3d) | [FaceNet](https://github.com/timesler/facenet-pytorch)

---

## 👥 Team Information

**Team Name**: BlackBox Alchemists

**Members**:

* Zehao Wang ([zwan0536@student.monash.edu](mailto:zwan0536@student.monash.edu))
* Ru Zhang ([rzha0193@student.monash.edu](mailto:rzha0193@student.monash.edu))

---

*This project was developed as part of the **“Adversarial ML on Gen AI” Challenge** (Theme 1 – Dark Side: Attacker).*