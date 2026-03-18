# 🚀 AI Image & Video Model Benchmarking Report

### Comprehensive Evaluation of Multi-Modal Generative AI Systems

---

# 🔷 1. Introduction

With the rapid advancement of generative AI, multiple models now exist for image and video generation. However, selecting the optimal model for a specific use case (speed, quality, editing, or animation) remains a challenge.

This project aims to build a **systematic benchmarking framework** to evaluate and compare multiple state-of-the-art AI models across three major tasks:

* Text-to-Image Generation
* Image-to-Image Transformation
* Image-to-Video Generation

The primary objective is to analyze models based on:

* Performance (Latency, Stability)
* Output Quality (CLIP Score, SSIM, LPIPS)
* Reliability (Success Rate)

---

# 🔷 2. System Architecture

The system is designed as a modular pipeline integrating API interaction, automated testing, and evaluation.

## 🔹 Workflow

```
User Prompt / Input Image
          ↓
    Model API Request
          ↓
    Async Task Execution
          ↓
    Output Generation (Image/Video)
          ↓
    Metrics Computation Engine
          ↓
    Final Benchmark Report
```

---

## 🔹 Core Components

### 1. API Interface Layer

* Defined using OpenAPI specification
* Provides structured access to all models
* Supports multiple categories:

  * Prompt-to-Image
  * Image-to-Image
  * Image-to-Video

---

### 2. Smart Proxy System

* Built using Flask
* Handles:

  * CORS issues
  * Request transformation
  * Model parameter injection

Example:

* Automatically injects:

  * `model_version = 2.0`
  * `style = cinematic`

---

### 3. Automated Benchmark Engine

* Iterates through all models
* Measures:

  * Latency
  * Success rate
  * Stability (polling steps)

---

### 4. Metrics Engine

Computes advanced evaluation metrics:

* CLIP Score → Prompt alignment
* SSIM → Structural similarity
* LPIPS → Perceptual similarity
* Temporal Consistency → Video smoothness

---

# 🔷 3. Models Evaluated

## 🖼️ Category 1: Prompt-to-Image

| Model           | Description                       |
| --------------- | --------------------------------- |
| Soul Standard   | Fast general-purpose model        |
| Soul 2.0 Pro    | High-quality aesthetic generation |
| Soul Cinematic  | Cinematic lighting & realism      |
| Soul Character  | Identity preservation             |
| Seedream v4 T2I | High-resolution output            |
| REVE            | Experimental model                |

---

## 🎨 Category 2: Image-to-Image

| Model            | Description                           |
| ---------------- | ------------------------------------- |
| Seedream v4 Edit | Advanced editing and transformation   |
| Soul Reference   | Style transfer using reference images |

---

## 🎥 Category 3: Image-to-Video

| Model         | Description                 |
| ------------- | --------------------------- |
| DOP Standard  | Stable animation generation |
| DOP Turbo     | Faster video generation     |
| Seedance Pro  | Efficient animation model   |
| Kling 2.1 Pro | Cinematic motion            |
| Kling 3.0 Pro | Advanced motion physics     |

---

# 🔷 4. Experimental Setup

## 🔹 Input Prompts

### Text-to-Image

```
A futuristic glass skyscraper in a lush jungle, sunset lighting, hyper-realistic, 8k
```

### Image-to-Video

```
The clouds move slowly across the sunset sky
```

---

## 🔹 Reference Data

* Reference image used for structural comparison
* Standardized resolution (512×512 for metrics)
* Uniform prompt across all models

---

## 🔹 Execution Strategy

* Each model executed sequentially
* Asynchronous polling used to track completion
* Results stored in JSON format
* Outputs saved in `outputs/` directory

---
# 🔷 4.1 Reference Image (For Evaluation)

To ensure consistent evaluation across all models, a common reference image was used for structural and perceptual comparison.

🔗 **Reference Image Link:**
https://images.pexels.com/photos/1103970/pexels-photo-1103970.jpeg

## 🔹 Purpose of Reference Image

* Used for **SSIM (Structural Similarity)** calculation
* Used for **LPIPS (Perceptual Similarity)** comparison
* Ensures **fair benchmarking across models**

## 🔹 Why this Image?

* Contains **complex structure (architecture + nature)**
* Includes **lighting variation (sunset)**
* Useful for evaluating:

  * Detail preservation
  * Texture realism
  * Depth and composition

