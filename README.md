# Using AI to Digitally Restore Historical Artifacts 
---

## 🏛️ Overview

This program is a native desktop program designed to that uses  original state. 


---

## Key Features

- **Runs Natively Within the Python IDE** 
- **User Upload Compatible** - Users can upload an image file from their computer to be restored by the LLM.
- **Image Download** - Users can download the restored image onto their computer. 

---

## HOW IT WORKS

### Computer Vision Anaylsis Diagnostics

Uses computer vision to determine the type of artifact, the 

### 2. Phase 2: Defect-Injected Prompting 
Rather than sending generic restoration prompts that cause generative models to hallucinate or replace the entire image, ARCH-RECON **injects the specific diagnostic defects** into affirmative inpainting directives:
- **Negative-to-Affirmative Purging**: Negative defect terms (e.g., *"severely broken nose"*, *"severed arm stumps"*, *"soot and grime"*) are dynamically translated into affirmative physical targets (e.g., *"complete prominent intact sculpted nose with straight defined bridge"*, *"complete intact sculpted arms and articulated hands"*, *"clean authentic polished surface"*).
- **Medium-Specific Rules**:
  - *Ceramics*: Enforces strict vessel symmetry and forbids attaching 3D anatomical appendages to pottery.
  - *Sculptures & Busts*: Enforces anatomical completeness while preventing unwanted torso attachments on portrait busts.
  - *Architecture*: Re-erects fluted columns and completes pediments while preserving masonry textures.
- **Negative Space Awareness**: Directs the inpainting engine to expand beyond the artifact boundary into adjacent background space to synthesize missing limbs and crowns.
- **Viewpoint Lock**: Strictly locks original camera perspective, lighting, and museum mounting/pedestals.

### 3. Phase 3: Visual Re-Evaluation & Verification Audit
After a restoration pass is generated, ARCH-RECON does not blindly assume the repair succeeded. Instead, it submits the newly restored image back to the Multimodal Vision LLM for an **objective verification audit**:
- The model compares the new image against each original diagnostic item (`#1, #2, #3...`).
- For each item, the vision inspector evaluates:
  - `resolved`: `true` or `false`.
  - `visual_evidence`: A concise observation explaining what is visible (e.g., *"Missing physical pieces restored into complete intact forms"*, *"Surface soot visibly lifted; original terracotta glaze revived"*).
- Compiles an updated count of resolved vs. remaining issues.

### 4. Phase 4: Closed-Loop Cycling & Self-Correction
If defects remain unresolved after an iteration:
1. The auditor generates a targeted `next_remodification_instruction`.
2. The controller injects this instruction along with the remaining unresolved checklist items back into **Phase 2**.
3. A subsequent restoration pass is executed focusing exclusively on the remaining defects.
4. The loop repeats until **all diagnostics are marked `[RESOLVED]`** or the maximum iteration threshold (default: 3 passes) is reached.
5. A comprehensive telemetry log (`restoration_closed_loop_telemetry.json`) is recorded.


## EXAMPLES

## DEMOSTRATION

## USER GUIDE

### 1. Prerequisites
- **Python**: Version 3.10 or higher.
- **System**: Windows, macOS, or Linux (Tkinter support included with standard Python installations).

### 2. Installation
Clone or navigate to the project directory and install the required dependencies:

```bash
pip install pillow requests python-dotenv
```

*(Note: `tkinter` is part of standard Python distributions. On Linux, ensure `python3-tk` is installed if not already present).*

### 3. API Key Configuration
Create or configure a `.env` file in the root directory with your ARC API key:

```env
ARC_API_KEY="your-api-key-here"
```

## 🛡️ License & Acknowledgments

- Developed for historical artifact preservation research and cultural heritage digital reconstruction.
- Computer Vision and Generative Inpainting powered by **DeepSeek-V4.1-Flash** via the **Virginia Tech ARC API**.
