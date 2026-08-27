# Touch-Controlled Analog Synthesizer

A fully analog, touch-controlled synthesizer that converts touch position into audible pitch using **logarithmic signal conditioning** and **voltage-to-frequency conversion**. The system was designed and simulated in **Proteus 8**.

<img width="812" height="623" alt="image" src="https://github.com/user-attachments/assets/35b461f5-6959-45cb-aa31-4a578095ebec" />


## Overview

The synthesizer consists of five analog stages:

```text
Touch Input
    ↓
Logarithmic Amplifier
    ↓
Inverting Amplifier (×10)
    ↓
LM331 Voltage-to-Frequency Converter
    ↓
Output Buffer → Speaker
```

The logarithmic stage maps the linear touch position into a control signal better suited to the approximately logarithmic nature of human pitch perception.

## Key Components

* **TL072** — logarithmic amplifier and gain stage
* **1N4148** — logarithmic feedback element
* **LM331** — voltage-to-frequency converter
* **10 kΩ potentiometer** — resistive touch-input model
* **Unity-gain buffer** — output isolation
* **±15 V** — dual supply

The LM331 timing network uses `RT = 100 kΩ`, `RS = 10 kΩ`, `RL = 100 kΩ`, and `CT = 4.9 nF`.

## Results

| Parameter         |               Result |
| ----------------- | -------------------: |
| LM331 input range |         ~2.48–3.63 V |
| Output frequency  |         ~1.1–1.6 kHz |
| Output waveform   | Approximately square |
| Duty cycle        |                 ~50% |
| Simulation        |            Proteus 8 |

Moving the touch position across the input range produces a monotonically increasing output frequency and corresponding rise in pitch.

## Limitations

The simulation does not model several physical effects, including thermal drift, component tolerances, supply noise, touch-contact characteristics, and real speaker impedance. A physical implementation would therefore require calibration and additional output-stage conditioning.

## Future Improvements

* Extend the frequency range by modifying `CT`, `RT`, or amplifier gain.
* Add temperature compensation to reduce pitch drift.
* Add frequency calibration/offset trimming.
* Replace the op-amp output buffer with a dedicated Class-AB power stage for low-impedance speakers.

## Authors

**Parth Kadam** · **Krrish Khavnekar**
Department of Electronics & Telecommunication Engineering
Sardar Patel Institute of Technology, Mumbai, India

## Acknowledgements

Developed as an analog circuit design project at **Sardar Patel Institute of Technology (SPIT)**, with reference support from **IETE-SPIT**.
