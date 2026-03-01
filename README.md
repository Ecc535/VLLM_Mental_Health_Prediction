# VLLM_Mental_Health_Prediction
Goal: Use vLLM to predict mental health. This repo tries to improve LLM efficiency (accuracy-latency ratio)

---

## Dataset Overview

- **Population:** Clinicians with long shift work patterns (`n = 44`)  
- **Label:** Highly skewed outcome — **burnout** (High : Low = 38 : 6) 
- **Burnout Evaluation:** Assessed across **three perspectives**:  
  1. **Emotional Exhaustion**  
  2. **Depersonalization**  
  3. **Reduced Personal Accomplishments**  

> ⚠️ Note: The dataset is small and imbalanced, which may affect model generalizability.  

---

## Model

- **Framework:** vLLM + standard LLM interface  
- **Base Model:** LLaMA **Nemetron Nano 4B**  
- **Prediction Task:** Predict overall burnout and its subcategories under different data sources (Sensor, Survey, Aggregated Rhythm)

---

## Setup and Settings

- **Deployment:** API server used to launch vLLM  
- **Efficiency Optimizations:**  
  - **PagedAttention**  
  - **Prefill Tiling**  
  - **Batch concurrent processing**  

---

## Key Findings

- **LLM Performance:**  
  - Good at predicting **overall burnout**. The overall accuracy is 0.84 and the average F1 score is more than 0.65 for 2 labels.
  - Struggles with classification of the **three subcategories**
> For Zero-shot training, pre-trained llm has more training inputs about burnout. While for 3 deatiled sub-categories, inference needs more provided information.

- **Feature Engineering Insights:**  
  - Adding more raw features does **not necessarily improve performance**  
  - Selecting features based on **SHAP analysis** leads to:  
    - Sufficient classification performance  
    - Efficient computation  

---
