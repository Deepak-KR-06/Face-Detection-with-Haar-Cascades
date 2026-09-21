# Exp 12 - Face Detection using Haar Cascades with OpenCV and Matplotlib

## Name : Deepak K R
## Reg no : 212225040057
## Date : 03/09/2026

## Aim

To write a Python program using OpenCV to perform the following image manipulations:  
i) Extract ROI from an image.  
ii) Perform face detection using Haar Cascades in static images.  
iii) Perform eye detection in images.  
iv) Perform face detection with label in real-time video from webcam.

## Software Required

- Anaconda - Python 3.7 or above  
- OpenCV library (`opencv-python`)  
- Matplotlib library (`matplotlib`)  
- Jupyter Notebook or any Python IDE (e.g., VS Code, PyCharm)

## Algorithm

### I) Load and Display Images

- Step 1: Import necessary packages: `numpy`, `cv2`, `matplotlib.pyplot`  
- Step 2: Load grayscale images using `cv2.imread()` with flag `0`  
- Step 3: Display images using `plt.imshow()` with `cmap='gray'`

### II) Load Haar Cascade Classifiers

- Step 1: Load face and eye cascade XML files 
### III) Perform Face Detection in Images

- Step 1: Define a function `detect_face()` that copies the input image  
- Step 2: Use `face_cascade.detectMultiScale()` to detect faces  
- Step 3: Draw white rectangles around detected faces with thickness 10  
- Step 4: Return the processed image with rectangles  

### IV) Perform Eye Detection in Images

- Step 1: Define a function `detect_eyes()` that copies the input image  
- Step 2: Use `eye_cascade.detectMultiScale()` to detect eyes  
- Step 3: Draw white rectangles around detected eyes with thickness 10  
- Step 4: Return the processed image with rectangles  

### V) Display Detection Results on Images

- Step 1: Call `detect_face()` or `detect_eyes()` on loaded images  
- Step 2: Use `plt.imshow()` with `cmap='gray'` to display images with detected regions highlighted  

### VI) Perform Face Detection on Real-Time Webcam Video

- Step 1: Capture video from webcam using `cv2.VideoCapture(0)`  
- Step 2: Loop to continuously read frames from webcam  
- Step 3: Apply `detect_face()` function on each frame  
- Step 4: Display the video frame with rectangles around detected faces  
- Step 5: Exit loop and close windows when ESC key (key code 27) is pressed  
- Step 6: Release video capture and destroy all OpenCV windows  

## PROGRAM :
```py

import cv2

# Load Haar cascade
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')

# Read the image
image = cv2.imread('sabii.jpg')

# Check if image was loaded
if image is None:
    print("Error: Image not found.")
else:
    # Convert to grayscale
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    # Detect faces
    faces = face_cascade.detectMultiScale(gray, scaleFactor=1.1, minNeighbors=5)

    # Draw rectangles
    for (x, y, w, h) in faces:
        cv2.rectangle(image, (x, y), (x + w, y + h), (255, 0, 0), 2)

    # Get screen resolution
    screen_res = 1920, 1080  # You can change this based on your screen
    scale_width = screen_res[0] / image.shape[1]
    scale_height = screen_res[1] / image.shape[0]
    scale = min(scale_width, scale_height)

    window_width = int(image.shape[1] * scale)
    window_height = int(image.shape[0] * scale)

    # Resize image
    resized_image = cv2.resize(image, (window_width, window_height))

    # Show image
    cv2.imshow('Detected Faces', resized_image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
```
## OUTPUT:

<img width="442" height="483" alt="image" src="https://github.com/user-attachments/assets/1189bd4c-e08e-4076-9e8a-6328a82d85bd" />

<img width="352" height="456" alt="image" src="https://github.com/user-attachments/assets/ec569245-7b7b-46a6-ad24-951340741f04" />

<img width="618" height="326" alt="image" src="https://github.com/user-attachments/assets/c3b3c86c-0ef1-4b5b-b35a-b5eccc4f7902" />

<img width="652" height="337" alt="image" src="https://github.com/user-attachments/assets/d4c79a04-ac73-4d78-8b66-cdbfc1f9e800" />

<img width="632" height="327" alt="image" src="https://github.com/user-attachments/assets/18edf150-9942-4ed4-b461-3f20338b899e" />

<img width="452" height="475" alt="image" src="https://github.com/user-attachments/assets/c5e4b2bc-9ef9-4d95-bcea-6291e2e46b4c" />






## RESULT:
thus the given objective of face detection is done sucessfully.
