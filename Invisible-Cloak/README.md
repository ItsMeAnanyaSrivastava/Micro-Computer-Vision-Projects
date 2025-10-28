# Invisible Cloak — invisible.py

A simple computer-vision demo that creates an "invisibility cloak" effect using OpenCV: replace a colored cloak with the previously captured background so the wearer appears invisible.

## Features
- Real-time webcam or video-file processing
- HSV-based color segmentation with morphological cleanup
- Background capture and seamless replacement
- Optional video output

## Requirements
- Python 3.8+
- OpenCV (opencv-python)
- NumPy

Install quickly:
```
python -m pip install opencv-python numpy
```
Or use a requirements file:
```
pip install -r requirements.txt
```

## Files
- invisible.py — main script to run the effect
- (optional) requirements.txt — dependency list

## Usage
Run with webcam (default):
```
python invisible.py
```

Run with a video file:
```
python invisible.py --video path/to/video.mp4
```

Common command-line options (adjust depending on script implementation):
- --video <path>      Use a video file instead of webcam
- --output <path>     Save processed output to file (e.g., out.avi)
- --color <name>      Preset cloak color: red, green, blue (or provide HSV range)
- --bg-frames <N>     Number of frames to capture background (default: 60)
- --show-hsv          Show intermediate HSV mask window for tuning

Example (webcam, red cloak, save output):
```
python invisible.py --color red --output result.avi
```

## Tips for best results
- Use a solid-colored cloak that contrasts with the background and subject skin/clothing.
- Capture background without the subject in frame (move out while background is recorded).
- Even, bright lighting reduces noise and improves mask quality.
- If effect is poor, tune HSV ranges or show the HSV mask window to pick thresholds interactively.

## Troubleshooting
- No effect / cloak not detected: adjust HSV thresholds for the cloak color; try a cleaner background.
- Flickering or small holes: apply morphological open/close or increase background frames.
- Webcam access error: ensure no other app is using the camera and correct device index is set.

## License
MIT License — see LICENSE file or include your preferred license.

## Attribution
Author: Your Name (replace as needed). Adapt and reuse for learning and demos.

Enjoy experimenting with the invisible cloak effect!