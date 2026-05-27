# Deployment of Machine Learning Outputs on Embedded Platforms

**Author:** Emilie DUFLOT — VUT ID 286482  
**Institution:** Brno University of Technology (VUT)  
**Date:** May 2026

---

## Project Summary

This project investigates cross-platform TinyML deployment by training a 
single gesture recognition model and deploying it to six different 
microcontroller platforms without retraining. The central research question is:

> Does raw clock speed determine inference performance, or do processor 
> architecture and software library optimization matter more?

**Key finding:** Architecture dominates latency. A Cortex-M4F at 64 MHz 
(22 ms) outperforms a Cortex-M0+ at 133 MHz (68 ms) by 3× due to DSP 
extensions and CMSIS-NN optimization.

---

## Repository Contents

| File | Description |
|------|-------------|
| `REPORT.pdf` | Full written report |
| `edge-impulse-export/` | Exported Edge Impulse Arduino library |

---

## Platforms Tested

| Platform | Core | Clock | INT8 Latency |
|----------|------|-------|--------------|
| STM32F7 | Cortex-M7 | 216 MHz | 8 ms |
| Infineon PSoC6 | Cortex-M4F | 80 MHz | 14 ms |
| Arduino Nano 33 BLE | Cortex-M4F | 64 MHz | 22 ms |
| Nordic nRF52840 DK | Cortex-M4F | 64 MHz | 22 ms |
| Espressif ESP-EYE | ESP32 | 240 MHz | 30 ms |
| Raspberry Pi RP2040 | Cortex-M0+ | 133 MHz | 68 ms |

---

## Edge Impulse Project

Public project (dataset + model):  
https://studio.edgeimpulse.com/studio/994756

Original dataset (Continuous Motion Recognition):  
https://studio.edgeimpulse.com/public/14299/latest

---

## Tools Used

- [Edge Impulse Studio](https://edgeimpulse.com) — data collection, 
  training, quantization, deployment
- TensorFlow Lite Micro (TFLM)
- CMSIS-NN (ARM backend)
- EON Compiler
