# Using AI to Digitally Restore Historical Artifacts 
---

## OVERVIEW

This repository contains the files for a native desktop application for demonstrating how LLMs can be used to assist in the restoration of historical artifacts via computer vision anaylsis and dynamic prompting. This application uses Virginia Tech's ARC API to assist in the restoration of damaged historical artifact and return them to their oringal condition. 

**NOTE:** This program is mostly for demonstration for the potential of LLMs usage in digital restoration and is not yet capable of consistently outputting fully restored historical artifacts every single time. See the "KNOWN ISSUES" section for more information. 
---

## PROGRAM FEATURES

- **Runs Natively Within the Python IDE** - Uses the Tkinter Python package to run natively within the IDE when the program is ran. 

- **User Upload Compatible** - Users can upload an image file from their computer to be restored by the LLM or select one of the pre-existing images for demonstration. 

- **Image Download** - Users can download the restored image onto their computer.
  
- **Offline Fallback Mode** - The program will continue to run even when no API key is present. 

---

## HOW IT WORKS

### Computer Vision Anaylsis Diagnostics

Uses computer vision to determine the type of artifact, the time period and culture it originates from, and assess the damage that needs to be repaired. 

### Dynamic Restoration Prompting

Uses the results from the computer vision analysis as prompting for restoring the artifact to its original state. 

### Visual Re-Evaluation & Correction

After an artifact is restored, the LLM will reanalyze the image after to check for any unresolved damage and will re-modify the image to resolve any remaining defects. This process continues as a loop until all defects are resolved or until it reaches the user-specfied maximum number or repasses allowed. 

---

## EXAMPLE OUTPUTS

**LLM Restoration of Pottery**

**LLM Resotration of Sculputer**

## VIDEO DEMOSTRATION


---

## KNOWN ISSUES

**LLM Hallucinations** - When restoring the original artifact, the LLM may add additional details to the artifact that were not present in the original image due to misconstrueing different details within the image during the computer vision analysis.

**Partial Restoration** - The LLM does not always full restore the image. 

---

## USER GUIDE

**Download Repository**

**Add API Key**
