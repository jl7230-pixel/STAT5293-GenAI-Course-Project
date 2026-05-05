# STAT5293 GenAI Course Project

## Chain-of-Thought Distillation for Mathematical Reasoning

This repository contains the final project for **STAT GR5293 GenAI**. The project studies whether chain-of-thought (CoT) distillation can improve mathematical reasoning in a smaller student language model while balancing accuracy, output length, and inference latency.

The project uses the **GSM8K** mathematical reasoning dataset and compares three supervised fine-tuning formats:

1. **Answer-only supervision**
2. **Verbose chain-of-thought supervision**
3. **Compressed chain-of-thought supervision**

The student model is based on **Qwen2.5-3B-Instruct** and is fine-tuned using **LoRA**.

---

## Project Pipeline

![Project Pipeline](figures/figure_1_project_pipeline.png)

The project workflow includes:

1. Loading GSM8K math word problems
2. Generating teacher rationales
3. Constructing answer-only, verbose CoT, and compressed CoT datasets
4. Fine-tuning a Qwen2.5-3B-Instruct student model with LoRA
5. Evaluating accuracy, output length, and latency

---

## Research Questions

This project investigates the following questions:

1. Does chain-of-thought distillation improve the mathematical reasoning ability of a smaller student model compared with answer-only supervision?
2. How do verbose CoT and compressed CoT differ in output length and inference latency?
3. Can compressed CoT provide a useful compromise between interpretability and efficiency?
4. What implementation factors limit the current pilot experiment?

---

## Dataset

The project uses **GSM8K**, a benchmark dataset of grade-school math word problems. Each example contains a natural language math question and a gold final answer.

In the pilot experiment, the cleaned dataset contains:

| Split | Number of Examples |
|---|---:|
| Training | 200 |
| Validation | 50 |
| Test Generation Split | 50 |

---

## Methodology

For each GSM8K problem, the project creates three training conditions.

| Condition | Description |
|---|---|
| Answer-only | The model outputs only the final answer. |
| Verbose CoT | The model outputs a detailed step-by-step explanation followed by the final answer. |
| Compressed CoT | The model outputs a concise reasoning trace followed by the final answer. |

---

## Teacher Data Quality

### Output Length Comparison

![Teacher Output Length](figures/figure_2_teacher_length.png)

The verbose CoT outputs are much longer than the compressed CoT outputs. The average verbose output length is approximately **138.785 words**, while the average compressed output length is approximately **38.14 words**.

### Answer Match Rate

![Teacher Answer Match Rate](figures/figure_3_teacher_match_rate.png)

Verbose CoT matches the gold answer in **191 out of 200** training examples, while compressed CoT matches in **188 out of 200** training examples.

---

## Training Behavior

![Compressed CoT Loss](figures/notebook_cell_26_plot.png)

![Training Loss Comparison](figures/notebook_cell_27_plot.png)

![Smoothed Training Loss](figures/notebook_cell_28_plot.png)

These plots show the training and validation loss recorded during LoRA fine-tuning.

---

## Pilot Evaluation

![Pilot Evaluation Summary](figures/figure_4_pilot_eval_table.png)

The available notebook summary preserves the compressed CoT result. Because the final summary table in the notebook does not preserve all three conditions, the evaluation should be interpreted cautiously.

---

## Repository Structure

```text
STAT5293-GenAI-Course-Project/
|
|-- README.md
|-- Project_5293.ipynb
|-- requirements.txt
|-- report/
|   |-- STAT5293_Final_Report_With_Figures.pdf
|   |-- STAT5293_Final_Report_With_Figures.tex
|-- presentation/
|   |-- STAT5293_Final_Presentation.pptx
|-- scripts/
|   |-- demo_script.txt
|-- results/
|   |-- evaluation_results.csv
|-- figures/
|   |-- figure_1_project_pipeline.png
|   |-- figure_2_teacher_length.png
|   |-- figure_3_teacher_match_rate.png
|   |-- figure_4_pilot_eval_table.png
|   |-- notebook_cell_26_plot.png
|   |-- notebook_cell_27_plot.png
|   |-- notebook_cell_28_plot.png
