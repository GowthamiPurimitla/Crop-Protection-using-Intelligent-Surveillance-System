# Crop Protection using Intelligent Surveillance System
AI + IoT based Animal Detection & Crop Protection using ESP32-CAM, PIR, CNN, GSM.

## Abstract
This project aims to prevent crop damage caused by wildlife using an intelligent, automated surveillance system. The solution integrates IoT sensors, AI-based image classification, PIR motion detection, GSM communication, and ultrasonic deterrents.

**Key Features:**
- PIR sensor detects movement
- ESP32-CAM captures real-time images
- Haar Cascade identifies human vs animal
- CNN classifies domestic vs wild animals
- GSM module sends alerts to the farmer
- Sound-based deterrents scare animals without harming them
- 24×7 monitoring with cloud storage for large data

This system is cost-effective, non-invasive, and suitable for small to large agricultural plots.

## Introduction
Agriculture faces continuous threats from wildlife intrusion. Traditional scare methods fail to protect crops 24×7. This project provides:
- Real-time automated monitoring
- AI-based intrusion classification
- Immediate response and alert notifications
- Non-harmful animal repelling

Using AI + IoT, the system identifies the threat type and notifies the farmer instantly.

## Literature Survey
- YOLOv3 & YOLOv5 for animal detection
- Edge AI, TinyML for real-time inference
- IoT-based crop protection systems
- Image processing using Haar cascades
- PIR, ultrasonic sensors for motion detection
- Drone-assisted farm surveillance
- GSM-based alert systems

The survey shows the need for a low-cost, real-time, species-aware crop protection system, which this project addresses.

## Materials and Methods

### Hardware Components
- ESP32-CAM Module – Real-time image capture
- Raspberry Pi (optional) – For advanced processing
- PIR Sensor – Motion detection
- Ultrasonic Sensor – Animal repelling
- GSM Module – SMS notification
- ISD1820 Sound Module – Audio deterrents
- Breadboard, jumper wires, power modules

### Software & Algorithms
- CNN (Convolutional Neural Network) for animal classification
- Haar Cascade for human vs non-human detection
- Python, OpenCV for computer vision
- IoT communication via GSM
- Cloud storage for image logs

## System Architecture
**Workflow:**
1. PIR sensor detects movement
2. ESP32-CAM captures images
3. Haar Cascade Classifier → Human or animal
4. If animal → CNN classifies Domestic / Wild
5. GSM module sends SMS alerts
6. Sound deterrent activated
7. Data stored locally or in the cloud

## Results & Discussion
- Motion detection using PIR sensor works reliably.
- ESP32-CAM captures clear images for classification.
- Haar Cascade differentiates humans vs animals accurately.
- CNN provides accurate classification between domestic and wild animals.
- Alerts sent instantly via GSM:
  - "HUMAN ENTERED THE FIELD"
  - "DOMESTIC ANIMAL DETECTED"
  - "WILD ANIMAL DETECTED"
- Sound deterrents effectively scare animals away.

Overall, the system proved efficient, accurate, and lightweight for rural deployment.

## Conclusion
This project successfully implements a non-harmful, automated, AI-powered crop protection system using IoT and computer vision. It addresses key issues in existing methods:
- Lack of real-time monitoring
- Inability to classify species
- High manual effort
- Harmful deterrent mechanisms

The system provides a scalable, cost-effective solution suitable for farmers in developing regions.

## Future Scope
- Integration with solar panels for remote areas
- Drone-based patrol & monitoring
- Thermal cameras for night detection
- Edge AI hardware for faster processing
- Smartphone app with live monitoring
- ML model improvement with larger datasets
- Automatic water-sprinkler deterrent mechanism

## References
- Deep learning and computer vision research papers
- IoT-based animal detection systems
- Kaggle datasets and other online resources

[Download Full PDF Report](PROJECT REPORRT.pdf)

