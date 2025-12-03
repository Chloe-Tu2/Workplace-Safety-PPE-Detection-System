# Project Documentation & Presentation Files

This folder contains the official documentation, presentation slides, and transparency logs for the **Workplace Safety PPE Detection System**.

Below is a detailed breakdown of the four core files located in this directory.

---

## 1. `AI_USAGE_LOG.md`
**File Type:** Markdown Documentation  
**Purpose:** Academic Integrity, Transparency Report & Code Attribution

This file is a complete, honest record of how Artificial Intelligenc AI was used to build this project. It proves that while AI tools were used for help, we made all the important decisions.

### **In-Depth Details:**
* **The "Human First" Rule:** The log explains the team's core rule: *We researched → AI explained → We decided → AI helped implement.* AI was never used to replace human thinking.
* **Tools Used:**
    * **ChatGPT-4:** Used for research, understanding concepts, and debugging errors.
    * **Claude:** Used for reviewing code, writing documentation, and optimization strategies.
    * **GitHub Copilot:** Used for code completion and generating standard "boilerplate" code.
* **Code Attribution Stats:**
    * **Dataset Preprocessing:** ~30% AI-assisted (Helped with the logic for splitting data evenly).
    * **Model Training Pipeline:** ~40% AI-assisted (Helped select settings and structure the training loop).
    * **Evaluation Metrics:** ~50% AI-assisted (Helped generate confusion matrices and analyze class accuracy).
    * **Deployment/Demo Code:** ~25% AI-assisted (Helped with the inference pipeline and visuals).
    * **Documentation:** ~60% AI-assisted (Helped with technical writing and structure).
    * **Overall:** Approximately **40%** of the code was generated with AI assistance, while **60%** was written independently after understanding the AI's explanations.

---

## 2. `PPE-10-Slide-Presentation-Text.md`
**File Type:** Markdown Script  
**Purpose:** Presentation Content & Speaker Notes

This file contains the full text, script, and detailed plan for the Midterm Presentation. It serves as the "source of truth" for everything shown in the slides.

### **In-Depth Details:**
* **The Problem:** It outlines why this project exists—**4,764 workers died** in 2020, and 70% of falls happen because people aren't wearing safety gear.
* **The Solution:** Describes the 5-step pipeline: *Camera Input → YOLOv8 Detection → Compliance Check (Is the helmet on?) → Alert System → Report.*
* **Technical Stack:** Explains that the project runs for **$0** using free tools:
    * **Google Colab** (Free GPU for training)
    * **Kaggle** (Free dataset hosting)
    * **YOLOv8 & PyTorch** (Free open-source software)
* **Project Plan:** Includes a week-by-week schedule (Weeks 10–15) showing exactly when the data was downloaded, when the model was trained, and when the demo was recorded.
* **Risk Management:** It lists "Backup Plans." For example, if the model accuracy was too low (<80%), the plan was to use "aggressive data augmentation" (flipping and rotating images) to fix it.

---

## 3. `MD_DemarcusCrump_ChloeTu__ITAI1378.pptx`
**File Type:** PowerPoint Presentation  
**Purpose:** Visual Slides for Class Presentation

This is the editable slide deck used for the final class presentation. It visualizes all the data found in the text file above.

### **In-Depth Details:**
* **Visual Diagrams:** Instead of just text, this file contains the flowcharts showing how an image travels from a camera to a safety alert.
* **Project Tier:** Clearly marks this as a **"Tier 2"** project (Medium Difficulty), justified by the use of advanced Object Detection rather than simple classification.
* **Team Roles:**
    * **DeMarcus:** Focused on Model Training & Optimization (making the AI smart).
    * **Chloe:** Focused on Data Analysis & Deployment (making the demo work).
* **Slide Structure:** Contains exactly 10 slides, covering the Title, Problem, Solution, System Diagram, Success Metrics, and Future Resources, matching the course requirements perfectly.

---

## 4. `MD_DemarcusCrump_ChloeTu-ITAI1378.pdf`
**File Type:** PDF Document  
**Purpose:** Portable / Read-Only Version of Slides

This file is identical to the PowerPoint (`.pptx`) above but saved as a PDF.

### **Why this file exists:**
* **Compatibility:** Ensures the slides look exactly the same on any computer (Mac, Windows, Phone) without needing Microsoft PowerPoint installed.
* **Submission Ready:** This is the format typically submitted to professors to ensure fonts and images don't get moved around or broken.
* **Content:** It contains the exact same 10 slides, charts, and diagrams as the PowerPoint file.

---
