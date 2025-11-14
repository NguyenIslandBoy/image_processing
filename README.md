# Automated Detection and Segmentation of Retinal Cysts in OCT Images

## Overview

A classical image processing pipeline for automated detection and segmentation of retinal cysts in Optical Coherence Tomography (OCT) images using traditional computer vision techniques.

**Results:** Mean Dice Coefficient of **56.85% ± 14.44%** across 10 test images  
**Best Performance:** 75.34% (TRAINING3) | **Worst:** 30.43% (TRAINING1)

**Key Features:**
- Fully automated - no manual intervention required
- No training data or deep learning models needed
- Fast processing: 2-3 seconds per image on CPU
- Interpretable at every step
- Modular design for easy modification

## Pipeline Architecture

```
Input OCT Images
       ↓
1. Preprocessing
   • Reference-based histogram matching
   • Exponential enhancement (1.05^im - 1)
   • Align to cleanest image (TRAINING6)
       ↓
2. Binary Segmentation
   • Otsu thresholding (inverse)
   • Morphological opening (disk 1)
   • Clear border artifacts
       ↓
3. Watershed Segmentation
   • Distance transform
   • Peak detection (3×3 footprint)
   • Separate clustered cysts
       ↓
4. Feature Extraction & Filtering
   • Extract: area, intensity_mean, eccentricity
   • Filter: area ≥ mean AND intensity ≤ mean
       ↓
5. Post-Processing
   • Binary closing (disk 2)
   • Remove small objects (< 15 pixels)
       ↓
Output Binary Masks
```

## Requirements

- Python 3.8+
- NumPy, scikit-image, SciPy, Pandas, Matplotlib

## Usage

See `Traditional OCT Cyst Detection.ipynb` for complete implementation with step-by-step visualizations.
