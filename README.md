# Screw Measurement & Quality Inspection using OpenCV

A classical computer vision-based system that automatically measures and inspects industrial screws for dimensional accuracy using Python, OpenCV, and Tkinter — without any machine learning or deep learning.

---

## 🚀 Features

- Detects screws in images from a camera or smartphone
- Calculates **total length** and **width** in millimeters
- Quality control classification:
  - ✅ ACCEPTED if dimensions within tolerance
  - ❌ REJECTED otherwise
- Supports 3 screw types:
  - M6×25
  - M8×10
  - M8×16
- Full folder batch inspection
- Annotated results saved automatically
- CSV file generated with all measurements
- Lightweight UI for simple user interaction

---

## 📂 Project Structure

Screw_measurement_CV/
│
├── data_baba/ # Input screw images
├── results/ # Output annotated images & bounding boxes
├── screw_QC_UI.py # Main script + Graphical User Interface
├── measurements.csv # Generated results summary (after execution)
└── README.md # Documentation (You are here)


---

## 🧠 How It Works

1️⃣ Load screw images from folder  
2️⃣ Remove ruler region (fixed location → cropped out)  
3️⃣ Convert to grayscale + apply Gaussian blur  
4️⃣ Use Canny edge detection to extract screw shape  
5️⃣ Find largest contour and compute rotated bounding box  
6️⃣ Determine:
- Longest edge → **Screw Length**
- Shortest edge → **Width (diameter)**  
7️⃣ Convert pixels → millimeters using a calibrated scale  
8️⃣ Compare with expected screw size → QC decision  
9️⃣ Save processed result images + numeric measurements

---

## ✅ QC Logic (Accept / Reject)

```python
if abs(measured_value - expected_value) <= tolerance:
    status = "ACCEPTED"
else:
    status = "REJECTED"
