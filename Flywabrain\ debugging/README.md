# Flywabrain Debugging: Visual Pathway to Mushroom Body

This folder contains comprehensive documentation and analysis of the visual signal pathway in the DOOMFLY neural simulation, including the critical missing link: **CT1 neurons**.

## Quick Start: Launch Jupyter Lab

From the doomfly repository root directory, run:

```bash
cd /home/melinda2/Git/doomfly && \
source .venv-neural/bin/activate && \
jupyter lab --no-browser --ip=0.0.0.0 --port=8888
```

Then open in your browser:
- **Local access:** http://127.0.0.1:8888/lab?token=... (check terminal for full URL)
- **From Windows (WSL2):** http://Peter4Ever:8888/lab?token=...

## Contents

### 📓 Notebooks
- **Vision to mushroom body issue.ipynb** - Complete analysis of the visual pathway blockage and solution

## Key Findings

### The Problem
- Kenyon cells (KC) in the mushroom body were receiving **zero visual input**
- Despite retina and lamina firing properly, T4/T5 motion detectors couldn't drive learning

### The Solution
- **CT1 neurons (bodyIds: 10009, 10157)** relay motion signals from T4/T5 to KC
- FlyWire validation confirms: 6,660 upstream inputs (T4/T5 motion), 7,570 downstream outputs (to KC)
- Only 2 CT1 neurons exist in the entire brain — one per hemisphere

### Cell IDs (MaleCNS v1.0 connectome)
| Layer | Sample IDs | Count |
|-------|-----------|-------|
| Retina | 11139, 15479, 15625 | 4,188 |
| Lamina | 10465, 10350, 10694 | 7,114 |
| T4/T5 | 13882, 14326 | 13,585 |
| **CT1** | **10009, 10157** | **2** |
| KC | 11862, 13173, 14292 | 4,064 |
| MBON11 | 10704, 11402 | 2 |

## References

- **FlyWire Codex:** https://codex.flywire.ai/
- **Connectome:** MaleCNS v1.0 (male Drosophila melanogaster)
- **Data:** `connectome_data/malecns_v1/annotations.feather` + `outputs/doom/malecns_v1/graph.npz`

## Next Steps

1. ✅ Identify missing CT1 pathway (DONE)
2. ⏳ Implement CT1 sensory input in simulator (`doom/native.py`)
3. ⏳ Validate visual learning with CT1 active
4. ⏳ Compare training performance before/after fix
