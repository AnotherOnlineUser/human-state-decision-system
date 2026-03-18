# Edge Deployment Plan

## Overview

The system is designed to run efficiently on edge devices such as mobile phones or low-resource environments. The goal is to ensure low latency, privacy, and offline capability.

---

## Model Choice

We use lightweight models:

* TF-IDF for text representation
* Logistic Regression for emotion classification
* Random Forest for intensity prediction

These models are:

* fast
* memory-efficient
* easy to deploy

---

## Why Not Large Models?

Large transformer models (e.g., BERT) provide better accuracy but:

* require high memory
* increase latency
* depend on GPUs or cloud APIs

Since the constraint is local execution, lightweight models are preferred.

---

## Deployment Strategy

### On-device pipeline:

1. Preprocess input text
2. Convert to TF-IDF vector
3. Combine with metadata
4. Run prediction models
5. Apply decision logic

---

## Performance Considerations

| Factor   | Impact               |
| -------- | -------------------- |
| Latency  | Low (fast inference) |
| Memory   | Low                  |
| Accuracy | Moderate             |
| Privacy  | High                 |

---

## Optimizations

* Reduce TF-IDF features (e.g., 500 instead of 1000)
* Convert models using ONNX for faster inference
* Use model quantization for smaller size

---

## Handling Offline Scenarios

* Entire pipeline runs locally
* No dependency on internet
* Ensures user privacy and reliability

---

## Trade-offs

* Slight drop in accuracy compared to large models
* Limited contextual understanding

However, these are acceptable given the benefits of:

* speed
* privacy
* deployability

---

## Future Improvements

* Use lightweight transformer models (DistilBERT)
* Incremental learning based on user history
* Personalized recommendations

---

## Conclusion

The system is optimized for real-world deployment by prioritizing:

* low latency
* minimal resource usage
* privacy preservation

This makes it suitable for mobile and edge environments.
