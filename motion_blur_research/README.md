# Motion blur research (ICMTC, SkyXperts CV)

How much motion blur a fixed-wing drone gets, how much it hurts small-object detection, and how to fix it.

## Files

| Path | What it is |
|---|---|
| `motion_blur.ipynb` | The notebook, already run with all results and plots saved. One section per milestone: M2 fake motion blur, M3 blur score and sharpest-frame selection, M4 YOLO recall vs blur on VisDrone, M5 fixes (Wiener deblurring, blur augmentation) |
| `figures/` | Key plots exported from the notebook, ready for slides |
| `assets/` | A test photo, a test video and the pretrained `yolov8n.pt` model the notebook uses |
| `datasets/VisDrone2019-DET-val/` | VisDrone validation set (548 drone photos), used in M4 and M5 |
| `One-page summary.pdf`, `motion_blur_doc.pdf` | The written summary and full documentation |

## Main result

Small objects (under 32 × 32 px) keep 87% recall at 2 px of blur but only 62% at 4 px and 27% at 8 px. The flag is a small object at 75 m, so blur should stay at 2 px or less: **shutter 1/500 s or faster** at 20 m/s and 75 m, plus sharpest-frame selection.

## Run it

Python with `opencv-python`, `numpy`, `matplotlib`, `pandas` and `ultralytics`. Open the notebook and Run All (about 5–8 minutes on a CPU). If `datasets/` is missing, download `VisDrone2019-DET-val.zip` from https://github.com/ultralytics/assets/releases/download/v0.0.0/VisDrone2019-DET-val.zip and unzip it into `datasets/`.
