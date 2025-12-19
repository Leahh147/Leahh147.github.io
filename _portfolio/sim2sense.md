---
title: "SIM2SENSE: Multisensory RL-based Biomechanical User Simulation"
collection: portfolio
excerpt: "Extending SIM2VR with auditory perception to enable multisensory perceptuomotor interaction in VR."
date: 2025-06-02

header:
  teaser: /images/sim2sense.gif

github: https://github.com/Leahh147/SIM2SENSE
institution: University of Cambridge
role: Final Year / Master’s Project

tags:
  - Reinforcement Learning
  - Multimodal Learning
  - VR
  - Biomechanical Simulation
  - Human-Computer Interaction
---

## Overview

**SIM2SENSE** is a reinforcement learning–based biomechanical simulation framework that extends **SIM2VR** and **User-in-the-Box (UitB)** by integrating **auditory perception** alongside vision and proprioception.  
The goal is to model **multisensory perceptuomotor interaction** in virtual reality more faithfully, enabling simulated users to *hear*, *see*, and *act* within real VR applications.

This project was completed as my **Final Year / Master’s project at the University of Cambridge**, supervised by **Dr. Florian Fischer** and **Prof. Per Ola Kristensson**.

---

## Demo

<img src="/images/sim2sense.gif" alt="SIM2SENSE multisensory RL demo" width="800">

*RL-controlled biomechanical arm interacting with a VR Whac-A-Mole task using auditory, visual, and proprioceptive feedback.*

---

## Motivation

Existing RL-based biomechanical user models (e.g. UitB, SIM2VR) rely primarily on **visual and proprioceptive feedback**, limiting their ecological validity in VR environments where **audio cues play a critical role** in:

- Spatial localization  
- Temporal coordination  
- Off-screen event awareness  

SIM2SENSE addresses this gap by **closing the auditory loop** in RL-based biomechanical control.

---

## Method

### Multisensory Perception Pipeline

At each timestep, the agent receives:

- **Vision**: RGB-D observations from the Unity VR environment  
- **Proprioception**: Joint angles, velocities, and muscle states  
- **Audio**:  
  - **Stereo amplitude audio** for spatial guidance  
  - **Mono amplitude audio** for temporal signaling  

Each modality is processed by a dedicated encoder and fused into a **shared policy network** trained using **Proximal Policy Optimization (PPO)**.

---

### Auditory Integration

- Audio captured via **ml-audio-sensor** at 20 Hz  
- Configurable signal modes:
  - **Stereo + Amplitude** → spatial localization
  - **Mono + Amplitude** → timing cues
- Encoder architectures:
  - CNN-based encoders for spatial audio
  - CNN / LSTM-based encoders for temporal audio
- Audio features concatenated with visual and proprioceptive embeddings

---

### Control & Learning

- **7-DoF muscle-actuated upper-limb model**
- Continuous control via PPO
- Reward formulation balances:
  - Task performance (hit accuracy, reaction time)
  - Biomechanical effort (muscle activation penalties)

---

## Tasks & Evaluation

### VR Whac-A-Mole

- 3×3 target grid
- Single-target (easy mode)
- Spatial audio attached to targets
- Multiple sensory configurations evaluated:
  - Vision-only (SIM2VR baseline)
  - Vision + Audio (stereo / mono)
  - Audio-only variants
  - Dense vs. sparse reward structures

### Metrics

- **Hit rate**
- **Reaction time**
- **Movement plausibility**
- **Qualitative motion patterns**

---

## Key Results

- **Multisensory models outperform vision-only baselines**
  - Higher hit rates
  - Significantly reduced reaction times
- **Stereo audio provides meaningful spatial information**
  - Enables directional guidance even without vision
- **Audio-only agents exhibit distinct movement strategies**
  - Straighter arm postures
  - Less biomechanically economical behavior
- Reward structure strongly interacts with sensory modality

These results highlight both the **promise and challenges** of multisensory RL for biomechanical realism.

---

## Contributions

- First integration of **auditory perception** into SIM2VR-style RL biomechanical simulation
- Modular multisensory perception framework (vision + proprioception + audio)
- Empirical analysis of **audio–vision–reward interactions** in VR tasks
- Foundation for future work in:
  - Multisensory VR interface evaluation
  - Accessibility modeling
  - Audio-guided interaction design

---

## Future Work

- More realistic auditory encoding (frequency-domain features)
- Cognitive constraints (attention, sensory processing costs)
- User studies comparing simulated and real VR users
- Extension to speech and semantic audio cues

