# Vessel review

A single-file, offline browser tool for reviewing coronary stenosis labels on straightened (CPR) vessel images.

- Open `index.html` (or the GitHub Pages URL) in Chrome or Edge, then choose a local folder containing `manifest.json` and the images.
- **All data stays on the local computer.** Files are read in the browser and are never uploaded. Answers are kept in browser storage until exported as CSV.
- Enter a reader code first; each reader's answers are stored separately and are not visible to other readers.
- Two modes:
  - **Blinded review**: click lesion positions, set stenosis grade and lesion nature (plaque types, myocardial bridge, in-stent restenosis, artifact, other); then reveal the report excerpt and parsed label, record a verdict and the final grade. Blinded answers lock after reveal; "redo" resets a vessel and flags it.
  - **Teaching annotation**: the report is shown from the start; mark points or ranges and write an explanation of what the problem on the image is and why. Always editable.
- Click a red marker number to delete it (before reveal in blinded mode).
- `demo/` contains synthetic images (not patient data) for trying the interface.

## Optional overlays (manifest fields)
- `locator`: small frontal MIP image with the vessel drawn.
- `branches` [{name, mm}]: branch take-offs, dashed blue lines.
- `segments`, `ostia` [{name, from, to}]: estimated segment and ostium ranges, shown under the vessel. Segments named in the report text are highlighted once the report is shown.
- `calcium` [[from, to]]: calcified ranges, shown once the report is shown.
- A built-in glossary explains report terms (segment names, plaque types, stenosis grades) once the report is shown.

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
