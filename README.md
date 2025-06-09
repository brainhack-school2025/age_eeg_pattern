# Age-Dependent EEG Patterns for Predicting Treatment Response in ADHD

<a href="https://github.com/lamanda0227">
   <img src="https://avatars.githubusercontent.com/u/51805224?v=4" width="100px;" alt=""/>
   <br /><sub><b>Tianyi/Amanda Liu</b></sub>
</a>

First year PhD student at Institute of Medical Science at University of Toronto. My thesis focuses on multi-omic characterization of cell-type specific pathway for bipolar disorder using a Whole Person and Population Modelling modelling approach.

## Background

Attention Deficit Hyperactivity Disorder (ADHD) is a neurodevelopmental and psychiatric disorder that exhibits significant age-related changes throughout development. Electroencephalography (EEG) has emerged as a powerful neuroimaging technique for extracting neural features and patterns associated with ADHD, particularly theta-beta ratios and alpha peak frequency variations.

While machine learning approaches have shown promise for age prediction using neural data, there remains a critical gap in developing treatments based on EEG patterns and age-specific considerations for individuals with ADHD. Current research has established that EEG biomarkers change across the lifespan, but the relationship between these developmental patterns and treatment response remains poorly understood.

## Objectives

1. **Characterize age-related EEG patterns in treatment response**
2. **Assess age-specificity of EEG-based treatment prediction**
3. **Identify EEG signatures of neurofeedback treatment response across development**

## Data

**TDBrain Database**

- **Source**: [Brainclinics Foundation](https://brainclinics.com/resources/tdbrain-dataset/introduction/downloads)
- **Total Dataset**: 1,274 participants collected over two decades
- **ADHD Subset**: 204 ADHD participants (70 with treatment response data)
- **Age Range**: 5-89 years
- **Data Types**: Raw resting-state EEG recordings, NEO-FFI personality data, demographic information, and neurofeedback treatment outcomes

## Tools

**Python**

- **Data Processing**: numpy, scipy, pandas
- **EEG Feature Extraction**: FOOOF
- **Visualization**: matplotlib, seaborn

**R Packages:**

- **Machine Learning**: caret, randomForest
- **Visualization**: ggplot2

Jupyter notebooks

## Pipeline

1. Data preprocessing
    - Artifact identification, removal and cleaning
    - Epoching of continuous EEG data
    - Feature extraction (frequency bands, power ratios)
2. **Data Preparation**
    - Load demographics and EEG data (204 ADHD samples)
    - Extract treatment response subset (70 participants)
    - Merging extracted feature with meta-data
3. **Feature Selection**
    - 100 bootstrap evaluations per feature count
    - Optimization to 60 optimal features
4. **Model Development**
    - Random Forest implementation (1000 trees, balanced class weights)
    - Out-of-bag bootstrap with median imputation
5. **Age-Related Analysis**
    - Age tertile stratification (youngest, middle, oldest)
    - Correlation analysis between age and EEG features
    - Developmental trajectory visualization

## Repository Structure

```
├── README.md                          # This file
├── LICENSE                           # MIT License
├── analysis_code/                    # Analysis notebooks
│   ├── pre-process-py.ipynb         # Python preprocessing workflow
│   ├── pre-process.ipynb            # R preprocessing workflow  
│   └── running_analysis.ipynb       # Main analysis pipeline
```

**Notebook Descriptions:**

- **`pre-process-py.ipynb`**: Python preprocessing workflow including data loading, feature extraction, and demographic integration
- **`pre-process.ipynb`**: R preprocessing workflow with statistical analysis and age-stratified preparation
- **`running_analysis.ipynb`**: Main analysis pipeline with machine learning model development, feature selection, and age-related pattern visualizations

## Key Results

**Model Performance:**

- Random Forest achieved **AUC = 0.865** for treatment response prediction
- Optimal performance with **60 features** selected from 100+ candidates

**Top Predictive Features:**

1. **C3_delta_rel** - Central delta relative power
2. **CPz_fooof_alpha_cf** - Central-parietal alpha center frequency
3. **T8_theta_beta_ratio** - Right temporal theta-beta ratio
4. **Age** - Chronological age (8th most important predictor)

**Age-Related Findings:**

- **Most Age-Variable Features**: F4_delta_abs, T8_fooof_offset, C3_delta_rel showed highest variability across development
- No visible or obvious difference for responder v.s. non-responder for different age groups
- Result non-interpretable due to low sample size and imbalanced responder and non-responder groups

## Acknowledgments

- **Data Source**: [Brainclinics Foundation](https://brainclinics.com/) for providing the TDBrain dataset and preprocessing pipeline
- **Community**: [BrainHack School](https://school.brainhackmtl.org/) for supporting this collaborative research
- **Authors**: Amanda/Tianyi Liu and Ingrid Campbell, Institute of Medical Science, University of Toronto
