# Real-Time Object Detection with YOLOv8 and Video Streaming
<p align="center">
<img width="800" alt="library demo" src="https://github.com/user-attachments/assets/44bb0021-983a-4e7a-82d2-acc6acae964a" />
</p>

# Ona Vision 
<p align="center">
<img width="500" height="395" alt="logo" src="https://github.com/user-attachments/assets/ad7173d1-7dee-471d-8a2e-cc707cf3306c" />
</p>

## Our Mission  
At **Ona Vision**, we strive to revolutionize real-time computer vision by making cutting-edge AI-powered detection and monitoring systems accessible, scalable, and efficient.  

## Our Vision  
To empower individuals, businesses, and communities with **state-of-the-art** object detection and recognition solutions that enhance safety, automation, and decision-making.  

## Core Values  
- **Innovation** – Pushing the boundaries of AI and real-time processing.  
- **Efficiency** – Optimizing performance for seamless, real-world applications.  
- **Accessibility** – Bringing advanced vision technology to everyone, everywhere.  
- **Reliability** – Ensuring accuracy and dependability in mission-critical scenarios.  

## What We Do  
Ona Vision integrates **YOLO-based object detection**, real-time **video streaming**, and **observability features** to provide insights that drive smarter, safer environments. Whether for security surveillance, industrial monitoring, or smart city applications, our solutions are built for high performance and scalability.  


## Overview
This project implements **real-time object detection** using **YOLOv8** and streams the processed video over a network. The server captures video from a webcam, performs object detection, and sends the processed frames to a client for display. Additionally, it integrates **observability features** using Prometheus to monitor system performance and model inference metrics.

## Features
- Uses **YOLOv8** for state-of-the-art object detection
- **Real-time video processing** with OpenCV
- **Network streaming** using Python sockets
- **Bounding box rendering** with object labels
- **Observability integration** with Prometheus for:
  - FPS (Frames Per Second)
  - Inference time
  - CPU and memory usage
  - Detection confidence and per-class object count

## Multi-Object Tracking (MOT) with DeepSORT

### What is DeepSORT?
DeepSORT (Deep Simple Online and Realtime Tracker) is an advanced object tracking algorithm that extends the original SORT tracker by adding deep learning-based appearance descriptors. This helps improve object re-identification across frames, making tracking more reliable in crowded or fast-moving scenes.

### Why Use DeepSORT?
- **Tracks multiple objects across frames** with consistent IDs.
- **Handles occlusions** (when objects overlap or disappear temporarily).
- **Re-identifies objects** even if they leave and re-enter the scene.
- **More accurate tracking** compared to basic object detection.

### How It Works in Ona Vision
1. **YOLOv8 detects objects** in each frame.
2. **DeepSORT assigns unique IDs** to detected objects.
3. **Tracks objects over time**, even if they move, overlap, or briefly disappear.
4. **Outputs tracking results** with bounding boxes and IDs.

### Performance Impact
- Adds a **small processing overhead** (~5-10% FPS drop).
- More stable tracking compared to detection-only mode.
- Ideal for **surveillance, traffic monitoring, and sports analytics**.

## Technologies Used
- Python
- OpenCV
- PyTorch
- Ultralytics YOLOv8
- Socket Programming
- **Prometheus** for monitoring

## Setup Instructions

Install Libraries from requirements.txt
```bash
pip install -r requirements.txt
```

Run the project
```bash
python download_model.py
```

Start the server which processes frames from webcam or other source
```bash
python main.py
```

Display real-time video
```bash
python client.py
```

Metrics will be available at `http://localhost:8000/metrics`.

## How It Works
1. The **server** captures frames from the webcam and runs YOLOv8 for object detection.
2. Bounding boxes and labels are added to the frame.
3. The processed frame is serialized and sent to the **client** over a socket connection.
4. The **client** receives and displays the video in real-time.
5. **Prometheus metrics** are collected in the background, tracking performance and inference statistics.

## Observability Metrics
| Metric | Description |
|--------|-------------|
| **FPS** | Frames per second for performance monitoring |
| **Inference Time** | Time taken for YOLOv8 inference per frame |
| **CPU Usage** | System CPU utilization during processing |
| **Memory Usage** | System memory consumption during processing |
| **Detection Confidence** | Average confidence of detected objects per frame |
| **Class-wise Object Count** | Tracks the number of detected objects per class |

## Demo
https://github.com/user-attachments/assets/8246bf73-b810-48b7-9b8b-a855f730fb1f

## Potential Improvements
- **Multi-object tracking** using DeepSORT
- **Edge deployment** on a Raspberry Pi or Jetson Nano
- **Cloud integration** to store detection data
- **Web-based visualization** using Flask or FastAPI

## License
This project is open-source under the MIT License.

## Author
**Josiah Mbao**
🔗 [GitHub](https://github.com/josiah-mbao)  |  ✉️ josiahmbaomc@gmail.com

