# Camera Calibration Toolkit

## About
This project is a modular toolkit for camera calibration using Aruco markers, designed for extracting both intrinsic and extrinsic camera parameters. The toolkit allows users to:
- Generate custom Aruco boards for calibration.
- Capture calibration images from live video streams or camera feeds.
- Compute intrinsic and extrinsic parameters of the camera.
- Validate calibration results by projecting 3D points onto the image.

## Topics
- computer-vision
- camera-calibration
- aruco-markers
- image-processing
- 3d-geometry
- opencv
- intrinsic-parameters
- extrinsic-parameters

## Features
- **Aruco Board Generation**: Create custom Aruco boards to use for calibration.
- **Image Capture**: Capture calibration images from a live video stream or camera.
- **Intrinsic Calibration**: Compute the camera's intrinsic parameters such as focal length, optical center, and distortion coefficients.
- **Extrinsic Calibration**: Compute the camera's extrinsic parameters including rotation and translation vectors.
- **Calibration Testing**: Visualize the accuracy of the calibration by projecting 3D points onto the image and comparing with actual image points.

## Requirements
The project requires Python and the following libraries:
- `opencv-python`
- `numpy`
- `PyYAML`
- `tqdm`

To install these dependencies, run:
```bash
pip install -r requirements.txt
```

## Project Structure
```bash
.
├── README.md
├── main.py               # Main file to run the entire calibration process
├── utils
│   ├── aruco_generator.py  # Generates custom Aruco boards
│   ├── image_capture.py    # Captures calibration images from a camera or video feed
│   ├── intrinsic_calib.py  # Performs intrinsic camera calibration
│   ├── calib_test.py       # Tests the accuracy of the calibration results
│   ├── extrinsic_calib.py  # Performs extrinsic calibration and projects 3D points
├── data                   # Directory to store calibration images and results
├── debug                  # Directory to store test outputs
└── requirements.txt       # Required dependencies for the project
```

## How to Use
**1- Generate Aruco Board:** Run the script to generate an Aruco board for calibration:
```bash
python utils/aruco_generator.py --rows <num_rows> --cols <num_cols> --marker_size <size>
```
This will create an Aruco board saved as `aruco_board.png`.

**2- Capture Calibration Images:** Capture calibration images using a camera or video feed:
```bash
python utils/image_capture.py --input <camera_or_video_url> --model <model_name> --win <window_size>
```
Images will be saved in the `data/<model_name>` directory.

**3- Perform Intrinsic Calibration:** Compute the intrinsic parameters using the captured images:
```bash
python utils/intrinsic_calib.py --model <model_name> --len <marker_length> --sep <marker_separation>
```
The resulting camera matrix and distortion coefficients will be saved as `calibration.yaml`.
