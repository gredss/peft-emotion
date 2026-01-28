# PEFT Evaluation for Indonesian Emotion Classification

This repository contains the data preparation and preprocessing pipeline for evaluating **Parameter-Efficient Fine-Tuning (PEFT)** methods on Indonesian NLP tasks using transformer-based model such as  **IndoBERTweet**. The primary goal is to assess how PEFT strategies (LoRA, QLoRA, Prefix Tuning, and Full Fine-Tuning) perform in low-resource and domain-specific contexts.

---

## Dataset Source

**Source:** [PRDECT-ID Dataset (Product Review Dataset for Emotion and Customer Text – Indonesia)](https://doi.org/10.1016/j.dib.2022.108554)

# **Project: Benchmarking PEFT Strategies for Indonesian Emotion Classification**

This repository contains the implementation and empirical evaluation of various **Parameter-Efficient Fine-Tuning (PEFT)** strategies applied to **IndoBERTweet** for emotion classification in the Indonesian e-commerce domain. The study focuses on the trade-offs between predictive performance, memory consumption, and training latency.

---

## **Project Overview**

Adapting Large Language Models (LLMs) for localized, noisy, and informal datasets—such as Indonesian consumer feedback—often poses a significant challenge due to hardware constraints. This project provides a systematic comparison between **Full Fine-Tuning (Full FT)**, **LoRA**, **QLoRA**, and **Prefix Tuning** to identify the optimal configuration for resource-constrained environments.

### **Key Findings**

* **Optimal Performance**: IndoBERTweet with **LoRA** on raw datasets achieved a peak **F1-macro of 0.676**.
* **Memory Efficiency**: LoRA reduced GPU memory overhead by **42%** (1.23 GB) compared to Full FT (2.16 GB).
* **Parameter Efficiency**: LoRA achieved competitive results while updating only **2.68M parameters**, a **>97% reduction** from the 110M parameters in Full FT.
* **Quantization Trade-off**: **QLoRA** emerged as the fastest transformer method (55.03s per epoch) but suffered an **89% performance degradation**.
* **Calibration**: All models maintained high reliability with an **Expected Calibration Error (ECE) of 0.036**.

---

## **Experimental Architecture**

### **Model Configurations**

| Strategy | Description | Trainable Params |
| --- | --- | --- |
| **Full FT** | Updates all model weights; serves as the performance baseline. | 110,562,053 |
| **LoRA** | Injects low-rank trainable matrices into transformer layers. | 2,682,629 |
| **Prefix Tuning** | Prepends trainable task-specific vectors to hidden states. | 92,544 |
| **QLoRA** | 4-bit quantization of the backbone model with LoRA adapters. | 110,562,053 |

### **Evaluation Metrics**

1. **Predictive Quality**: F1-Macro Score and Accuracy.
2. **Hardware Efficiency**: Peak GPU VRAM (MB) and Training Wall Time (s).
3. **Reliability**: Expected Calibration Error (ECE).
4. **Pareto Frontier**: A multi-criteria analysis of the Performance-Efficiency trade-off.

---

## **Technical Implementation**

### **Dataset Preprocessing**

The study utilizes two variants of Indonesian e-commerce data:

* **Raw**: Retains original linguistic features, emojis, and informal punctuation.
* **Normalized**: Standardized text following Indonesian formal rules.
Results indicate that **Raw data** provides richer sentiment signals for LoRA-based models.

---

## **Citation and Acknowledgments**

This research was supported by **Bina Nusantara University**.
