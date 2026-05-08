# STAT5293 GenAI Course Project

## Chain-of-Thought Distillation for Mathematical Reasoning

This repository contains the final project for **STAT GR5293 GenAI**. The project studies chain-of-thought (CoT) distillation for mathematical reasoning using the GSM8K dataset and a Qwen2.5-3B-Instruct student model.

The main goal is to compare three training formats:

1. Answer-only supervision
2. Verbose chain-of-thought supervision
3. Compressed chain-of-thought supervision

The project focuses on both reasoning performance and efficiency. In addition to final answer accuracy, we also consider output length and inference latency.

---

## Project Overview

Large language models often perform better on reasoning tasks when they generate intermediate reasoning steps. However, full chain-of-thought responses can be long and expensive to generate. This project explores whether a smaller student model can learn useful reasoning behavior from distilled reasoning traces.

We compare three supervision strategies:

| Training Format | Description |
|---|---|
| Answer-only | The model is trained to output only the final numerical answer. |
| Verbose CoT | The model is trained to output detailed step-by-step reasoning before the final answer. |
| Compressed CoT | The model is trained to output a shorter reasoning trace before the final answer. |

The compressed CoT setting is the main focus because it may provide a balance between interpretability and efficiency.

---

## Research Questions

This project addresses the following questions:

1. Does chain-of-thought supervision help a smaller language model learn mathematical reasoning better than answer-only supervision?
2. How do verbose CoT and compressed CoT differ in output length?
3. Can compressed CoT reduce reasoning cost while preserving useful reasoning information?
4. What are the main limitations of building a reasoning-distillation pipeline under limited computing resources?

---

## Dataset

The project uses **GSM8K**, a benchmark dataset of grade-school mathematical word problems. Each example contains a natural language math question and a gold final answer.

In the pilot experiment, the dataset was divided into:

| Split | Number of Examples |
|---|---:|
| Training | 1000 |
| Validation | 100 |
| Test / Generation | 100 |

Because this is a course project with limited computing resources, the experiment uses a small subset of GSM8K rather than the full dataset.

---

## Model

The student model is based on:

```text
Qwen2.5-3B-Instruct
