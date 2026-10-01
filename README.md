# Automatic License Plate Detection & Recognition
A deep learning-based computer vision project exploring automatic license plate detection and recognition from images and video. The system combines a custom-trained **YOLOv4** object detection model with **PaddleOCR** for character recognition, with additional experimentation into video-based object tracking using **Deep SORT**.
<br>
<br>
This project was developed as my final-year undergraduate project in Informatics and Computer Science at **Strathmore University**.

## Overview
Automatic License Plate Recognition (ALPR), also referred to as Automatic Number Plate Recognition (ANPR), combines computer vision and optical character recognition to identify vehicles and read their license plates. The project explored a pipeline for detecting license plates in traffic imagery and extracting the characters contained within them:

### Processing Pipeline
```text
Traffic Image / Video
         |
         ▼
  YOLOV4 Detection
         |
         ▼
Detected License Plate
         |
         ▼
     Plate Crop
         |
         ▼
     PaddleOCR
         |
         ▼
Recognized Plate Text
```
The project was developed in stages, beginning with custom object detection and later integrating OCR for character recognition. Video processing and object tracking were also explored as an extension of the detection and recognition pipeline.

## Key Components
### 1. License Plate Detection
License plate images were labelled and prepared in YOLO format for custom object detection. The project used **Darknet's YOLOv4 implementation** to train a custom license plate detector. YOLOv4 was selected for its ability to perform object detection efficiently while maintaining a strong balance between speed and accuracy.
<br>
<br>
Two detection approaches were explored:
* YOLOv4
* YOLOv4-tiny

The training workflow included:
* Preparing and annotating the dataset
* Configuring Darknet
* Preparing YOLO dataset configuration files
* Using pretrained YOLOv4 convolutional weights
* Training custom object detection models
* Evaluating model performance

### 2. Model Training & Evaluation
The dataset used for the detection model consisted of:
* **1,500 training images**
* **300 validation images**
* YOLO-format annotations

The models were trained and evaluated using Darknet, with **mean Average Precision (mAP)** used as an object-detection evaluation metric.

The project also included experimentation with different training configurations and model weights to investigate detection performance.

### 3. Optical Character Recognition
After detecting a license plate, the detected region could be cropped and passed to **PaddleOCR** for character recognition. The OCR component was configured using the **CRNN** recognition algorithm and integrated into the Python inference pipeline.

This created the second stage of the system:
```text
YOLOv4
   |___ Detect license plate
                 │
                 ▼
             Crop plate
                 │
                 ▼
              PaddleOCR
                  |___ Recognize characters
```

### 4. Video Processing & Tracking
The project also explored extending the image-based pipeline to video. **Deep SORT** was investigated as an object-tracking component for maintaining identities across video frames and associating OCR results with tracked license plates. This part of the project remained experimental and was not developed into a fully reliable end-to-end tracking system.

## Project Results
The trained detection models were tested on previously unseen license plate images and traffic footage. The final project reported a **96.03% full recognition rate** on the evaluated license plate dataset. Testing also revealed recognition errors involving visually similar characters and demonstrated the limitations of applying the system to more challenging real-world conditions.

Examples of challenges included:
* Variations in lighting
* Different license plate sizes and orientations
* Complex backgrounds
* Character ambiguity during OCR
* Detection and recognition errors in video

These results highlighted the difference between achieving strong performance on a prepared dataset and building a robust system for varied real-world environments.

## System Architecture
Beyond the machine learning pipeline, the project included the design of a broader ANPR application.

The proposed system architecture incorporated:
* Image and video input
* License plate detection
* Character recognition
* User interaction
* Database storage
* Client-server communication

The project documentation also included:
* Use case diagrams
* Sequence diagrams
* Activity diagrams
* Class diagrams
* Entity-relationship diagrams
* Database schema
* System architecture diagrams
* User interface wireframes

## Technology Stack
|Technology            | Purpose                                |
|----------------------|----------------------------------------|
|**Python**            | Machine learning and inference pipeline|
|**YOLOv4**            | License plate object detection         |
|**Darknet**           | YOLO model training and inference      |
|**PaddleOCR**         | License plate character recognition    |
|**Deep SORT**         | Experimental object tracking           |
|**Jupyter Notebook**  | Development and experimentation        |
|**CUDA / cuDNN**      | GPU-accelerated model training         |

## Repository Structure
```text
|--- annotations/    # License plate annotations
|--- darknet/        # Darknet / YOLO implementation and configuration
|--- deep_sortt/     # Experimental Deep SORT tracking implementation
|--- images/         # Project images and test data
|--- notebooks/      # Model training and ANPR inference notebooks
└────readme/
```
## Development Process
The project was developed iteratively over the course of my final year of undergraduate study.

The main stages were:
1. Research into automatic license plate recognition and existing approaches.
2. Collection and annotation of license plate images.
3. Preparation of the dataset in YOLO format.
4. Configuration of the Darknet environment.
5. Training custom YOLOv4 detection models.
6. Evaluation and testing of the trained models.
7. Integration of PaddleOCR for character recognition.
8. Experimentation with processing traffic video.
9. Exploration of Deep SORT for object tracking.
10. Evaluation of the limitations of the resulting system.

## Limitations and Future Work
The project demonstrated that a combination of object detection and OCR could be used to construct an automatic license plate recognition pipeline, but several areas would require further development for a production-ready system.

Potential improvements include:
* Training with a larger and more diverse dataset.
* Improving recognition across different plate sizes, orientations, and viewing angles.
* Applying additional image transformations before OCR.
* Improving OCR handling of visually similar characters.
* Developing a more robust video-tracking pipeline.
* Evaluating the system across a wider range of real-world traffic conditions.
* Optimising the complete pipeline for real-time inference.

## What I Learned
This project provided hands-on experience with the development of a machine learning system beyond simply training an individual model. In particular, it involved working across the computer vision pipeline, from **data annotation and model training to inference, OCR integration, video processing, and system design**. It also highlighted an important practical aspect of machine learning development: individual components can perform well in isolation while the complete end-to-end system can still require substantial debugging and iteration.

## Academic Project
This project was completed as a final-year undergraduate project for the **Bachelor of Science in Informatics and Computer Science at Strathmore University**.

The accompanying research paper was titled: <br>
<p align="center">
  <b>Deep Learning Based Automatic Car Number Plate Detection and Recognition Systems for Solving Crime Investigations</b>
</p>

The project documentation discusses the research background, methodology, system design, implementation, model training, testing, results, and future work.

---
Copyright © 2026 Vicky Kimani. Last updated on September 30, 2026.







