# EEG Signal Processing and Music Stimulus Analysis

## Overview
This project implements a complete EEG signal processing pipeline to analyze how different music styles influence brain activity. The work was carried out as part of my MSc training in Biomedical Engineering to gain hands-on experience in EEG preprocessing, frequency-domain analysis, and time–frequency methods.

The objective is to transform raw EEG recordings into interpretable frequency-based features and compare brain responses across different music conditions using standard biomedical signal processing techniques.

---

## Dataset
- **Format:** EDF (European Data Format)  
- **File name:** Proband1.EDF  
- **Type:** Multichannel EEG recording  
- **Sampling frequency:** ~200 Hz (determined from EDF header)  
- **Channels analyzed:** O1 and O2 (occipital cortex)  

⚠️ **Note:**  
The original EEG data file (`.EDF`) is not included in this repository due to data-handling and size constraints. The dataset was provided for academic use and must be placed locally to reproduce the analysis.

---

## Project Objectives
- Load and inspect real EEG recordings  
- Determine the correct sampling frequency from metadata  
- Remove baseline drift using digital filtering  
- Segment EEG data according to different music styles  
- Analyze standard EEG frequency bands  
- Compare brain activity across music conditions and channels  
- Quantify results using band power and spectral indices  
- Visualize EEG components using wavelet decomposition  

---

## Signal Processing Pipeline

### Data Import and Inspection
EEG data is loaded using MATLAB’s `edfread` function. Channel labels and metadata are inspected to verify correct data import.

### Sampling Frequency Determination
The sampling frequency is extracted from EDF header information, as timetable row times correspond to record timing rather than individual EEG samples.

### Filtering
A **4th-order IIR Butterworth high-pass filter** with a cutoff frequency of **0.5 Hz** is designed to remove low-frequency baseline drift. An IIR filter is selected for computational efficiency at low cutoff frequencies.

### Music Segmentation
The continuous EEG recording is segmented into time intervals corresponding to different music conditions:
- Pre-recording  
- Metal  
- Classical music  
- Relaxing music  
- Favourite song  
- Post-recording  

### Frequency-Band Analysis
Standard EEG frequency bands are defined and analyzed:
- Delta: 0.5–4 Hz  
- Theta: 4–8 Hz  
- Alpha: 8–13 Hz  
- Beta: 13–30 Hz  
- Gamma: 30–45 Hz  

### Feature Extraction
For each music segment and EEG channel (O1 and O2):
- Band power is computed  
- Relative band power is calculated  
- The **Power Ratio Index (PRI)** is derived:

PRI = (Delta + Theta) / (Alpha + Beta + Gamma)


### Wavelet Decomposition
Discrete Wavelet Transform (DWT) is applied to decompose EEG signals into frequency components while preserving time frequency information, which is well suited for non stationary EEG data.

---

## Interpretation of Results
- Low-frequency EEG bands dominate signal amplitude, consistent with normal physiological behavior  
- Alpha activity is prominent in occipital channels during relaxed music listening  
- Beta and Gamma bands exhibit lower amplitude but reflect cognitive engagement  
- Different music styles influence EEG rhythms in a measurable and comparable manner  

---

## Tools and Requirements
- MATLAB  
- Signal Processing Toolbox  
- Wavelet Toolbox  

---

## Learning Outcomes
- Practical EEG preprocessing and digital filtering  
- Frequency-domain and time frequency EEG analysis  
- Feature extraction and quantitative comparison across conditions  
- Interpretation of EEG rhythms in response to auditory stimuli  

---

## Disclaimer
This project is intended for educational and research purposes only and does not provide medical or clinical diagnosis.

---

## Author
**Samson Agbadi**  
MSc Biomedical Engineering  EEG Signal Processing Project

