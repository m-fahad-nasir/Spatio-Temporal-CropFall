<h1 align="center">
  Spatio-Temporal Crop Fall
</h1>

<h2 align="center">
  A Multimodal Framework for Spatial-Temporal Crop Fall Analysis and Pre-emptive Agricultural Decision-Making
  
</h2>




<div align="center">
  <a href="https://scholar.google.com/citations?hl=en&user=fZkn9poAAAAJ">Mobeen ur Rehman</a> &nbsp;•&nbsp;
  <a href="https://scholar.google.com/citations?user=g9gcbl0AAAAJ&hl=en&oi=ao">Muhammad Fahad Nasir</a> &nbsp;•&nbsp;
  <a href="https://scholar.google.com/citations?user=bCC3kdUAAAAJ&hl=en">Irfan Hussain</a> &nbsp;•&nbsp;
</div>

<h4 align="center">
  <a href="https://www.frontiersin.org/journals/plant-science/articles/10.3389/fpls.2025.1735096/full"><b>Paper</b></a> &nbsp;•&nbsp; 
  <a href="https://www.youtube.com/@Dr._Irfan_Robotics_Lab_KU"><b>Video</b></a>
</h4>

<div align="center">

<img height="65" alt="image" src="https://github.com/user-attachments/assets/f9af6b5d-b8f3-4ca9-9398-d1d01cea6262" />  &nbsp;&nbsp; <img height="65" alt="image" src="https://github.com/user-attachments/assets/5dd33fad-d340-4fa4-b47b-6b2c3e44819a"  />&nbsp;&nbsp; <img height="65" alt="image" src="https://github.com/user-attachments/assets/b50ab72b-f752-4941-9a6a-b0a0cfcecaa7" />

</div>

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg



## 🌾 Overview

Accurate crop fall detection is essential for agricultural sustainability, enabling timely interventions to minimize yield loss. Existing approaches based primarily on remote sensing or meteorological models struggle to capture the dynamic spatial-temporal nature of crop growth.

We propose a **modular, multi-modal framework** that:

- Leverages **drone imagery** and **Oriented Bounding Box (OBB)** annotations for precise spatial localization of crop fall regions.
- Performs **temporal pattern analysis** (isolated, scattered, clustered) across crop growth phases.
- Uses a **Perception Module** for image stitching, crop fall quantification, and spatial pattern classification.
- Generates **dense field-level captions** via a spatio-temporal vision-language pipeline (Phi-3.5 based).
- Combines structured perception outputs with VLM/LLM reasoning to produce **interpretable, phase-aware, actionable agricultural insights**.

<img width="1966" height="921" alt="image" src="https://github.com/user-attachments/assets/9e031775-f3ea-4302-b30c-23c76ba7e3e1" />


## ✨ Key Contributions

- A high-resolution **temporal drone dataset** with OBB annotations for crop fall detection and yield prediction (525 field images, 8,589 labeled OBBs across 7 fields).
- A **unified multi-modal framework** integrating OBB detection, spatio-temporal modeling, and VLM-LLM reasoning.
- A **Perception Module** for field stitching, crop fall quantification, and spatial pattern classification (isolated, scattered, clustered).
- An **explainable temporal reasoning mechanism** enabling phase-aware agricultural decision support.

---

## 📁📊 Dataset

- **525** high-resolution drone field images
- **8,589** labeled Oriented Bounding Boxes (OBBs)
- **7** distinct crop fields, spanning variations in soil type, environmental conditions, and management practices
- **5 temporal phases** (P1–P5) representing the full crop growth cycle, from normal growth to severe crop loss

<img width="608" height="720" alt="Barley Fields" src="https://github.com/user-attachments/assets/9a1ad885-429b-40b1-9f3b-3014424a6421" />
<img width="1373" height="521" alt="OBB vs BB - Small" src="https://github.com/user-attachments/assets/380c8109-cb1a-4420-9e6f-2968daaa3c84" />



| Phase | Description |
|-------|-------------|
| P1–P2 | Normal growth — baseline establishment |
| P3 | Mild crop fall, often due to soil deficiencies |
| P4 | Crop fall caused by pests or environmental stress |
| P5 | Severe crop loss requiring immediate mitigation |

Further dataset details and phase-wise breakdowns are available in the supplementary material.

You can download the dataset used in this study from the following link:  
📥 [Google Drive – Dataset](https://drive.google.com/drive/folders/1s4LmaWyT2hOpbk4pm-X65qN5lNkH3K0a?usp=sharing)



---

## 🧠 Method Summary

1. **OBB Detection & Benchmarking** — Fine-tuned YOLO variants (v8 / v11) predict oriented bounding boxes for crop fall regions, using a composite loss (center + size + orientation).
2. **Perception Module** — Stitches temporal field imagery (SIFT + RANSAC), computes crop fall percentage, and classifies spatial patterns (isolated / scattered / clustered) via density and distance metrics.
3. **Dense Caption Generation** — A spatio-temporal adapter (spatial pooling + temporal self-attention) feeds aggregated features into a Phi-3.5-based language decoder for rich field-level descriptions.
4. **LLM-Based Reasoning** — Structured attributes (phase, fall %, pattern) and dense captions are fused into a prompt for a commercial LLM (e.g., GPT-4o), producing actionable reports with causes and mitigation strategies.

---

## 📈 Results Highlights

- **OBB Detection:** YOLO v8-l achieves the best accuracy–efficiency trade-off (mAP@0.5 = 93.7, 19.98 ms).
- **Pattern Classification:** 91.2% accuracy on isolated, 94.4% on clustered crop fall patterns.
- **Dense Captioning:** Phi-3.5 outperforms BLIP-2, Qwen2-VL-2B, CLIP, Florence, LLAVA, and LLaMA 3.2 on BLEU-4, ROUGE-L, and CIDEr.
- **Proposed Pipeline vs. Baseline VLM:** Average gains across 7 fields — BLEU-4: 0.0609, ROUGE-L: 0.3091, METEOR: 0.2919, CIDEr: 0.1612.
- **LLM Reasoning:** GPT-4o achieves 85.7% accuracy in identifying crop fall causes when given all inputs (fall %, pattern, temporal data).


---

## 🖼️ Visualizations

Comprehensive visualizations of the dataset, detection results, dense captions, and end-to-end reasoning pipeline are provided below.

<img width="1080" height="984" alt="OBBs - Small" src="https://github.com/user-attachments/assets/f41659bb-028a-49bb-a323-2120e6626797" />
<img width="2153" height="869" alt="End-to-End" src="https://github.com/user-attachments/assets/ea01c041-c57d-4e06-b568-d0e0172218a9" />


---

## 🚀 Code

> 🔧 Code release coming soon. This section will include:
> - Dataset loading & preprocessing scripts
> - OBB detection training/evaluation (YOLO v8/v11)
> - Perception Module (stitching, fall % computation, pattern classification)
> - Dense captioning pipeline (spatio-temporal adapter + Phi-3.5)
> - LLM reasoning & prompt templates

---

## 📜 Citation

```bibtex
@inproceedings{TBD-2026spatialtemporal,
  title     = {A Multimodal Framework for Spatial-Temporal Crop Fall Analysis and Pre-emptive Agricultural Decision-Making},
  author    = {Rehman M, Nasir MF, Hussain I},
  booktitle = {TBD},
  year      = {2026},
  note      = {TBD}
}
```
