# ARC Artifact Restoration Pipeline

An automated, two-stage artificial intelligence system designed to catalog, analyze, and physically reconstruct damaged historical artifacts, ancient sculptures, pottery vessels, paintings, and classical architecture.

The system utilizes multimodal vision large language models (**DeepSeek-V4.1-Flash**) to perform archaeological cataloging, synthesizes category-adaptive reconstruction prompts subject to strict universal conservation rules, and executes high-fidelity image editing via the Virginia Tech ARC LLM API.

---

## ✨ Key Features

1. **Multimodal Archaeological Cataloging:**
   - Automatically determines artifact classification (`sculpture`, `pottery`, `painting`, `architecture`, or `artifact`).
   - Identifies historical period, culture, origin, and material (e.g., *Pentelic marble*, *terracotta*, *limestone poros*, *Pompeian fresco*).
   - Generates a detailed structural condition and damage report.

2. **Mandatory Universal Conservation Constraints:**
   Every reconstruction follows six non-negotiable restoration rules regardless of category:
   - **Strict Composition & Perspective Preservation:** The camera angle, viewpoint, framing, position, zoom level, and spatial composition remain completely identical to the source image.
   - **Complete Defect Rebuilding:** Missing limbs, broken handles, fractured columns, and chipped segments are fully reconstructed without leaving broken stumps, jagged fractures, or cut-offs.
   - **Surface Cleansing:** Surface dirt, dust, soil encrustation, mold, and modern weathering are removed.
   - **Texture Integrity:** Preserves natural stone, ceramic, and plaster textures without creating synthetic, plastic, or overly smoothed surfaces.
   - **Material Consistency:** Applies only historically authentic materials suitable for the artifact's era.
   - **Style Consistency:** Adheres strictly to the aesthetic conventions of the artifact's historical culture.

3. **Domain-Specific Reconstruction Directives:**
   - **Sculptures:** Rebuilds bilateral limbs (arms, hands, fingers) attached naturally to shoulders in classical poses (e.g., *contrapposto*), restores facial features (nose, lips, hair), and smooths weathered drapery.
   - **Pottery & Ceramics:** Reconstructs symmetrical dual handles, repairs jagged rim/mouth breaks into unbroken circular lips, and enforces authentic black-figure slip glaze on necks, rims, and bases while preserving terracotta figure panels.
   - **Architecture:** Rebuilds collapsed fluted columns into complete continuous peristyle colonnades, reconstructs triangular pediments and tiled gable roofs, spans unbroken entablatures, and clears fallen ground rubble into clean level steps.
   - **Paintings & Frescoes:** Inpaints missing, flaked, and abraded sections in matching historical brushwork while removing craquelure and yellowed varnish.
