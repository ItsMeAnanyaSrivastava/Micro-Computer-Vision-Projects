# Invisible Cloak — README

A short README for `invisible.py`. This script implements a simple "invisibility cloak" effect using a webcam and OpenCV: it detects a cloak (by color), then replaces the cloak region with a previously captured background so the cloak appears transparent.

## Features
- Capture a static background frame
- Detect cloak color in HSV space
- Smooth and clean mask with morphological ops
- Composite live feed with background where cloak is detected
- Optional parameters for color ranges and output

## Requirements
- Python 3.7+
- OpenCV (cv2)
- NumPy

## Installation
```
pip install opencv-python numpy
```

## Usage
Typical run from project root:
```
python invisible.py
```

Common options (adjust names to your script's arguments if different):
```
# capture background, then run invisibility with default red cloak detection
python invisible.py --capture-bg

# specify webcam index, save output video, set HSV thresholds
python invisible.py --camera 0 --output output.avi --hsv-low 0,120,70 --hsv-high 10,255,255

# toggle preview windows or debug display
python invisible.py --no-preview
```

## Algorithm (summary)
1. Capture several frames at start and compute a stable background.
2. Convert each incoming frame to HSV.
3. Threshold HSV to get mask of cloak color (e.g., red).
4. Refine mask with open/close and blur to remove noise.
5. Use mask to replace cloak pixels in current frame with corresponding pixels from background.
6. Display and optionally save result.

## Tips
- Calibrate HSV thresholds for your cloak color and lighting.
- Use a plain, contrasting background and steady lighting for best results.
- Capture background without the cloak in frame.

## Troubleshooting
- If cloak not detected, adjust HSV ranges or increase number of background frames.
- Flicker/noise: apply stronger morphological operations and Gaussian blur.

## License
MIT — adapt as needed.

## Credits
Based on common OpenCV invisibility-cloak approaches and tutorials.

(Modify command-line flags above to match the exact arguments in your `invisible.py`.)