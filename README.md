EEG Music Analysis Project
Overview

This project implements a complete EEG signal processing pipeline to analyze how different music styles affect brain activity.
The EEG data is processed using MATLAB, following standard biomedical signal-processing methods, including filtering, frequency-band analysis, Fourier analysis, and wavelet decomposition.

The project demonstrates how raw EEG recordings can be transformed into interpretable brain rhythm features and compared across music conditions and EEG channels.

Dataset

Format: EDF (European Data Format)

File: Proband1.EDF

Type: Multichannel EEG recording

Sampling frequency: ~200 Hz (determined from EDF header)

Channels used for analysis: O1 and O2 (occipital cortex)

Objectives

The goals of this project are to:

Load and inspect real EEG data

Determine the correct sampling frequency

Remove low-frequency baseline drift

Segment EEG data based on music styles

Analyze EEG frequency bands (Delta–Gamma)

Compare brain activity across music conditions

Quantify results using band power and indices

Visualize EEG bands using wavelet decomposition

Processing Pipeline (Tasks 1–8)
Task 1 – Read EEG Data

The EEG data is loaded using MATLAB’s edfread function.
Channel names and metadata are inspected to understand the structure of the recording.

Task 2 – Determine Sampling Rate

The sampling frequency is extracted from the EDF header information.
This step is essential for correct frequency analysis, filtering, and spectral computations.

Task 3 – High-Pass Filter Design

A 0.5 Hz high-pass IIR Butterworth filter is designed to remove:

Baseline drift

Very slow non-physiological components

Why IIR?

Efficient for low cutoff frequencies

Requires lower filter order than FIR

Standard practice in EEG preprocessing

Task 4 – Music Segmentation

The continuous EEG recording is segmented into time intervals corresponding to different music styles:

Pre-recording

Metal

Classical music

Relaxing music

Favourite song

Post-recording

Each segment is analyzed independently.

Task 5 – EEG Frequency Bands

Standard EEG frequency bands are defined:

Band	Frequency Range (Hz)
Delta	0.5 – 4
Theta	4 – 8
Alpha	8 – 13
Beta	13 – 30
Gamma	30 – 45

These bands correspond to different physiological and cognitive states.

Task 6 – Analysis by Song and Channel

For each music segment and EEG channel (O1, O2):

The signal is filtered

Band power is computed

Relative band power is calculated

The Power Ratio Index (PRI) is derived

Power Ratio Index (PRI):

PRI
=
Delta + Theta
Alpha + Beta + Gamma
PRI=
Alpha + Beta + Gamma
Delta + Theta
	​


PRI provides a compact measure of slow vs. fast brain activity dominance.

Task 7 – Results Table and Export

All computed features are stored in a MATLAB table and exported as an Excel file (.xlsx) using:

table

writetable

winopen

This enables further analysis and reporting outside MATLAB.

Task 8 – Wavelet Decomposition

Discrete Wavelet Transform (DWT) is used to decompose EEG signals into individual frequency bands.

Why wavelets?

EEG is non-stationary

Wavelets preserve both time and frequency information

Suitable for analyzing dynamic brain responses to music

Each music condition and channel is visualized with separate Delta–Gamma band signals.

Interpretation of Results

Low-frequency bands (Delta, Theta) dominate amplitude, which is normal in EEG.

High-frequency bands (Beta, Gamma) have lower amplitude but reflect cognitive engagement.

Differences between music styles are interpreted relatively, not by absolute amplitude.

O1 and O2 channels are used because they provide stable measurements related to visual and relaxation processes.

Key Takeaways

EEG analysis focuses on patterns and comparisons, not raw voltages.

Music influences brain rhythms in measurable ways.

Frequency-based features and ratios provide meaningful insights into brain state changes.

This pipeline reflects standard EEG preprocessing and analysis used in research.

Tools and Methods

MATLAB

Signal Processing Toolbox

Wavelet Toolbox

EDF medical data format

Disclaimer

This project is for educational purposes only.
It does not perform medical diagnosis or clinical interpretation.

Author

Samson Agbadi 
EEG Signal Processing & Biomedical Engineering Project