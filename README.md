# Transfer learning between Sentinel-1 acquisition modes enhances the few-shot segmentation of natural oil slicks in the Arctic

This repository contains the code and data for the project **Transfer learning between Sentinel-1 acquisition modes enhances the few-shot segmentation of natural oil slicks in the Arctic**.

The associated article has been submitted.

---

## Contents
1. [Abstract](#abstract)
2. [Repo structure](#rep-structure)
3. [Data](#data)
4. [Contact](#contact)

---

## Abstract
Natural seepage is a significant contributor to marine hydrocarbon inputs. Remote and intermittent seeps are difficult to monitor in the field, yet oil slicks can be observed from spaceborne 
    synthetic aperture radar (SAR) due to differences in their backscatter,
    creating potential for automatic mapping. In mapping tasks such as segmentation, deep learning models excel, whilst needing large amounts of labeled images.
    To deal with scarcity of labeled images, transfer learning is an approach 
    commonly used in computer vision, yet still underutilized in remote sensing. In the case of oil slicks, differences between Sentinel-1 acquisition modes—such as the 
    interferometric wide (IW) in the North Sea and extra-wide (EW) in the Arctic—complicate direct model transfer.
    Here, we present a use-case where transfer learning enhances the segmentation of natural oil slicks. We used labeled slicks in IW images in the North Sea to pretrain a series of DeepLabv3 and SAM models. 
    These models were then fine-tuned on EW-labeled slicks from two documented Arctic seeps on which we have only limited observations. Our results show clear evidence that transfer learning improves few-shot 
    segmentation, even in challenging images with slick look-alikes. Overall, few studies have addressed transfer learning between SAR acquisition modes, and this work contributes to 
    better monitoring poorly understood or yet undiscovered natural oil seeps. 

---

## Repo structure
```plaintext
main/
├── data/                     # Raw and processed data
│   ├── s1*/                              # Unprocessed Sentinel-1 (S1) satellite images
│   ├── training_samples*/                # Processed training samples and labeled tiles
|   ├── pred*/                            # Model predictions
|   ├── model_results/                    # Tables of results (Dice scores on the test set)
|   ├── fig_samples/                      # training samples used to produced Fig. 3
├── models/                   # deep learning model folders
|   ├── pretrained*                       # Models pretrained on IW-VV S1 images in the North Sea
|   ├── base*                             # Models trained solely on EW-HH images in the Arctic (with backbone/checkpoint weights)
|   ├── transfer_learning*                # Models using the North Sea pretrained weights, then fine-tuned on the EW-HH Arctic images
├── src/                      # Source code for models and utilities
|   ├── ASF-S1.ipynb                      # code to download S1 imagery from the ASF api
|   ├── format_tiff_s1_folders.ipynb      # utilities code to format folders after downloading S1 images
|   ├── export_samples.ipynb              # code to create training samples from labeled polygons and imagery
│   ├── model_training.py                 # code to batch train deep learning models with ArcPy
│   ├── analysis.ipynb                    # code to generate model predictions and compute test-set dice scores
│   └── figures.ipynb                     # code to generate figures
├── latex/                    # latex code for generating the manuscript    
|   ├── figures                           # Output figures, maps, and plots
|   ├── manuscript.tex                    # Manuscript in LaTeX format
|   ├── manuscript.pdf                    # Manuscript in PDF format
|   ├── references.bib                    # BibTeX reference list
├── temp/                     # Temp folder for data processing
├── conda_env.yml             # Conda environment file with required Python libraries
├── README.md                 # Project documentation (this file)
└── LICENSE                   # CC BY 4.0 license
```
*Folder not uploaded due to storage limitation. Contact corresponding author for data access.

---

## Data Sources
The project used:
- **Sentinel-1 imagery** (https://dataspace.copernicus.eu)
- **Labeled slicks observed in Sentinel-1 images**. *We are open to data sharing, please contact us*
   - In the North Sea (2017-2021).
   - Prins Karls Forland, Svalbard (2015-2024). See https://doi.org/10.1016/j.scitotenv.2023.167788
   - Sentralbanken High, Barents Sea (2015-2020) See https://doi.org/10.1038/s41467-023-37514-9

**Note**: Raw data is not included in this repository due to size constraints.

---

## Contact
For questions or collaborations, please contact the corresponding author:
- **Name**: Julien Vadnais
- **Email**: julien.vadnais@uib.no
- **GitHub**: [@julvad](https://github.com/julvad)
---
