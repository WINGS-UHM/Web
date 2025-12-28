---
layout: post
title: mmWave Breathing Pattern Detection
description: How to create a docs site for your project with WINGS Lab 
date: 2024-08-01 00:00:00
hero_image: /assets/img/project/AIoT_Breath.png
hero_height: is-large
hero_darken: true
image: /assets/img/project/AIoT_Breath.png
tags: mmWave ISAC
series: project_series_isac
testbed_facilities: testbed_breathing
author: sparkar
summary: A lightweight Integrated Sensing and Communication (ISAC) framework is presented for contactless respiration pattern recognition using a composite OFDM–FMCW waveform at 28 GHz mmWave. A narrowband FMCW radar signal is embedded into the OFDM guard band, enabling simultaneous high-resolution sensing and data communication without modifying the OFDM structure or requiring additional hardware.
---

# On this Page  <!-- omit in toc -->
- [Overview](#overview)
  - [Highlights](#highlights)
- [Methodology](#methodology)
  - [Composite Waveform design](#composite-waveform-design)
  - [Sensing Pipeline](#sensing-pipeline)
  - [Respiration Patern Extraction](#respiration-patern-extraction)
- [Experimental Setup](#experimental-setup)
- [Deep Learning Model for Pattern Classification](#deep-learning-model-for-pattern-classification)
- [Results](#results)

## Overview
A lightweight Integrated Sensing and Communication (ISAC) framework is presented for contactless respiration pattern recognition using a composite OFDM–FMCW waveform at 28 GHz mmWave.
A narrowband FMCW radar signal is embedded into the OFDM guard band, enabling simultaneous high-resolution sensing and data communication without modifying the OFDM structure or requiring additional hardware.

### Highlights
- Guard-band FMCW reuse preserves 5G NR spectral integrity

- Robust respiration sensing under realistic body motion

- Hardware validation on a mmWave USRP testbed

- End-to-end AI pipeline achieving >98% classification accuracy

## Methodology

### Composite Waveform design
- Narrowband FMCW chirps embedded into unused OFDM guard bands

- No changes to OFDM modulation, framing, or scheduling

- FMCW sweep bandwidth evaluated from 0.25–2 MHz

- FMCW-to-OFDM power ratio systematically analyzed to balance sensing and communication
<div style="text-align: center; margin: 1.5rem 0;">
  <img src="{{"/assets/img/isac-breathing/spectrogram.png"  | relative_url }}" 
       alt="Waveform Spectrogram" 
       style="max-width: 100%; height: auto;" />
  <div style="margin-top: 0.5rem; font-size: 0.9rem; color: #444444;">
    Fig. 1. Waveform Spectrogram
  </div>
</div>

### Sensing Pipeline
**OFDM Mode**
- Compensation for SFO, STO, and CFO
- CSI phase extraction per active subcarrier
- Linear detrending for phase sanitization
<div style="text-align: center; margin: 1.5rem 0;">
  <img src="{{"/assets/img/isac-breathing/sfo_sto_a.png" | relative_url }}" 
       alt="unprocessed phase" 
       style="max-width: 100%; height: auto;" />
  <div style="margin-top: 0.5rem; font-size: 0.9rem; color: #444444;">
    Fig. 2.1. Raw phase with SFO/STO trend. 
  </div>
</div>
<div style="text-align: center; margin: 1.5rem 0;">
  <img src="{{"/assets/img/isac-breathing/sfo_sto_c.png"  | relative_url }} "
       alt="processed phase" 
       style="max-width: 100%; height: auto;" />
  <div style="margin-top: 0.5rem; font-size: 0.9rem; color: #444444;">
    Fig. 2.2. Zoomed view showing respiratory cycles amid noise.
  </div>
</div>

**FMCW Mode**
- Dechirping and beat-frequency extraction

- Range-bin selection for slow-time respiration signal

- Drift suppression using detrend filtering


### Respiration Patern Extraction
- Hampel filtering, Moving-average and median filtering for smoothing
- Empirical Wavelet Transform (EWT) for adaptive respiration-band isolation
- Hilbert transform used to extract amplitude envelopes and normalize signals

<div style="text-align: center; margin: 2rem 0;">
  <!-- Subfigures row -->
  <div style="display: flex; justify-content: center; gap: 1rem; flex-wrap: wrap;">
    <div style="flex: 1; max-width: 32%;">
      <img src="{{"/assets/img/isac-breathing/eupnea_median_filtered.png"  | relative_url }}" alt="Subfigure A" style="width: 100%; height: auto;">
      <div style="font-size: 0.85rem; margin-top: 0.4rem; color: #555;">
        Raw and Preprocessed beat signal
      </div>
    </div>
    <div style="flex: 1; max-width: 32%;">
      <img src="{{"/assets/img/isac-breathing/eupnea_ewt.png"  | relative_url }}" alt="Subfigure B" style="width: 100%; height: auto;">
      <div style="font-size: 0.85rem; margin-top: 0.4rem; color: #555;">
        EWT based decomposition for pattern isolation
      </div>
    </div>
    <div style="flex: 1; max-width: 32%;">
      <img src="{{"/assets/img/isac-breathing/eupnea_extracted.png"  | relative_url }}" alt="Subfigure C" style="width: 100%; height: auto;">
      <div style="font-size: 0.85rem; margin-top: 0.4rem; color: #555;">
        Hilbert transform and pattern normalization
      </div>
    </div>

  </div>
  <!-- Main caption -->
  <div style="margin-top: 0.75rem; font-size: 0.9rem; color: #444;">
    Fig. 3. Pattern Extraction for FMCW mode
  </div>
</div>

<div style="text-align: center; margin: 2rem 0;">
  <!-- Subfigures row -->
  <div style="display: flex; justify-content: center; gap: 1rem; flex-wrap: wrap;">
    <div style="flex: 1; max-width: 32%;">
      <img src="{{"/assets/img/isac-breathing/ofdm_raw_phase_eupnea.png"  | relative_url }}" alt="Subfigure A" style="width: 100%; height: auto;">
      <div style="font-size: 0.85rem; margin-top: 0.4rem; color: #555;">
        Phase denoising and smoothing
      </div>
    </div>
    <div style="flex: 1; max-width: 32%;">
      <img src="{{"/assets/img/isac-breathing/ofdm_ewts_eupnea.png"  | relative_url }}" alt="Subfigure B" style="width: 100%; height: auto;">
      <div style="font-size: 0.85rem; margin-top: 0.4rem; color: #555;">
        EWT based decomposition for pattern isolation
      </div>
    </div>
    <div style="flex: 1; max-width: 32%;">
      <img src="{{"/assets/img/isac-breathing/ofdm_extracted_eupnea.png"  | relative_url }}" alt="Subfigure C" style="width: 100%; height: auto;">
      <div style="font-size: 0.85rem; margin-top: 0.4rem; color: #555;">
        Hilbert transform and pattern normalization
      </div>
    </div>

  </div>
  <!-- Main caption -->
  <div style="margin-top: 0.75rem; font-size: 0.9rem; color: #444;">
    Fig. 4. Pattern Extraction for OFDM mode
  </div>
</div>

## Experimental Setup

- 28 GHz mmWave testbed based on NI-USRP-2974

- 16-channel transmit and 4-channel receive phased arrays

<div style="text-align: center; margin: 1.5rem 0;">
  <img src="{{"/assets/img/project/AIoT_Breath.png"  | relative_url }}"
       alt="Experimental Setup" 
       style="max-width: 75%; height: auto;" />
  <div style="margin-top: 0.5rem; font-size: 0.9rem; color: #444444;">
    Fig. 5. Experimental Setup
  </div>
</div>


## Deep Learning Model for Pattern Classification
- Input: normalized respiration waveforms

- Model: lightweight 1D convolutional neural network (1D-CNN)

- Two convolution layers followed by global max pooling

- Output: multi-class respiration pattern prediction

<div style="text-align: center; margin: 1.5rem 0;">
  <img src="{{"/assets/img/isac-breathing/cnn_model.png"  | relative_url }}"
       alt="CNN model" 
       style="max-width: 300px; height: auto;" />
  <div style="margin-top: 0.5rem; font-size: 0.9rem; color: #444444;">
    Fig. 6. CNN model Structure
  </div>
</div>

## Results

- Overall classification accuracy: 98–98.5%; Eupnea and Kussmaul patterns achieve 100% accuracy.
- FMCW sensing maintains stable respiration extraction under body and hand movement with similarity score of 89.2%
- OFDM CSI-based sensing degrades under motion due to multipath sensitivity with similarity score of 83.5%
- Communication EVM : 20.36%

<div style="text-align: center; margin: 1.5rem 0;">
  <img src="{{"/assets/img/isac-breathing/classification_results.png"  | relative_url }}"
       alt="Classification Results" 
       style="max-width: 500px; height: auto;" />
  <div style="margin-top: 0.5rem; font-size: 0.9rem; color: #444444;">
    Fig. 7. Confusion matrix of the classification model
  </div>
</div>