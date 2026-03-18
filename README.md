# ArvyaX ML Internship Assignment

**Theme:** From Understanding Humans → To Guiding Them

---

## 🚀 Overview

This project builds an **end-to-end intelligent system** that goes beyond prediction.

Instead of only classifying emotions, the system is designed to:

* Understand human emotional state
* Reason under noisy and incomplete inputs
* Decide meaningful next actions
* Guide users toward better mental states

This mimics a **real-world assistive AI system**, not just a machine learning model.

---

## 🧠 System Architecture

The pipeline is divided into four layers:

### 1. Understanding Layer

* Input: user journal text + contextual signals
* Text processed using **TF-IDF**
* Metadata includes:

  * sleep hours
  * stress level
  * energy level
  * time of day
  * previous mood

---

### 2. Prediction Layer

* **Emotional State** → Classification (Logistic Regression)
* **Intensity (1–5)** → Regression (Random Forest)

Intensity is modeled as regression to capture ordinal relationships and then discretized.

---

### 3. Decision Layer (Core)

A rule-based system determines:

#### ➤ What to do

Examples:

* box_breathing
* journaling
* deep_work
* rest
* pause

#### ➤ When to do

* now
* within_15_min
* later_today
* tonight
* tomorrow_morning

This ensures:

* interpretability
* reliability
* real-world usability

---

### 4. Uncertainty Layer

The system explicitly models uncertainty:

* **Confidence score** from model probabilities
* **Uncertain flag** triggered when:

  * confidence < threshold
  * input is too short
  * signals are conflicting

This makes the system **aware of its limitations**, which is critical in real-world deployment.

---

## 📊 Feature Engineering

### Text Features

* TF-IDF vectorization (max_features=1000)

### Metadata Features

* sleep_hours
* energy_level
* stress_level
* duration_min

### Insights

* Text is primary driver for emotion detection
* Metadata improves performance in ambiguous cases
* Stress & energy strongly influence decision-making

---

## 📈 Model Performance

| Task                   | Model               | Metric          |
| ---------------------- | ------------------- | --------------- |
| Emotion Classification | Logistic Regression | Accuracy ≈ 0.62 |
| Intensity Prediction   | Random Forest       | MSE ≈ 2.27      |

---

## 🔬 Ablation Study

| Model           | Accuracy |
| --------------- | -------- |
| Text Only       | Lower    |
| Text + Metadata | Higher   |

Conclusion:

> Metadata significantly improves predictions, especially for vague inputs.

---

## ⚠️ Error Analysis Summary

Key failure modes:

* Ambiguous text (“I’m fine”)
* Very short inputs (“ok”)
* Conflicting emotions (“tired but excited”)
* Keyword bias (“anxious”, “heavy”)
* Label noise
* Lack of contextual understanding

---

## 🛠️ How to Run

### 1. Install dependencies

```bash
pip install pandas numpy scikit-learn
```

### 2. Run notebook

* Open Jupyter Notebook
* Run all cells sequentially

### 3. Output

```bash
predictions.csv
```

---

## 📁 Output Format

```plaintext
id
predicted_state
predicted_intensity
confidence
uncertain_flag
what_to_do
when_to_do
```

---

## 📱 Edge / Deployment Considerations

The system is designed for lightweight deployment:

* Uses **TF-IDF + Logistic Regression** (low memory)
* Fast inference → suitable for mobile
* No external APIs → privacy preserving

Trade-offs:

* Slightly lower accuracy vs large models
* Much better speed and deployability

---

## 💡 Key Takeaways

* This is not just a prediction system, but a **decision-making AI**
* Handles:

  * noisy data
  * missing values
  * uncertainty
* Combines:

  * ML + rule-based reasoning
* Designed with **real-world constraints in mind**

---

## 🚀 Future Improvements

* Use transformer models (BERT) for better context understanding
* Improve uncertainty modeling using Bayesian approaches
* Personalization using user history
* Multi-label emotion detection

---

## 🎯 Conclusion

This project demonstrates:

* ability to handle messy real-world data
* reasoning beyond standard ML tasks
* building systems that **guide users, not just predict**

It reflects a **product-oriented approach to AI system design**.
