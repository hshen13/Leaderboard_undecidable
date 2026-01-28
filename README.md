# Leaderboard_undecidable
# Verified Private Benchmarks for Frontier Reasoning

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository is the official implementation of the paper **"Verified Private Benchmarks for Frontier Reasoning"**. [cite_start]It introduces a novel framework for evaluating Large Language Models (LLMs) that addresses the critical challenges of **benchmark saturation**, **data contamination**, and the **lack of transparency** in private evaluations [cite: 59-62].

## 📖 Introduction

[cite_start]As general-purpose benchmarks (like GSM8K) become increasingly saturated, static evaluation scores often fail to reflect true reasoning capabilities due to potential training data leakage [cite: 75-78]. 

This project provides a comprehensive solution by combining:
1.  [cite_start]**Discrimination**: Maintaining benchmark difficulty when standard suites saturate[cite: 61].
2.  [cite_start]**Leakage Detection**: Identifying whether a model has "memorized" the test set[cite: 62].
3.  [cite_start]**Verifiable Privacy**: Enabling public verification of scores without revealing proprietary datasets or model weights[cite: 62].

## 🚀 Key Features

### 1. Post-Training DiD Leakage Detection
[cite_start]We introduce a **Difference-in-Differences (DiD)** methodology based on controlled post-training interventions[cite: 63, 164]. 
* **Mechanism**: We measure the learning slope of a model on a specific task after limited fine-tuning.
* [cite_start]**Insight**: "Clean" models show measurable improvement with exposure, whereas models that have already seen the data (leaked) exhibit diminishing returns (near-zero slope)[cite: 358, 788].
* [cite_start]**Results**: Experiments show this method significantly outperforms traditional N-gram or perplexity-based detection [cite: 782-786].

### 2. Complexity-Stratified Datasets (SGU)
[cite_start]To prevent shortcut learning, we construct benchmarks grounded in **Strongly Generically Undecidable (SGU)** task families[cite: 64, 163].
* [cite_start]**Structure**: The dataset is stratified into five levels: Known Leaks (e.g., GSM8K), Hard Problems, P-time, NP-hard, and Undecidable (SGU) [cite: 587-592].
* [cite_start]**Advantage**: Ensures that high performance requires genuine computation rather than heuristic pattern matching[cite: 163].

### 3. Four-Party Verified Protocol
[cite_start]We propose a cryptographic four-party protocol involving a **Dataset Provider (DP)**, **Model Provider (LP)**, **Execution Server**, and **Verifier**[cite: 65, 595].
* [cite_start]**Technology**: Utilizes **Zero-Knowledge Proofs (ZKPs)** to verify score correctness and **Trusted Execution Environments (TEEs)** to attest to execution integrity[cite: 167].
* [cite_start]**Privacy**: Guarantees that questions (Q), answers (A), and model parameters remain confidential while the final score is publicly verifiable [cite: 598-599].

## 📊 Experimental Results

* [cite_start]**GSM8K Leakage**: Our DiD analysis reveals a negligible response slope for GSM8K across multiple open models, strongly suggesting extensive pre-training contamination[cite: 788].
* [cite_start]**SGU Effectiveness**: SGU tasks maintain high discrimination power and resist saturation compared to traditional math benchmarks[cite: 66, 797].

## 🛠️ Citation

If you find this work or code useful for your research, please cite our paper:

```bibtex
@inproceedings{anonymous2026verified,
  title={Verified Private Benchmarks for Frontier Reasoning},
  author={Anonymous Authors},
  booktitle={ICML 2026 Undecidable Track},
  year={2026}
}
