# 🚦 Real-Time Road Sign Detection using YOLO (Custom Trained)

## Project Summary
This project builds a **custom YOLO-based object detection model** to detect key road objects such as:
- **Traffic Lights** (Red Light, Green Light)
- **Stop Sign**
- **Speed Limit Signs** (10–120)

The goal was to train a model that performs well on unseen road images and can run on video streams for **real-time driver assistance / autonomous driving perception** use cases.

---

## What I Did (Workflow)
- Trained a YOLO object detection model for **60 epochs** on a labeled road-sign dataset
- Evaluated model performance on **Train / Validation / Test** splits using:
  - Precision
  - Recall
  - mAP@50
  - mAP@50–95
- Performed real-time testing on an **MP4 video stream (~15–20 seconds)** and measured FPS for deployment readiness

---

## Final Results (Accuracy Metrics)

### Train Set
- Precision: **0.963**
- Recall: **0.965**
- mAP@50: **0.981**
- mAP@50–95: **0.884**

### Validation Set
- Precision: **0.950**
- Recall: **0.944**
- mAP@50: **0.964**
- mAP@50–95: **0.854**

### Test Set (Final Unseen Performance)
- Precision: **0.926**
- Recall: **0.906**
- mAP@50: **0.943**
- mAP@50–95: **0.827**

---

## Real-Time Video Performance (Speed Metrics)
The trained model was tested on an MP4 video stream using an **NVIDIA Tesla T4 GPU**.

- **Overall FPS (end-to-end throughput): 30.36 FPS**
- **Inference-only FPS: 61.46 FPS**
- Average inference time: **16.27 ms/frame**

> Note: Overall FPS is the true real-time performance because it includes video decoding + full pipeline overhead.  
> Inference-only FPS shows the model’s raw speed excluding video I/O overhead.

---

## Conclusion
The YOLO model achieved strong accuracy on unseen test data with **mAP@50 = 0.943** and **mAP@50–95 = 0.827**, showing reliable detection performance across multiple road sign classes. Real-time benchmarking on a video stream demonstrated practical deployment capability with **~30.36 FPS end-to-end throughput** on a Tesla T4 GPU. Overall, this project confirms that the trained model is both accurate and efficient for real-time road sign detection applications.

---

## Future Improvements
- Improve detection for difficult classes like traffic lights (small objects, glare, low-light conditions)
- Add object tracking (ByteTrack / DeepSORT) for smoother predictions in video
- Optimize speed using FP16 / ONNX / TensorRT for higher real-time FPS
- Test on multiple real-world driving videos at different resolutions (720p/1080p) and lighting conditions
- Deploy as a real-time application using Flask/FastAPI with live webcam/video input
