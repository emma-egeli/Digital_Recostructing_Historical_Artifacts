# Digital Restoration of Historical Artifacts 
---

## 🏛️ Overview

This program is a native desktop program designed to that uses Virginia Tech ARC API to digitally analyze historical artifacts and pieces, and restore them to their original state. 


---

## ✨ Key Features

- **Runs Natively Within Python** - 
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


## Sample Demostration

## 🖥️ User Interface Overview

The Tkinter desktop interface is organized into a clean, dark-themed workstation layout:

## 📊 Telemetry & Audit Output Example

## 🚀 Getting Started

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

> **Note:** If an API key is not configured or network access is unavailable, ARCH-RECON will automatically employ its built-in **architectural & optical baseline fallback engine** to ensure uninterrupted functionality. However, this does not do any substantial restoration. 

---

## 💻 Usage

### Launch Native Desktop GUI (Default)
Run the application without arguments to launch the graphical desktop workstation:

```bash
python main_tkinter.py
```

1. Click **Choose Artifact Photo...** or select one of the preset sample buttons (**🏛️ Temple**, **🏺 Pottery**, **👑 Pharaoh**, etc.).
2. Wait for the initial vision diagnostic checklist to populate automatically.
3. Configure the number of iterations (default: 3) and check **Expand Negative Space** if needed.
4. Click **🔄 Run Closed-Loop Restoration**.
5. Watch the live color-coded audit trail update as each issue is resolved.
6. Toggle between **Restored Artifact** and **Side-by-Side Comparison** and export high-resolution results.

---

### Command-Line Interface (CLI Mode)

ARCH-RECON also features a headless command-line interface for automated batch processing, scripting, or remote servers:

#### 1. Full Closed-Loop Restoration via CLI:
```bash
python main_tkinter.py --image sample_pottery.jpg --max-iterations 3 --out restored_pottery.png --comp-out comparison_pottery.jpg
```

#### 2. Computer Vision Forensic Diagnosis Only:
```bash
python main_tkinter.py --image sample_temple.jpg --diagnose-only
```

#### CLI Options Reference:
| Option | Type | Default | Description |
| :--- | :---: | :---: | :--- |
| `--image` | `str` | *None* | Path to input artifact photo (triggers CLI mode). |
| `--cli` | `flag` | `False` | Run in headless command-line mode. |
| `--diagnose-only` | `flag` | `False` | Run Phase 1 vision diagnostics only and output raw JSON report. |
| `--max-iterations` | `int` | `3` | Maximum closed-loop remodification passes. |
| `--expand-negative-space` | `flag` | `False` | Expand into negative empty air space for severed limbs or architecture. |
| `--out` | `str` | `closed_loop_restored.png` | Destination filepath for restored image. |
| `--comp-out` | `str` | `closed_loop_comparison.jpg` | Destination filepath for side-by-side comparison image. |

---

## 📁 Repository Structure

```
Restoration AI/
├── main_tkinter.py                          # Core Desktop Tkinter App, Closed-Loop Controller & CLI
├── restoration_closed_loop_telemetry.json  # Comprehensive audit history and diagnostic telemetry
├── .env                                    # API credentials configuration
├── sample_temple.jpg                       # Classical Greek monumental temple ruin
├── sample_pottery.jpg                      # Ancient Attic black-figure amphora
├── sample_egyptian_pharaoh.jpg             # Egyptian Pharaoh royal limestone bust
├── sample_chinese_terracotta.jpg           # Qin Dynasty Terracotta Army warrior
├── sample_mesopotamian_relief.jpg          # Carved limestone bas-relief antiquity
├── sample_fresco.jpg                       # Ancient wall mural fresco painting
└── README.md                               # Project documentation
```

---

## 🛡️ License & Acknowledgments

- Developed for historical artifact preservation research and cultural heritage digital reconstruction.
- Computer Vision and Generative Inpainting powered by **DeepSeek-V4.1-Flash** via the **Virginia Tech ARC API**.
