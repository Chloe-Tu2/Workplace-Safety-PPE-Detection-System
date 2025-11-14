# Workplace Safety PPE Detection System

## Team Members
- DeMarcus Crump 
- Chloe Tu 

## Project Tier
**Tier 2**: Multi-class object detection with compliance logic for PPE verification, real-time inference capabilities, and integration of multiple detection classes for comprehensive workplace safety monitoring.

## Problem Statement
Construction workers and warehouse employees face significant occupational hazards - non-compliance with Personal Protective Equipment (PPE) requirements leads to preventable injuries and deaths. Current workplace safety monitoring relies on manual observation and periodic inspections, which are inconsistent, error-prone, and cannot monitor all workers simultaneously.

## Solution Overview
We're building a real-time computer vision system that detects PPE on workers, automatically verifies compliance, and generates alerts for violations. The system uses YOLOv8 to identify PPE items (helmets, vests, masks) and workers in workplace cameras, applies rule-based compliance checking, and outputs annotated images with safety status.

## Technical Approach
- **CV Technique:** Object Detection (Multi-class detection of PPE items and workers)
- **Model:** YOLOv8 (You Only Look Once, version 8)
- **Framework:** PyTorch + Ultralytics YOLO Library
- **Why this approach:** Real-time PPE detection requires fast inference (30+ FPS), high accuracy (90%+ mAP), and multi-class capability. YOLOv8 balances speed and accuracy perfectly for workplace safety applications.

## Dataset
- **Source:** [Construction Site Safety Image Dataset Roboflow](https://www.kaggle.com/datasets/snehilsanyal/construction-site-safety-image-dataset-roboflow)
- **Size:** 2801 images (2605 training, 114 validation, 82 test)
- **Labels:** Hardhat, NO-Hardhat, Safety Vest, NO-Safety Vest, Mask, NO-Mask, Person, Gloves (~10 classes)
- **Link:** https://www.kaggle.com/datasets/snehilsanyal/construction-site-safety-image-dataset-roboflow

## Success Metrics
- **Primary Metric:** mAP@50 (Detection Accuracy)
- **Target:** ≥75% mAP
- **Secondary Metrics:** Precision ≥85%, Recall ≥75%, Inference Speed <100ms per image (CPU)

## Week-by-Week Plan
- **Week 10:** Download dataset, set up Google Colab environment, explore data, create GitHub repo
- **Week 11:** Train YOLOv8 model on PPE dataset - achieve ≥70% mAP
- **Week 12:** Evaluate model, improve accuracy with augmentation - reach ≥75% mAP
- **Week 13:** Build compliance logic, create demo with visual overlays - functional end-to-end system
- **Week 14:** Record demo video, final testing, complete documentation
- **Week 15:** Present final project with live/recorded demo

## Resources Needed
- **Compute:** Google Colab (Free GPU)
- **Cost:** $0 (all free resources)
- **APIs:** None required (direct dataset download from Kaggle)

## Risks & Mitigation

| Risk | Probability | Mitigation |
|------|-------------|------------|
| Low accuracy (<75% mAP) | Medium | Apply aggressive augmentation, try YOLOv8-medium variant, fine-tune on hard examples |
| Class imbalance | Medium | Use weighted loss functions, class-specific augmentation |
| Occluded PPE | Medium | Train on augmented occlusion patterns, adjust detection thresholds |
| Slow inference on CPU | Low | Use YOLOv8-nano for speed, apply quantization |
| Demo technical failure | Low | Record backup demo video, prepare static image fallback |

## AI Usage Log
**Status:** Will be updated throughout Weeks 11-15 as AI tools are used.

## Current Status
- [x] Repository created
- [x] Proposal written
- [x] Dataset acquired
- [x] Model training started
- [x] Demo created
- [ ] Final presentation ready
