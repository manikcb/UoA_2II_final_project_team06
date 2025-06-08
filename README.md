# UoA_2II_final_project_team06
GIF enhancer

---

# 🧠 GIF Face Restoration with Temporal Consistency using GFPGAN

## 📌 Overview

This project focuses on restoring low-quality GIFs generated from raw face videos collected across social platforms. The aim is to **enhance facial GIFs** that are blurry, noisy, or low-resolution using **GFPGAN** (a state-of-the-art facial restoration model), while maintaining **temporal consistency** across frames.

We extend the **GFPGAN architecture**, which was originally designed for single image enhancement, to handle GIFs by breaking them into frames, processing each frame, and reassembling them while preserving motion flow.

---

## 📽️ Use Case & Motivation

In real-world scenarios like surveillance footage, memes, social videos, or animated avatars, facial GIFs are commonly degraded. This project addresses the practical need to restore and enhance such low-quality GIFs into clear, stable, and natural-looking facial animations.

---

## 🧱 System Architecture

```text
[Raw Face Videos]
       ↓
[GIF Generator + Categorizer]
       ↓──────▶ [Noisy GIFs]
       │       [Blurry GIFs]
       │       [Low-Resolution GIFs]
       ↓
[GIF Splitter → Frame Extractor]
       ↓
[Preprocessing (Resize, Normalize)]
       ↓
[GFPGAN Enhancement (Per Frame)]
       ↓
[Temporal Consistency Layer (Optical Flow + Temporal Loss)]
       ↓
[Frame Merger → GIF Reconstruction]
       ↓
[Enhanced GIF Output]
       ↓
[Evaluation Metrics: PSNR, SSIM, GMSD, T-MSE]
```

---

## 📊 Key Components

### 1. **Raw Video Collection**

* Source: Public social media platforms (e.g., YouTube, Instagram)
* Type: Facial expression videos of varying quality

### 2. **GIF Categorization**

After converting videos into GIFs, they are divided into:

* **Noisy GIFs** – Artificial noise or compression artifacts
* **Blurry GIFs** – Motion blur or camera shake
* **Low-Resolution GIFs** – Downsampled or pixelated

### 3. **Frame Extraction & Preprocessing**

* Frames are extracted using `PIL` or `OpenCV`.
* Preprocessed with normalization and resizing to match GFPGAN input requirements.

### 4. **GFPGAN Model**

* Applied frame-by-frame to enhance facial details.
* Handles deblurring, super-resolution, and artifact removal.

### 5. **Temporal Consistency Module**

* Uses Optical Flow and Temporal Loss to maintain motion consistency.
* Prevents flickering or visual instability between frames.

### 6. **GIF Reconstruction**

* Enhanced frames are stitched back with the original timing.
* Ensures smooth and coherent motion in final output.

### 7. **Evaluation Metrics**

* **PSNR** – Measures pixel-level quality
* **SSIM** – Measures structural similarity
* **GMSD** – Measures perceptual distortion
* **T-MSE** – Measures consistency over time

---

## 🚀 How to Run

### ✅ Prerequisites

* Python 3.8+
* CUDA-compatible GPU (recommended)
* Install requirements:

```bash
pip install -r requirements.txt
```

### 📂 Dataset Structure

```bash
dataset/
├── raw_videos/
├── gifs/
│   ├── blurry/
│   ├── noisy/
│   └── low_res/
├── frames/
│   ├── input/
│   └── enhanced/
└── output_gifs/
```

### 🛠️ Steps

1. Convert videos to categorized GIFs
2. Split each GIF into frames
3. Preprocess and enhance frames via GFPGAN
4. Apply temporal consistency
5. Reconstruct enhanced GIF
6. Evaluate results with metrics

---

## 📈 Results (Sample Comparison)

| Input GIF                     | Enhanced GIF                        |
| ----------------------------- | ----------------------------------- |
| ![low](samples/lowres.gif)    | ![enh](samples/lowres_enhanced.gif) |
| ![blurry](samples/blurry.gif) | ![enh](samples/blurry_enhanced.gif) |

---

## 🧪 Future Enhancements

* Multilingual lip-sync support
* Integration with LLaVA or CLIP for content-aware enhancement
* Real-time deployment via web interface
* Support for full video (not just GIFs)

---

## 📚 References

* [GFPGAN by Tencent ARC](https://github.com/TencentARC/GFPGAN)
* [RAFT for Optical Flow](https://github.com/princeton-vl/RAFT)
* [Vapory for Temporal Loss](https://arxiv.org/abs/2011.12596)

---

## 🙌 Acknowledgements

Thanks to the open-source community and academic mentors for guidance and resources.

---
