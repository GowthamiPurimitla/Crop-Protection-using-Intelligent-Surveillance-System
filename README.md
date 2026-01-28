# Crop-Protection-using-Intelligent-Surveillance-System
AI + IoT based Animal Detection &amp; Crop Protection using ESP32-CAM, PIR, CNN, GSM.

## Project Overview
Crop damage caused by wild animals—such as pigs, elephants, deer, and other wildlife—is a major threat faced by farmers. Traditional methods like scarecrows, manual guards, and electric fences are outdated, inefficient, or harmful.

This project presents a non-harmful, AI-driven, IoT-based intelligent surveillance system that:

* Detects animal movement
* Identifies humans vs animals
* Classifies domestic vs wild animals
* Sends real-time alerts to farmers through GSM
* Repels animals using ultrasonic sound and audio deterrents

The system uses ESP32-CAM, PIR sensors, GSM module, ultrasonic components, CNN, and Haar Cascade classification for a fully automated crop protection solution.

 ## Abstract
This project aims to prevent crop damage caused by wildlife using an intelligent, automated surveillance system. The solution integrates IoT sensors, AI-based image classification, PIR motion detection, GSM communication, and ultrasonic deterrents.

Key features:
* PIR Sensor detects movement
* ESP32-CAM captures real-time images
* Haar Cascade identifies whether the intruder is human or animal
* CNN Model classifies domestic vs wild animals
* GSM Module sends alerts to the farmer
* Sound-based deterrents scare animals without harming them
* 24×7 monitoring with cloud storage for large data

This system is cost-effective, non-invasive, and suitable for small to large agricultural plots.

## 1. Introduction
Agriculture faces continuous threats from wildlife intrusion. Manual guarding and traditional scare methods fail to protect crops 24×7.

This project provides:

* Real-time automated monitoring
* AI-based intrusion classification
* Immediate response and alert notifications
* Non-harmful animal repelling

Using AI + IoT, the system identifies the threat type and notifies the farmer instantly.

## 2. Literature Survey
* YOLOv3 & YOLOv5 for animal detection
* Edge AI and TinyML for real-time inference
* IoT-based crop protection systems
* Image processing using Haar cascades
* PIR and ultrasonic sensors for motion detection
* Drone-assisted farm surveillance
* GSM-based alert systems

The survey shows the need for a low-cost, real-time, species-aware crop protection system, which this project addresses.

 ## 3. Materials and Methods
 Hardware Components
* ESP32-CAM Module – Real-time image capture
* Raspberry Pi (optional) – For advanced processing
* PIR Sensor – Motion detection
* Ultrasonic Sensor – Animal repelling
* GSM Module – SMS notification
* ISD1820 Sound Module – Audio deterrents
* Breadboard, jumper wires, power modules

Software & Algorithms
* CNN (Convolutional Neural Network) for animal classification
* Haar Cascade for human vs non-human detection
* Python, OpenCV for computer vision
* IoT communication via GSM
* Cloud storage for image logs

## 4. System Architecture
Workflow:
1. PIR sensor detects movement
2. ESP32-CAM captures images
3. Haar Cascade Classifier → Human or animal
4. If animal → CNN classifies Domestic / Wild
5. GSM module sends SMS
6. Sound deterrent activated
7. Data stored (local/cloud)

## 5. Results & Discussion
* The system successfully detected motion using PIR.
* ESP32-CAM captured clear images for classification.
* Haar Cascade accurately differentiated humans vs animals.
* CNN provided accurate domestic vs wild animal classification.
* Alerts were sent instantly via GSM, including:
  * “HUMAN ENTERED THE FIELD”
  * “DOMESTIC ANIMAL DETECTED”
  * “WILD ANIMAL DETECTED”
* Sound deterrents effectively scared animals away.

Overall, the system proved efficient, accurate, and lightweight for rural deployment.

## 6. Conclusion
This project successfully implements a non-harmful, automated, AI-powered crop protection system using IoT and computer vision. It addresses issues in traditional methods such as:
* Lack of real-time monitoring
* Inability to classify species
* High manual effort
* Harmful deterrent mechanisms

The system offers a scalable, cost-effective solution suitable for farmers in developing regions.

## 7. Future Scope
* Integration with solar panels for remote areas
* Drone-based patrol and monitoring
* Thermal cameras for night detection
* Edge AI hardware for faster processing
* Smartphone app with live monitoring
* Improved ML models with larger datasets
* Automatic water-sprinkler deterrent mechanism
