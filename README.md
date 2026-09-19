#  LifeBlink — Smart Eyewear for Assistive Communication & Health Monitoring

> A wearable embedded-AI system that uses **EOG-based eye-movement and blink detection** as an alternative communication interface for speech-impaired individuals, while simultaneously enabling physiological monitoring through **PPG sensing**.

**Faculty-Guided Project under Dr. Vibhor Pandhare**  
**Duration:** January 2025 – February 2025

---

##  Overview

Communication is a fundamental requirement for independent living, yet individuals with speech impairments may face significant challenges when conventional speech-based interfaces are unavailable or difficult to use.

**LifeBlink** explores a wearable, non-invasive solution in which intentional eye movements and blinks are interpreted as user inputs and converted into meaningful commands.

The system combines:

-  **EOG sensing** for eye-blink and eye-movement detection
-  **PPG sensing** for physiological monitoring
-  **LSTM-based temporal classification**
-  **ESP32** for embedded processing
-  **Cloud connectivity** for data transmission and monitoring
-  A compact wearable eyewear platform

The project demonstrates an end-to-end pipeline from **physiological signal acquisition → signal processing → machine learning → embedded deployment → assistive interaction**.

---

#  Motivation

People with speech impairments may have difficulty communicating through conventional voice-based interfaces. Existing assistive communication systems can require keyboards, touch interfaces, or other physical interaction modalities that may not always be convenient.

Eye movements provide a potentially useful alternative input modality because they can be generated intentionally while requiring minimal physical movement.

This motivated the development of **LifeBlink**:

> **Can eye-related physiological signals be captured through a wearable device and converted into meaningful user commands using embedded machine learning?**

The project therefore focuses on building a compact wearable system capable of:

1. Capturing eye-related physiological signals.
2. Detecting meaningful patterns such as blinks and directional eye movements.
3. Classifying these temporal patterns using machine learning.
4. Running the resulting model on an embedded microcontroller.
5. Providing a pathway for the classified commands to be communicated externally.

In parallel, physiological sensing through PPG enables the same wearable platform to support health-monitoring functionality.

---

#  Problem Statement

The project addresses the following engineering problem:

> **Develop a compact wearable system that can acquire physiological signals, interpret intentional eye movements using machine learning, and provide an embedded interface for assistive communication and health monitoring.**

The main technical challenges are:

- Physiological signals are inherently noisy.
- Eye movements produce time-varying signals rather than simple static values.
- Different users may generate different signal patterns.
- The system must distinguish intentional eye actions from signal noise and natural variations.
- Machine-learning inference must ultimately operate within the computational constraints of an embedded device.
- The complete sensing and processing pipeline must be sufficiently compact for wearable deployment.

---

#  Proposed Solution

LifeBlink follows a multi-stage sensing and inference pipeline.

```text
              USER
                │
                │ Eye movement / blink
                ▼
        ┌─────────────────┐
        │   EOG Sensors   │
        └────────┬────────┘
                 │
                 │ Raw physiological signal
                 ▼
        ┌─────────────────┐
        │ Signal          │
        │ Acquisition     │
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │ Pre-processing  │
        │ & Conditioning  │
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │ Temporal Signal │
        │ Representation  │
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │ LSTM Classifier │
        └────────┬────────┘
                 │
                 │ Classified eye action
                 ▼
        ┌─────────────────┐
        │      ESP32      │
        │ Embedded System  │
        └────────┬────────┘
                 │
          ┌──────┴───────┐
          │              │
          ▼              ▼
     Communication   Cloud / IoT
       Interface       Platform
