# ScoreMatch: Classical Composer Identification from MIDI

*AAI-511 Neural Networks and Deep Learning*  
University of San Diego – Team 4  
Nicholas Alforque · Thomas Geraci · Cameron Aljilani

## Overview

ScoreMatch classifies classical MIDI files as works by Bach, Beethoven, Chopin, or Mozart. The project compares two modeling approaches under the same stratified file-level splits:

1. Classical machine-learning models trained on 42 engineered symbolic MIDI features extracted with `pretty_midi`
2. Deep-learning models (CNN and CNN-LSTM) trained on 20 FPS piano-roll representations fused with the same engineered features

Primary experiments used a balanced subset of 136 files per composer. Random Forest achieved the strongest balanced result with **0.8611 accuracy** and **0.8590 macro-F1**. The strongest pure deep-learning model was the **15-second CNN**, which achieved **0.7778 accuracy** and **0.7776 macro-F1**.

Additional experiments evaluated stronger augmentation, hybrid CNN-engineered features, and training on the complete four-composer collection of 1,628 valid MIDI files.

## Team Roles

- **Nicholas Alforque** – data collection, dataset organization, MIDI parsing, and feature extraction
- **Thomas Geraci** – CNN/CNN-LSTM design and training, piano-roll pipeline, 10- and 15-second experiments, augmentation, and model checkpointing
- **Cameron Aljilani** – evaluation, confusion-matrix analysis, hybrid/full-dataset experiments, and final report compilation

## Repository Contents

- `aai_511_team_4_final.ipynb` – complete project pipeline
- `Final Project Notebook Team 4.html` – rendered notebook with code and saved outputs
- `Final Project Report Team 4.pdf` – final technical report
- `datasets/` – project dataset-related files or supporting materials

## Dataset

This project uses the Kaggle **midi-classic-music** dataset (Fedorak, 2019).

The original Kaggle dataset contains a larger and relatively unorganized collection of MIDI files. For this project, the files for the four required composers were reorganized into a cleaner project-specific archive containing only:

- Bach
- Beethoven
- Chopin
- Mozart

The MIDI content itself was not modified. The reorganization was performed so the notebook could reliably locate and process the required composer folders.

The curated archive was uploaded directly to Google Colab before running the notebook.

### Required Archive Structure

The notebook expects the uploaded ZIP file to contain an `archive` directory, with the four composer folders inside it:

```text
archive.zip
└── archive/
    ├── Bach/
    │   ├── *.mid
    │   └── ...
    ├── Beethoven/
    │   ├── *.mid
    │   └── ...
    ├── Chopin/
    │   ├── *.mid
    │   └── ...
    └── Mozart/
        ├── *.mid
        └── ...
