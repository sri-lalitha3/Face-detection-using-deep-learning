# Face Detection System using Deep Learning

A real-time face detection system built in Python using OpenCV and Haar Cascade classification. Supports two modes — **live webcam detection** via Google Colab browser integration and **image-based detection**. Implemented entirely in Google Colab as a hands-on computer vision project.

---

## What This Project Does

This project has two working modes:

### Mode 1 — Image-Based Face Detection
- Loads an image file into the notebook
- Converts the image to grayscale for processing
- Applies OpenCV Haar Cascade Classifier (`haarcascade_frontalface_default.xml`) using `detectMultiScale`
- Draws green bounding boxes around every detected face
- Displays the output image using Matplotlib

### Mode 2 — Live Webcam Face Detection
- Uses JavaScript (`navigator.mediaDevices.getUserMedia`) to access the laptop webcam directly through the browser in Google Colab
- Displays a **Capture button** in the Colab interface
- When clicked, captures a photo from the live webcam feed
- Converts the captured base64 image data into an OpenCV format
- Applies Haar Cascade face detection on the captured frame
- Draws blue bounding boxes around all detected faces
- Saves and displays the final output image

---

## Technologies Used

| Technology | How It Was Used |
|---|---|
| Python | Core programming language |
| OpenCV (cv2) | Image reading, grayscale conversion, Haar Cascade detection, rectangle drawing |
| Haar Cascade Classifier | `haarcascade_frontalface_default.xml` for face region detection |
| NumPy | Image array manipulation and base64 decoding |
| Matplotlib | Displaying output images in the notebook |
| JavaScript | `navigator.mediaDevices.getUserMedia` for live webcam capture in Colab |
| Google Colab | Development, execution environment, webcam integration |
| Jupyter Notebook | Interactive code and output display |

---

## How to Run

### Run in Google Colab (Recommended)

1. Open the notebook using the Colab link below
2. Click **Runtime → Run All**
3. **For image detection** — the notebook will load and process the image automatically
4. **For webcam detection** — a Capture button will appear; click it, allow camera access when your browser prompts, and the photo will be taken and processed

**Open in Google Colab:**
[Face Detection Notebook](https://colab.research.google.com/drive/1ANyyeltkVs6O7rbVOXGixZtFcSYo1mtL?usp=sharing)

### Run Locally

```bash
git clone https://github.com/sri-lalitha3/Face-detection-using-deep-learning.git
cd Face-detection-using-deep-learning
pip install -r requirements.txt
jupyter notebook Face_Detection_using_Deep_Learning.ipynb
```

> Note: Live webcam mode works best in Google Colab. Running locally requires a separate webcam setup.

---

## Project Structure

```
Face-detection-using-deep-learning/
├── Face_Detection_using_Deep_Learning.ipynb   # Main notebook with both detection modes
├── requirements.txt                            # Dependencies
└── README.md                                   # Project documentation
```

---

## How the Webcam Integration Works

Google Colab does not support `cv2.VideoCapture(0)` directly. Instead, this project uses a JavaScript-based approach:

1. A `Javascript` object is injected into the Colab output using `IPython.display`
2. The script uses `navigator.mediaDevices.getUserMedia({video: true})` to access the webcam via the browser
3. A canvas element captures the current frame when the user clicks Capture
4. The frame is returned as a base64-encoded JPEG string using `canvas.toDataURL`
5. Python decodes the base64 string using `b64decode` and converts it to a NumPy array
6. OpenCV decodes the array into a BGR image for face detection processing

---

## Key Learnings

- Learned how to use OpenCV Haar Cascade Classifier for face detection in images
- Understood grayscale conversion and why it is needed before detection
- Implemented browser-based webcam capture in Google Colab using JavaScript integration
- Practised base64 image encoding/decoding between JavaScript and Python
- Built a complete computer vision pipeline from image input to annotated output

---

## Future Improvements

- Add emotion detection on top of face detection
- Extend to detect multiple faces and label each one
- Build a simple Streamlit interface for easier use without Colab
- Improve with a deep learning based detector like MTCNN for higher accuracy

---

