# LLaVA++: Extending Visual Capabilities with LLaMA-3 and Phi-3
<p align="center">
    <img src="https://i.imgur.com/waxVImv.png" alt="Oryx Models">
</p>

#### [Hanoona Rasheed](https://www.hanoonarasheed.com/)\*, [Muhammad Maaz](https://www.muhammadmaaz.com)\*, [Salman Khan](https://salman-h-khan.github.io/), and [Fahad Khan](https://sites.google.com/view/fahadkhans/home)
\* Equally contributing first authors

#### **Mohamed bin Zayed University of AI**

---

## 📢 Latest Updates
- **Apr-26-24**- Phi-3-V and LLaVA-3-V released: Excited to release the new integration of LLaVA with Phi-3 Mini Instruct and LLaMA-3 Instruct models! 🔥🔥🔥

---
<p align="center">
  <img src="images/logos/face.png" width="300">
</p>

## 💬 Introduction
This repository enhances the capabilities of the LLaVA 1.5 model, incorporating latest LLMs released this weak🔥, [Phi-3 Mini Instruct 3.8B](https://huggingface.co/microsoft/Phi-3-mini-4k-instruct), and [LLaMA-3 Instruct 8B](https://huggingface.co/meta-llama/Meta-Llama-3-8B).


## 🏆 Results: Phi-3-V and LLaVA-3-V
<p align="center">
  <img src="images/lava++_radar_plot.png" width="450">
</p>

### Comparison on Benchmarks for Instruction-following LMMS & academic-task-oriented datasets:

| Model                 | MMMU | POPE |  MME   | MMBench-en | MMBench-cn | SEED-all | SEED-img | SEED-vid | LLaVA-Wild | GQA  | Science-QA | Average  |
|:----------------------|:----:|:----:|:------:|:----------:|:----------:|:--------:|:--------:|:--------:|:----------:|:----:|:----------:|:--------:|
| LLaVA-v1.5-7B         | 35.4 | 85.8 | 1510.7 |    64.3    |    58.3    |   58.6   |   66.1   |   37.3   |    65.4    | 62.0 |    66.8    |   58.9   |
| LLaVA-v1.5-13B        | 36.4 | 85.9 | 1531.3 |    67.7    |    63.6    |   61.6   |   68.2   |   42.7   |    72.5    | 63.3 |    71.6    |   62.3   |
| **Phi-3-V-mini-3.8B** | 37.8 | 85.6 | 1470.1 |    68.2    |    68.1    |   62.8   |   67.7   |   44.5   |    70.9    | 61.7 |    80.7    | **63.2** |

🌟 LLaMA-3-V-8B results and models - coming soon!

*Average computed excluding MME

## 🤖 Model-Zoo

The following table provides an overview of the available models in our zoo. For each model, you can find links to its Hugging Face page. 

|                            Model Name |                             Hugging Face Link                              |                                                                                                           Summary |
|--------------------------------------|:--------------------------------------------------------------------------:|------------------------------------------------------------------------------------------------------------------|
| LLaVA-Phi-3-mini-4k-instruct-pretrain | [HF](https://huggingface.co/MBZUAI/LLaVA-Phi-3-mini-4k-instruct-pretrain)  |                              Pretrained on [LCS-558K](https://huggingface.co/datasets/liuhaotian/LLaVA-Pretrain). |
|     LLaVA-Phi-3-mini-4k-instruct-lora |   [HF](https://huggingface.co/MBZUAI/LLaVA-Phi-3-mini-4k-instruct-lora)    |  LoRA weights fine-tuned on [LLaVA-Instruct-665K](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K) 
|          LLaVA-Phi-3-mini-4k-instruct |      [HF](https://huggingface.co/MBZUAI/LLaVA-Phi-3-mini-4k-instruct)      |                                                                             Merged weights in HuggingFace format. |

# Installation

```bash
git clone https://github.com/mbzuai-oryx/LLaVA-pp.git
cd LLaVA-pp
git submodule update --init --recursive
```
Packages you need to update from LLAVA:
```bash
pip install git+https://github.com/huggingface/transformers@a98c41798cf6ed99e1ff17e3792d6e06a2ff2ff3
```

## 🚀 Phi-3-V
To integrate Phi-3-V with LLaVA, follow these steps to update the codebase:

```bash
# Copy necessary files
cp Phi-3-V/train.py LLaVA/llava/train/train.py
cp Phi-3-V/llava_phi3.py LLaVA/llava/model/language_model/llava_phi3.py
cp Phi-3-V/builder.py LLaVA/llava/model/builder.py
cp Phi-3-V/model__init__.py LLaVA/llava/model/__init__.py
cp Phi-3-V/main__init__.py LLaVA/llava/__init__.py
cp Phi-3-V/conversation.py LLaVA/llava/conversation.py

# Training commands
cp scripts/Phi3-V_pretrain.sh LLaVA/Vi-phi3_pretrain.sh
cp scripts/Phi3-V_finetune_lora.sh LLaVA/Vi-phi3_finetune_lora.sh
```

### Train Phi-3-V
1. Pre-train
```bash
cd LLaVA
bash Phi3-V_pretrain.sh
```
2. Finetune
```bash
cd LLaVA
bash Phi3-V_finetune_lora.sh
```

## 🚀 LLaMA-3-V
To integrate LLaMA-3-V with LLaVA, follow these steps to update the codebase:

```bash
# Copy necessary files
cp Phi-3-V/train.py LLaVA/llava/train/train.py
cp Phi-3-V/conversation.py LLaVA/llava/conversation.py

# Training commands
cp scripts/LLaMA3-V_pretrain.sh LLaVA/LLaMA3-V_pretrain.sh
cp scripts/LLaMA3-V_finetune_lora.sh LLaVA/LLaMA3-V_finetune_lora.sh
```

### Train LLaMA-3-V
1. Pre-train
```bash
cd LLaVA
bash LLaMA3-V_pretrain.sh
```
2. Finetune
```bash
cd LLaVA
bash LLaMA3-V_finetune_lora.sh
```

---
## 🙏 Acknowledgement
We are thankful to [LLaVA](https://github.com/haotian-liu/LLaVA.git), and [lmms-eval](https://github.com/EvolvingLMMs-Lab/lmms-eval.git) for releasing their models and code as open-source contributions.

---
[<img src="images/logos/IVAL_logo.png" width="200" height="100">](https://www.ival-mbzuai.com)
[<img src="images/logos/Oryx_logo.png" width="100" height="100">](https://github.com/mbzuai-oryx)
[<img src="images/logos/MBZUAI_logo.png" width="360" height="85">](https://mbzuai.ac.ae)
