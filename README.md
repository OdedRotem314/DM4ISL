# DDPM4ISL (Denoising diffusion probabalistic model forIn silico labeling)


## Paper Abstract

In silico labeling prediction of organelle fluorescence from label-free microscopy images has the potential to revolutionize our understanding of cells as integrated complex systems. However, out-of-distribution data caused by changes in the intracellular organization across cell types, cellular processes or perturbations, can lead to altered label-free images and impaired in silico labeling. We demonstrated that incorporating biological meaningful cell contexts, via a context-dependent model that we call CELTIC, enhanced in silico labeling prediction and enabled downstream analysis of out-of-distribution data such as cells undergoing mitosis, and cells located at the edge of the colony. These results suggest a link between cell context and intracellular organization. Using CELTIC for generative traversal along single cells undergoing context transition enabled integrated characterization of the gradual alterations in cellular organization across multiple organelles, overcoming inter-cell variability. The explicit inclusion of context has the potential to harmonize multiple datasets, paving the way for generalized in silico labeling foundation models.

<img src="assets/f2.png" width="700" />


## Framework

### Overview
DDPM4ISL is a framework designed to predict organelle fluorescence in label-free microscopy images based on diffusion models and a inference optimized mechanism for improved results. This repository includes the source code for training, inderence, and results analysis.


### Example Notebooks
- **TRAINING notebook**: 

    This notebook demonstrates how to train the DDPM4ISL model using paired brightfield and organelle fluoresnce images. 
    
- **INFERENCE notebook**:

    This notebook demonstrates how to predict a flouresnce image using a trained DDPM4ISL model and brightfield input images. 

- **RESULTS_ANALYSIS**:

    This notebook provides a detailed walkthrough of how to analyze prediction results using all evaluation metrics described in the paper.

### Data

The full data of paired brightfield and fluorescence images can be downloaded from the allen intitute of cell science
[https://open.quiltdata.com/b/allencell/packages/aics/label-free-imaging-collection/tree/latest/](https://open.quiltdata.com/b/allencell/packages/aics/label-free-imaging-collection/tree/latest/)

We provide several patches of Nuclear Envelope under data/NucEnv, allowing you to run the training, inference and analysis notebooks.

**The data directory includes**:
- BF - brightfield patches
- GT - fluorescence patches use for ground truth

**The INFERENCE notebook will save data into the following folders:**
- FL_pred - predictions of the DDPM final output
- FLavg_pred - predictions of the DDPM4ISL average
- FLavg_std - standard deviation images using the intermidiate timesteps
- FLavg_std_seg - binary image of FLavg_std spotting erroneuos locations
- FLavg_std_seeds - standard deviation images using the intermidiate timesteps initiaed from multiple seeds
- FLavg_std_seg_seeds - binary image of FLavg_std_seeds spotting erroneuos locations

**To run the RESULTS_ANALYSIS notebook we also provide samples from Unet and GAN predictions:**
- Unet
- GAN

## Installation and Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/zaritskylab/DDPM4ISL

2. Install the required dependencies:
    ```bash
    %cd DDPM4ISL
    !pip install requirements.
3. Download two models from hugging face https://huggingface.co/OdedRot/DDPM4ISL/tree/main
   Add CLS.pth to saved_models/CLS
   Add NucEnv.pth to saved_models/NucEnv
4. For every notebook you use, update the "main_path" directory path.
5. To train a new model use the TRAINING notebook.
6. To run inference on a trained model use the INFERENCE notebook.
7. To evaluate predictions on a trained model use the RESULTS_ANALYSIS notebook.

## Acknowledgement
Based on the MONAI framework found here:
https://github.com/Project-MONAI/MONAI

