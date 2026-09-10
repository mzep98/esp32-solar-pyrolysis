# Concentrated Solar Pyrolysis & ML Auger Control System

![Competition](https://img.shields.io/badge/JA%20WE%20Challenge-2026%20National%20Submission-red)
![Hardware](https://img.shields.io/badge/Hardware-ESP32%20|%20MAX6675%20|%20NEMA17-blue)
![ML](https://img.shields.io/badge/ML-Time--Series%20Regression-orange)
![UI](https://img.shields.io/badge/UI-Android%20Figma%20Prototype-green)
![License](https://img.shields.io/badge/License-MIT-lightgray)

> **JA WE Challenge Philippines 2026 Submission**  
> *Concentrated Solar Pyrolysis and Syngas Reforming Engine with Machine Learning Auger Control for Bicol Coconut Husk and Coir Dust Residues*

---

## 📌 Executive Summary
This repository houses the technical architecture, machine learning control logic, mechanical CAD models, and companion mobile application designs for an automated solar-thermal waste-to-energy unit. By combining concentrated solar-thermal collectors with an ESP32 edge microcontroller and a time-series regression model running on a companion Android app, the system dynamically regulates biomass auger feed rates to maintain the pyrolysis reactor within its optimal thermal band ($300^\circ\text{C}$–$700^\circ\text{C}$) under variable solar irradiance.

---

## ⚙️ System Architecture & Process Flow

```text
[ Raw Coconut Husk / Coir Dust ]
               │
               ▼
┌──────────────────────────────┐       ┌──────────────────────────────┐
│  Capacitive Moisture Sensor  │───────►│    ESP32 Microcontroller     │
└──────────────────────────────┘       │  (Telemetry & Pulse Driver)  │
                                       └──────────────┬───────────────┘
                                                      │
[ Solar Collector / Thermal ]                         │ BLE / Wi-Fi Streaming
               │                                      ▼
               ▼                       ┌──────────────────────────────┐
┌──────────────────────────────┐       │   Android Companion App      │
│ Stainless Steel Reactor Tube │       │   (Runs Time-Series ML Model)│
│       (300°C – 700°C)        │       └──────────────┬───────────────┘
└──────────────┬───────────────┘                      │
               │                                      │ (Target RPM Command)
               ▼                                      ▼
┌──────────────────────────────┐       ┌──────────────────────────────┐
│ K-Type Thermocouple +        │───────►│ NEMA 17 Stepper & Auger Feed │
│ MAX6675 Cold-Junction Module │       │  (Adjusts Biomass Volume)    │
└──────────────────────────────┘       └──────────────────────────────┘
               │
               ▼
[ Clean Syngas / Biochar Output ]