---

## 🔹 How it is used in the system

* Downloaded automatically during evaluation
* Resized to standard resolution (512×512)
* Compared against generated outputs



# 🔷 5. Evaluation Metrics

## 🔹 1. Latency (Performance)

* Definition: Time taken to generate output
* Unit: Seconds
* Interpretation:

  * Lower → Faster model

---

## 🔹 2. CLIP Score (Semantic Alignment)

* Measures similarity between prompt and generated image
* Range: 0–100
* Interpretation:

  * Higher → Better prompt understanding

---

## 🔹 3. SSIM (Structural Similarity Index)

* Measures structural similarity with reference image
* Range: 0–1
* Interpretation:

  * Higher → Better structure preservation

---

## 🔹 4. LPIPS (Perceptual Distance)

* Measures perceptual difference between images
* Interpretation:

  * Lower → More similar

---

## 🔹 5. Temporal Consistency (Video)

* Measures smoothness between video frames
* Interpretation:

  * Higher → Better motion continuity

---

# 🔷 6. Results and Observations

## 🖼️ Prompt-to-Image Results

| Model          | Latency | CLIP  | SSIM | Status  |
| -------------- | ------- | ----- | ---- | ------- |
| Soul Standard  | 13.06s  | 32.99 | 0.47 | Success |
| Soul 2.0 Pro   | 11.14s  | 36.04 | 0.51 | Success |
| Soul Cinematic | 14.08s  | 33.65 | 0.54 | Success |
| Soul Character | 12.11s  | 29.91 | 0.51 | Success |
| Seedream v4    | 15.08s  | 37.48 | 0.29 | Success |
| REVE           | N/A     | N/A   | N/A  | Failed  |

---

## 🎨 Image-to-Image Results

| Model            | Latency | CLIP  | SSIM |
| ---------------- | ------- | ----- | ---- |
| Seedream v4 Edit | 21.1s   | 37.97 | 0.34 |
| Soul Reference   | 9.12s   | 35.35 | 0.53 |

---

## 🎥 Image-to-Video Results

| Model         | Latency | Stability |
| ------------- | ------- | --------- |
| DOP Standard  | 92.66s  | High      |
| DOP Turbo     | 104.78s | High      |
| Seedance Pro  | 60.33s  | Good      |
| Kling 2.1 Pro | 75.45s  | High      |
| Kling 3.0 Pro | 102.07s | Very High |

---

# 🔷 7. Analysis

## 🔹 Key Insights

### 1. Best Quality Model

* **Seedream v4**
* Highest CLIP score
* Best prompt alignment

---

### 2. Best Balanced Model

* **Soul 2.0 Pro**
* Fast + high-quality output

---

### 3. Best Editing Model

* **Soul Reference**
* High SSIM + fast performance

---

### 4. Best Video Model

* **Kling Pro**
* Most realistic motion and physics

---


### 5. Failure Case

* **REVE model failed**
* Indicates instability or API issue

---

# 🔷 8. Business Recommendations

## 🔹 Text-to-Image

* Speed → Soul Standard
* Quality → Seedream v4

---

## 🔹 Image Editing

* Accuracy → Seedream v4 Edit
* Speed → Soul Reference

---

## 🔹 Video Generation

* High-end production → Kling Pro
* Fast preview → DOP Turbo

---

# 🔷 9. Limitations

* Limited prompt diversity
* Single reference image
* API dependency (network variability)
* No human evaluation included

---

# 🔷 10. Future Work

* Multi-prompt benchmarking
* Human evaluation scoring
* Cost vs performance analysis
* Real-time deployment system
* Integration with UI dashboard

---

# 🔷 11. Conclusion

This project successfully demonstrates a **scalable and automated benchmarking framework** for evaluating AI generative models.

Key achievements:

* Unified testing of 13 models
* Standardized evaluation metrics
* Clear comparison across tasks

Final takeaway:

> There is no single best model.
> The optimal choice depends on the use case:
>
> * Speed
> * Quality
> * Editing capability
> * Motion realism

---

# 🔷 12. References

* CLIP: OpenAI Vision-Language Model
* SSIM: Structural Similarity Index
* LPIPS: Learned Perceptual Image Patch Similarity

---

# ✅ END OF REPORT
