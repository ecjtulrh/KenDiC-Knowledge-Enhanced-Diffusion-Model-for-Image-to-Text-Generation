# KenDiC
<div align="center">

<h1> Knowledge Enhanced Diffusion-Model for Image-to-Text Generation </h1>


![colored_mesh (1)](images/Fig0.jpg)
</div>


## Introduction
**KenDiC** is a Knowledge-Enhanced Diffusion-based Captioner designed for accurate and domain-specific image-to-text generation, particularly in industrial settings. While traditional autoregressive and diffusion models have shown impressive generative capabilities, they often fail in specialized domains due to a lack of external knowledge, resulting in hallucinations or vague descriptions. KenDiC addresses this gap by integrating contrastively trained visual representations with terminology-guided decoding in a latent diffusion framework. In addition, we release an industrial benchmark dataset with **3,300 high-resolution images** and **16,500 expert-annotated captions**, covering realistic scenarios across metallurgy, equipment operations, and safety-critical events.


## Installation

###  Clone the Repository
```bash
git clone https://github.com/ecjtulrh/KenDiC-Knowledge-Enhanced-Diffusion-Model-for-Image-to-Text-Generation/
cd KenDiC
```
### ⚙️ Prepare the Environment
Required packages and dependencies are listed in the `kendic.yaml` file. You can install the environment using Conda with the following command:

```bash
conda env create -f kendic.yaml
conda activate ladic
```

We also provide docker image as follows:

```bash
coming soon...
```



### Prepare the Dataset
Organize your dataset in the following structure. We also provide our industrial image-text datasets, see: [Goole drive](https://drive.google.com/drive/folders/1n4AB3W1UFCIj3DzjqE_qbSnYVewV72xO?usp=sharing)
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
### 🧰 Pretrained models

In our Kenic model, Text Encoder and Decoder are initialized from BERT-base-uncased, which can be downloaded from [Huggingface](https://huggingface.co/bert-base-uncased).

For the image encoder, we initially fine-tuned the pretrained Vision Transformer (ViT) from BLIP on an industrial image dataset. The fine-tuned model is available for download via [here](https://drive.google.com/file/d/1AloAOf6q8nJvNBpIaMwBgwXUq9tIUqbv/view?usp=sharing) and put it into `pretrained_ckpt` folder. More information can be found in [BLIP&#39;s official repo](https://github.com/salesforce/BLIP).

We provide a version of our Kendic pre-trained weights [here](https://drive.google.com/file/d/1ZqfTafbS3k5mSt-B3FYgj5umNCs_ogGO/view?usp=sharing).


## Usage

### Configuration

We use [accelerate package](https://huggingface.co/docs/accelerate/index) developed by Huggingface.

Configure Accelerate by using the following command in the command line:

```bash
accelerate config
```
Answer the questions based on your actual setup. You will be prompted to specify the GPU to use, and other configurations can be left as default. For more information, refer to [this link](https://huggingface.co/docs/accelerate/v0.13.2/en/quicktour#launching-your-distributed-script).

### Pretrain Visual Encoder with Contrastive Learning

```bash
python finetune_vision_encoder/fintune_vit.py --config configs/contrastive.yaml
```

### 🎇 Training

Launch the `main.py` script using Accelerate with the following command:

```bash

accelerate launch main_indus.py 

```

We list some important optional parameters as follows. The `notes` parameter is both a note to be placed at the top of the filename and the running name for [wandb](https://wandb.ai/site). More hyperparameters and their description can be found in `configs/`

```bash
parser.add_argument('--notes', type=str, default=None, help='Note to be included in the trial name')
parser.add_argument('--bsz', type=int, default=64, help='batch size')
parser.add_argument('--seqlen', type=int, default=24, help='sequence length')
parser.add_argument('--epoch', type=int, default=60, help='epoch num')
parser.add_argument('--resume_epoch', type=int, default=0, help='start epoch of resume')
parser.add_argument('--resume_ckpt', type=str, default=None, help='resume or not')
parser.add_argument('--logdir', type=str, default='checkpoint', help='logdir')
```

### ⚖️ Evaluation

Specify `MODEL_NAME` and `RESULLT_FILE` in `coco_eval_indus.py` representing checkpoint to be evaluated and output path respectively. Then you can run

```bash
python coco_eval_indus.py
```

## Citation

If you use the codes and datasets , please cite the following paper(not published yet).

```
coming soon
```






