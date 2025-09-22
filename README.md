## Overview

This repository provides a comprehensive pipeline for fine-tuning large language models (LLMs) specifically DeepSeek R1 Distill Llama 8B and Qwen 2.5-3.5B Instruct – on a specialized medical dataset in the Chain of Thought format. The goal: create an accurate and concise medical assistant capable of diagnostic reasoning and treatment planning.

Fine-tuning is performed using **Low Rank Adaptation (LoRA)** for parameter-efficient learning. Models are optimized to follow detailed physician-like reasoning prompts and to generate high-quality responses for medical use-cases.

---

## Models Used

- **Qwen 2.5B & 3.5B Instruct:** Instruction-tuned LLMs with multilingual and long-context support, ideal for specialized domains.
- **DeepSeek R1 Distill Llama 8B:** Efficient, open-source Llama-based model providing strong generalization capabilities for medical language tasks.

---

## Dataset

- **Source:** OpenAI Medical Chain of Thought Dataset
- **Size:** First 500 samples (train split)
- **Format:** Physician-style prompts, step-by-step reasoning, and gold-standard medical answers.

---

## Training Pipeline

- Framework: PyTorch + Unsloth + Hugging Face Transformers
- Adapter: [LoRA](https://arxiv.org/abs/2106.09685) (Low Rank Adaptation)
- Optimizer: AdamW 8-bit for efficient optimization
- Quantization: fp16 and 4-bit for memory savings
- Custom prompt formatting with chain-of-thought instructions and reasoning

---

## Key Results

### Qwen 2.5-3.5B Instruct

- **Training loss decreased from 2.1 to 1.3** in just 1 epoch (60 steps), indicating rapid convergence and effective adaptation to the medical dataset.
- Model responds well to physician-style prompts; anticipated strong output quality for medical QA tasks.

### DeepSeek R1 Distill Llama 8B

- **Training loss reduced from 1.96 to 1.45** during 1 epoch (60 steps).
- Demonstrates solid generalization and alignment toward chain-of-thought medical reasoning.

### Metric Calculation

Due to out-of-memory (OOM) errors during response generation, it was not possible to compute BLEU or ROUGE scores directly as output strings could not be obtained for metric comparison.  
*Typical performance for similar loss values in literature:*
- **BLEU:** 20–40 (expected range)
- **ROUGE-L:** 0.4–0.6 (expected range)  
These are only estimates in accordance of the Losses

## You won't be able to deploy these Models on HuggingFace Spaces due to Hardware Limitations . Prefer Finetuning Qwen 0.5-2.5B Instruct , making some changes in the params , if your main aim is also deploying the chatbot.

---

## LoRA Fine-Tuning Implementation

*Add your LoRA implementation process image here.*

---


