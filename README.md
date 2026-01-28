# Leaderboard_undecidable

This repository is the official implementation of the paper **"Trustworthy Leaderboard: Post-Training DiD Analysis to Reveal Leakage in
Private Math Dataset"**. It introduces a novel framework for evaluating Large Language Models (LLMs) that addresses the critical challenges of **benchmark saturation**, **data contamination**, and the **lack of transparency** in private evaluations.

## 📖 Introduction

As general-purpose benchmarks (like GSM8K) become increasingly saturated, static evaluation scores often fail to reflect true reasoning capabilities due to potential training data leakage.

This project provides a comprehensive solution by combining:
1.  **Discrimination**: Maintaining benchmark difficulty when standard suites saturate.
2.  **Leakage Detection**: Identifying whether a model has "memorized" the test set.
3.  **Verifiable Privacy**: Enabling public verification of scores without revealing proprietary datasets or model weights.

## 🚀 Key Features

### 1. Post-Training DiD Leakage Detection
We introduce a **Difference-in-Differences (DiD)** methodology based on controlled post-training interventions.
* **Mechanism**: We measure the learning slope of a model on a specific task after limited fine-tuning.
* **Insight**: "Clean" models show measurable improvement with exposure, whereas models that have already seen the data (leaked) exhibit diminishing returns (near-zero slope).
* **Results**: Experiments show this method significantly outperforms traditional N-gram or perplexity-based detection.

### 2. Complexity-Stratified Datasets (SGU)
To prevent shortcut learning, we construct benchmarks grounded in **Strongly Generically Undecidable (SGU)** task families.
* **Structure**: The dataset is stratified into five levels: Known Leaks (e.g., GSM8K), Hard Problems, P-time, NP-hard, and Undecidable (SGU).
* **Advantage**: Ensures that high performance requires genuine computation rather than heuristic pattern matching.

### 3. Four-Party Verified Protocol
We propose a cryptographic four-party protocol involving a **Dataset Provider (DP)**, **Model Provider (LP)**, **Execution Server**, and **Verifier**.
* **Technology**: Utilizes **Zero-Knowledge Proofs (ZKPs)** to verify score correctness and **Trusted Execution Environments (TEEs)** to attest to execution integrity.
* **Privacy**: Guarantees that questions (Q), answers (A), and model parameters remain confidential while the final score is publicly verifiable.

## 📊 Experimental Results

* **GSM8K Leakage**: Our DiD analysis reveals a negligible response slope for GSM8K across multiple open models, strongly suggesting extensive pre-training contamination.
* **SGU Effectiveness**: SGU tasks maintain high discrimination power and resist saturation compared to traditional math benchmarks.
