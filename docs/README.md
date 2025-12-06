# Project Documentation & Resources

This directory contains the official documentation, presentation slides, download video, and transparency logs for the Workplace Safety PPE Detection System. Below is a detailed breakdown of the four core files located in this directory.

## 📂 Repository Organization

The documentation is organized into two primary folders to separate the Midterm progress from the Final deliverables.

```text
├── Final/
│   ├── Final_DemarcusCrump_ChloeTu__ITAI1378.pdf
│   ├── Final_DemarcusCrump_ChloeTu__ITAI1378.pptx
│   ├── Final-PPE-12-Slide-Presentation-Text.md
│   └── PPE-Demo-Video.mp4
│
├── Midterm/
│   ├── MD_DemarcusCrump_ChloeTu-ITAI1378.pdf
│   ├── MD_DemarcusCrump_ChloeTu__ITAI1378.pptx
│   └── MD-PPE-10-Slide-Presentation-Text.md
│
└── AI_USAGE_LOG.md
```

## 📁 1. Final Project Materials (/Final)

This folder contains the complete deliverables for the final submission of the project (December 3, 2025).

### **Final_DemarcusCrump_ChloeTu__ITAI1378.pdf**

**File Type:** PDF Document (Portable / Read-Only)

**Description:** This is the static export of our final 12-slide presentation.

**Content:** It covers the full project lifecycle, including the Problem & Motivation (20% fatality rate in construction), Technical Approach (YOLOv8s architecture and preprocessing), Results (achieving 77.1% mAP@50 and 88.9% Precision), and Future Work (Edge deployment and dataset expansion).

**Viewing Instruction:** Please open this file directly in GitHub to view the slides. This format ensures all fonts, layouts, and diagrams (such as the architecture flow on Slide 5) render correctly in the browser without requiring a download or PowerPoint software.

---

### **Final_DemarcusCrump_ChloeTu__ITAI1378.pptx**

**File Type:** PowerPoint Presentation (Source File)

**Description:** The editable source file for the final class presentation.

**Note:** This version includes original slide transitions, animations, and editable charts that are flattened in the PDF version.

---

### **Final-PPE-12-Slide-Presentation-Text.md**

**File Type:** Markdown Script

**Description:** A raw transcript of the final presentation.

**Content:** Contains the script, bullet points, and speaker notes for all 12 slides—serving as the source of truth for the presentation content.

---

### **PPE-Demo-Video.mp4**

**File Type:** Video File (MP4)

**Description:** A comprehensive 10-minute video walkthrough of our interactive notebook (`04_demo.ipynb`).

**Content Includes:**
- Model Loading: Initializing the YOLOv8s model (11.2M params)
- Batch Inference: Processing 423 test images in real-time
- External Image Tests: Demonstrating generalization
- Deployment: Exporting the model to ONNX and TorchScript formats

---

## 📁 2. Midterm Project Materials (/Midterm)

This folder contains the proposal and progress report materials submitted during the midterm phase (October 30, 2025).

### **MD_DemarcusCrump_ChloeTu-ITAI1378.pdf**

**File Type:** PDF Document  
**Description:** Static 10-slide midterm proposal.

**Content:** Includes initial project scope, dataset selection, system diagram, and the week-by-week development plan.

---

### **MD_DemarcusCrump_ChloeTu__ITAI1378.pptx**

**File Type:** PowerPoint Presentation

**Description:** Editable source file for the midterm presentation.

**Details:**  
- Marks the project as "Tier 2" (Medium Difficulty)  
- Includes editable tables for Success Metrics (Slide 7)  
- Includes Challenges & Backup Plans (Slide 9), such as augmentation for occluded PPE  

---

### **MD-PPE-10-Slide-Presentation-Text.md**

**File Type:** Markdown Script

**Description:** Text transcript of the midterm proposal.

**Details Covered:**  
- Problem: $1 billion per week cost of workplace injuries  
- Technical Stack: $0 cost using Google Colab + Kaggle  
- Risk Management: Backup plans (e.g., YOLOv8-medium fallback)  

---

## 🤖 AI Usage & Transparency

### **AI_USAGE_LOG.md**

**File Type:** Markdown Documentation  
**Purpose:** Academic Integrity, Transparency Report & Code Attribution

**Description:** A detailed transparency log documenting AI usage throughout the semester.

### **The “Human First” Workflow**
**We researched → AI explained → We decided → AI helped implement**

### **Tools Used**
- **ChatGPT-4:** Researching model variants & debugging  
- **Claude:** Fixing Google Drive persistence  
- **GitHub Copilot:** Boilerplate visualization code  

### **Code Attribution Breakdown**
- Dataset Preprocessing: ~30% AI-assisted  
- Model Training: ~40% AI-assisted  
- Evaluation: ~50% AI-assisted  
- Documentation: ~60% AI-assisted  
- **Overall:** ~40% AI-generated, ~60% human-written  

---

All content above is formatted and ready for use as a GitHub `README.md`.
