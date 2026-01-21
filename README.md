# WebSight UI Code Generation (Qwen2-VL + LoRA)

Fine-tuning a vision–language model to generate **HTML + Tailwind CSS** from UI screenshots using the **WebSight** dataset.

## Overview
- Base model: **Qwen2-VL-2B-Instruct**
- Task: UI screenshot → front-end code
- Method: **rsLoRA (rank 16)** with multi-layer adaptation
- Dataset: WebSight (1.5k samples)

## Results
| Metric | Base | Fine-tuned |
|------|------|------------|
| BLEU | 0.41 | **0.59 (+18%)** |
| 1-gram Precision | 60 | **78** |
| 4-gram Precision | 34 | **53** |

## Method
- LoRA applied to **vision, attention, MLP, and language** layers  
- Mixed-precision training with **8-bit AdamW**
- Gradient accumulation for memory efficiency
- Training via **Unsloth**

## Training Setup
- GPU: NVIDIA L4
- Epochs: 2
- Batch size: 4 (accumulated to 16)
- Max length: 2048
- Training time: ~30 minutes

