# 🚀 YOLO Object Detection Project

## 📌 Overview

This project demonstrates **Object Detection using YOLO (You Only Look Once)**.
The model detects objects in an image and displays them with bounding boxes and labels.

---

## 🎯 Features

* ✅ Detect objects in images
* ✅ Draw bounding boxes with labels
* ✅ Handles **No Detection Case**
* ✅ Beginner-friendly implementation
* ✅ Runs on Google Colab / VS Code

---

## 🛠️ Technologies Used

* Python
* OpenCV
* Matplotlib
* YOLOv8 (Ultralytics)

---

## ⚙️ Installation

### Step 1: Install Libraries

```bash
pip install ultralytics opencv-python matplotlib
```

---

## 📂 How to Run

### Step 1: Upload Image

If using Google Colab:

```python
from google.colab import files
uploaded = files.upload()
```

---

### Step 2: Run Code

```python
from ultralytics import YOLO
import cv2
import matplotlib.pyplot as plt

model = YOLO("yolov8n.pt")

image_path = list(uploaded.keys())[0]
image = cv2.imread(image_path)

results = model.predict(source=image, conf=0.25)

for r in results:
    if r.boxes is not None:
        for box in r.boxes:
            x1, y1, x2, y2 = map(int, box.xyxy[0])
            cls = int(box.cls[0])
            label = model.names[cls]

            cv2.rectangle(image, (x1,y1),(x2,y2),(0,255,0),2)
            cv2.putText(image, label, (x1,y1-10),
                        cv2.FONT_HERSHEY_SIMPLEX, 0.6, (0,255,0),2)

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.imshow(image_rgb)
plt.axis('off')
plt.show()
```

---

## 🧪 Output

### ✅ Case 1: Object Detected

* Displays bounding boxes
* Shows object labels

### ❌ Case 2: No Object Detected

* Displays image without boxes
* Prints: `No objects detected`

---

## 🧠 Concept Used

YOLO (You Only Look Once) is a deep learning model used for **real-time object detection**.
It processes the image in a single pass and detects multiple objects efficiently.

---

## 💡 Future Improvements

* Add video detection 🎥
* Add real-time webcam detection 📷
* Add object counting 📊
* Add GUI interface

---

## 🙌 Acknowledgment

This project uses the **Ultralytics YOLOv8** model for object detection.

---

## 📌 Author

**Nandini Tarak  
intern id CITS2593

## ⭐ If you like this project

Give it a ⭐ on GitHub!
