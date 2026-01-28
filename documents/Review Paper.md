# IoT and AI-Based Crop Protection System: A Review

## Abstract
This review discusses the design, implementation, and effectiveness of AI and IoT-based crop protection systems. These systems aim to safeguard agricultural fields from wild animal intrusion using real-time detection, alerts, and deterrents. Key technologies include CNNs, YOLO object detection models, microcontrollers, sensors, and GSM-based alert mechanisms.

---

## 1. Introduction
Agricultural crops face significant threats from wild animals. Traditional protection methods often require manual monitoring or lethal deterrents. Modern solutions integrate **Artificial Intelligence (AI)** and **Internet of Things (IoT)** technologies to provide real-time, non-lethal, and cost-effective solutions for farmers.

---

## 2. System Overview
The system consists of:
- **Camera & Microcontroller**: Raspberry Pi or ESP32-CAM captures images.
- **Sensors**: PIR sensors (heat detection) and ultrasonic sensors (motion detection).
- **AI Models**: CNNs and YOLO models for real-time animal detection.
- **Alerts**: LEDs, buzzers, and GSM modules notify farmers and deter animals.

**Workflow**:
1. Continuous video stream captured.
2. Frames extracted and analyzed by AI.
3. If animal detected → alarm and GSM alert.
4. If no detection → system idle.

![Flowchart of Proposed System](figs/flowchart.png)

---

## 3. Components and System Architecture

### 3.1 Sensors
- **PIR sensor**: Detects heat radiated by animals.
- **Ultrasonic sensor**: Detects motion via sound waves.

### 3.2 Microcontrollers
- **ESP32-CAM**: Captures images/videos on motion detection.
- **Arduino**: Controls sensors, actuators, LEDs, and alarms.

### 3.3 AI Models
- **YOLOv7/v8**: Real-time object detection.
- **CNN**: Frame-based image recognition.

### 3.4 Alert Systems
- **GSM Module**: Sends SMS alerts to farmers.
- **LEDs & Buzzers**: Deter animals through sound and light.

---

## 4. Detection Procedure
1. Motion detected → triggers camera.
2. Image captured and sent to server.
3. YOLO/CNN processes image → animal detection.
4. Alerts activated via GSM, LED, and buzzer.
5. Logs detection for analysis.

---

## 5. Performance Metrics
- **Accuracy**: Correct animal vs human differentiation.
- **Precision, Recall, F1-score**: Reduce false positives/negatives.
- **Intersection over Union (IoU), Mean Average Precision (mAP)**: Evaluate object detection localization.

**Advantages**:
- Reduces crop loss.
- Real-time alerts enable proactive action.
- Non-lethal deterrents preserve biodiversity.

---

## 6. Comparative Analysis of Existing Systems
| Paper | Technology | Focus | Strengths | Limitations |
|-------|-----------|-------|-----------|-------------|
| [5] Lakshmi et al. 2020 | Arduino + PIR + GSM | Alerts & Monitoring | Cost-effective | Limited functionality |
| [11] Gajanan et al. 2024 | Arduino + Sensors + Sound Deterrent | Fast response | Quick alerts | Small coverage area |
| [17] Deepa et al. 2021 | IoT + Sound deterrent | Crop protection | Detailed monitoring | Technical expertise required |
| [23] Drimaj et al. 2023 | UAS + Crop height/yield | Damage assessment | Quantitative | Not preventive |
| [29] Sundaram & Meena 2023 | Video & irradiance images | Observation | Theoretical depth | Limited practical repellence |

---

## 7. Challenges & Limitations
1. Sensor sensitivity & range limitations.
2. Network/GSM connectivity dependency.
3. High power consumption for continuous operation.
4. AI overfitting/underfitting risks.
5. False positives/negatives reduce efficiency.
6. Large field coverage requires more devices → higher cost.
7. Hardware durability under extreme conditions.
8. Environmental impact (lights, alarms).
9. Dependence on cloud/internet for alerts.

---

## 8. Results
- Detects animals up to 10 feet, alerts in ~10 seconds.
- Buzzers & LEDs deter animals within ~6 meters.
- Solar power integration reduces dependency on external electricity.
- Farmers report reduced crop losses.
- Preserves biodiversity using non-lethal deterrents.

---

## 9. Conclusion
The proposed system provides a **practical, cost-effective, and user-friendly solution** for crop protection:
- Combines AI and IoT for real-time monitoring.
- Reduces crop damage while preserving wildlife.
- Can be adapted to various farming environments.
- Supports remote monitoring and prompt action via GSM alerts.

---

## 10. References
1. Reddy, K. V., et al., *Edge AI in Sustainable Farming*, IEEE Access, 2024.  
2. Aranganathan, A., et al., *Smart Agricultural Security System*, ICSES, 2023.  
3. Li, G., et al., *CNN-based Computer Vision in Animal Farming*, Sensors, 2021.  
4. Baral, K., et al., *Human-Wildlife Conflict*, Sustainability, 2021.  
5. Lakshmi, K. M., et al., *Security for Crops using GSM*, 2020.  
6. Thirrunavukkarasu, R. R., et al., *Smart Irrigation and Crop Protection Using Arduino*, ICACCS, 2021.  


