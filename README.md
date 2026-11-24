# Vessel review

A single-file, offline browser tool for reviewing coronary stenosis labels on straightened (CPR) vessel images.

- Open `index.html` (or the GitHub Pages URL) in Chrome or Edge, then choose a local folder containing `manifest.json` and the images.
- **All data stays on the local computer.** Files are read in the browser and are never uploaded. Answers are kept in browser storage until exported as CSV.
- Two steps per vessel: (1) blinded reading — click lesion positions on the vessel, set stenosis grade and plaque type; (2) reveal the report excerpt and parsed label, then record a verdict and the final grade.
- `demo/` contains synthetic images (not patient data) for trying the interface.

## manifest.json
```json
{"set_id": "set1", "reader": "R1",
 "vessels": [{"id": "case_vessel", "vessel": "LAD", "length_mm": 140,
   "cpr": [{"file": "a_cpr0.png", "label": "0°"}, {"file": "a_cpr90.png", "label": "90°"}],
   "cross": [{"file": "a_x10.png", "mm": 10}],
   "report_grade": 3, "report_segment": "pLAD", "report_text": "..."}]}
```
The CPR image's horizontal axis must run from ostium (left) to distal end (right) and span `length_mm`.

Do not put patient data in this repository.
