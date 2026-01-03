# EEG Signal Processing and Music Analysis

## Overview
This repository contains a MATLAB-based project that implements a complete **EEG signal processing pipeline** to analyze how **different music styles influence brain activity**. The project demonstrates standard techniques used in biomedical signal processing, including filtering, frequency-band analysis, spectral analysis, and wavelet decomposition.

The main objective is to transform **raw EEG recordings** into **interpretable frequency-based features** and compare brain responses across different music conditions.

---

## Dataset
- **Format:** EDF (European Data Format)
- **File name:** Proband1.EDF
- **Type:** Multichannel EEG recording
- **Sampling frequency:** ~200 Hz (determined from EDF header)
- **Channels analyzed:** O1 and O2 (occipital cortex)

⚠️ **Important:**  
The original EEG data file (`.EDF`) is **not included** in this repository due to file size and data-handling restrictions. The dataset was provided externally for academic use and must be placed locally to run the analysis.

---

## Project Objectives
The goals of this project are to:
1. Load and inspect real EEG data
2. Determine the correct sampling frequency
3. Remove low-frequency baseline drift
4. Segment EEG data based on music styles
5. Analyze standard EEG frequency bands
6. Compare brain activity across music conditions and channels
7. Quantify results using band power and indices
8. Visualize EEG bands using wavelet decomposition

---

## Processing Pipeline (Tasks 1–8)

### Task 1 – Read EEG Data
EEG data is loaded using MATLAB’s `edfread` function. Channel names and metadata are inspected to verify correct data import.

---

### Task 2 – Sampling Frequency Determination
The sampling frequency is extracted from the EDF header information, as timetable row times represent record timing rather than individual EEG samples.

---

### Task 3 – High-Pass Filter Design
A **4th-order IIR Butterworth high-pass filter** with a cutoff frequency of **0.5 Hz** is designed to remove slow baseline drift and low-frequency artifacts. An IIR filter is chosen for its efficiency at low cutoff frequencies.

---

### Task 4 – Music Segmentation
The continuous EEG recording is segmented into time intervals corresponding to different music styles:
- Pre-recording
- Metal
- Classical music
- Relaxing music
- Favourite song
- Post-recording

---

### Task 5 – EEG Frequency Bands
Standard EEG frequency bands are defined:
- Delta: 0.5–4 Hz
- Theta: 4–8 Hz
- Alpha: 8–13 Hz
- Beta: 13–30 Hz
- Gamma: 30–45 Hz

---

### Task 6 – Analysis by Song and Channel
For each music segment and EEG channel (O1 and O2):
- The signal is filtered
- Band power is computed
- Relative band power is calculated
- The **Power Ratio Index (PRI)** is derived:

PRI = (Delta + Theta) / (Alpha + Beta + Gamma)

---

### Task 7 – Results Export
All computed features are stored in a MATLAB table and exported as an Excel (`.xlsx`) file using `table`, `writetable`, and `winopen`.

---

### Task 8 – Wavelet Decomposition
Discrete Wavelet Transform (DWT) is used to decompose EEG signals into individual frequency bands. Wavelet analysis preserves both time and frequency information and is well suited for non-stationary EEG signals.

---

## Interpretation of Results
- Low-frequency EEG bands dominate signal amplitude, which is normal physiological behavior.
- Alpha activity is prominent in occipital channels during relaxed music listening.
- Beta and Gamma bands have lower amplitude but reflect cognitive engagement.
- Music styles influence EEG rhythms in a measurable and comparable manner.

---

## Tools and Requirements
- MATLAB
- Signal Processing Toolbox
- Wavelet Toolbox

---

## Disclaimer
This project is intended **for educational purposes only** and does not provide medical or clinical diagnosis.

---

## Author
**Samson Agbadi**  
EEG Signal Processing & Biomedical Engineering Project

---

## How to Run
1. Place the EEG data file (`Proband1.EDF`) in the project directory (local only).
2. Open MATLAB.
3. Run the main script or live script (`Lab_EEG_basics.mlx`).
4. Generated figures and result tables will be saved automatically.
