# KenDiC
<div align="center">

<h1> Knowledge-Enhanced-Diffusion-Model-for-Image-to-Text-Generation </h1>

<div>
    <p> <b>South China University of Technology & Pengcheng Laboratory</b> </p>
</div>

![colored_mesh (1)](images/fig00.jpg)
</div>

---

## Introduction

**KenDiC** is a Knowledge-Enhanced Diffusion-based Captioner designed for accurate and domain-specific image-to-text generation, particularly in industrial settings. While traditional autoregressive and diffusion models have shown impressive generative capabilities, they often fail in specialized domains due to a lack of external knowledge, resulting in hallucinations or vague descriptions.

KenDiC addresses this gap by integrating contrastively trained visual representations with terminology-guided decoding in a latent diffusion framework. In addition, we release an industrial benchmark dataset with **3,300 high-resolution images** and **16,500 expert-annotated captions**, covering realistic scenarios across metallurgy, equipment operations, and safety-critical events.

---

## Features
coming soon
---

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourname/KenDiC.git
cd KenDiC
```
### Install Dependencies
```bash
pip install -r requirements.txt
```
### Prepare the Dataset
Organize your dataset in the following structure:
```bash
datasets/
├── train/
│   ├── Images/
│   └── captions_train.json
├── val/
│   ├── Images/
│   └── captions_val.json
└── test/
    ├── Images/
    └── captions_test.json
```
## Usage

### Pretrain Visual Encoder with Contrastive Learning
```bash
python train_contrastive.py --config configs/contrastive.yaml
```
### Train the KenDiC Captioning Model
```bash
python train_caption.py --config configs/kendic.yaml
```
### Run InferenceRun Inference
```bash
python predict.py --config configs/kendic.yaml
```
## Experimental Results

KenDiC significantly outperforms state-of-the-art AR (e.g., BLIP, ViTCap) and diffusion models (e.g., Prefix-Diffusion, DDCap) on our industrial dataset, especially in fine-grained terminology usage, visual accuracy, and semantic coverage.

For detailed benchmarks, case studies, and ablation results, please refer to the Paper.

#### 🐳Building With Docker Images
```shell
Coming soon
```


## Citation

If you use the codes and datasets , please cite the following paper(not published yet).

```
coming soon
```






