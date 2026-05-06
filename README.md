# Lensless Image Reconstruction Using Physics Guided Genetic Programming

This repository contains the implementation of a physics-guided genetic programming framework for single-shot lensless image reconstruction. The code evolves tile-dependent reconstruction hyperparameters using genetic programming and applies them to a gradient-descent-based inverse model for recovering object-plane amplitude, reconstructed intensity, phase, and object-sensor distance information from a single lensless intensity measurement.

## Associated Article

**Title:** Single-Shot Lensless Imaging with Physics-Guided Genetic Programming  
**Authors:** Ganesh M. Balasubramaniam, Xiao-Liu Chu, Radhika V. Nair, Matthew R. Foreman  

**Preprint:** https://doi.org/10.48550/arXiv.2604.22270  

The final article link will be added after publication.

## Overview

The framework combines two optimization stages:

1. **Outer optimization using genetic programming**
   - Evolves symbolic policies that map tile-level image features to reconstruction hyperparameters.
   - Uses DEAP-based genetic programming with NSGA-II selection.
   - Optimizes reconstruction quality while penalizing runtime and policy complexity.

2. **Inner physics-guided reconstruction**
   - Performs gradient-based optimization of object amplitude, phase, and propagation distance.
   - Uses an angular-spectrum forward model.
   - Enforces physical constraints on object-sensor distance.
   - Reconstructs individual overlapped tiles and stitches the non-overlapped cores into full-field images.

## Main Features

- Single-shot lensless image reconstruction.
- Tile-wise adaptive hyperparameter generation using genetic programming.
- Complex object reconstruction with amplitude and phase recovery.
- Bounded object-sensor distance optimization.
- Angular-spectrum propagation model implemented in PyTorch.
- Multi-objective GP fitness based on reconstruction SSIM, runtime, and symbolic tree size.
- Automatic saving of reconstructed tiles and stitched full-field outputs.
- GPU support when CUDA is available.

## Repository Contents

The main script performs the complete workflow:

1. Load lensless input image.
2. Divide the image into overlapped tiles.
3. Evolve GP policies for reconstruction hyperparameters.
4. Apply the best evolved policy to all tiles.
5. Save reconstructed tile outputs.
6. Stitch the full-field amplitude, intensity, and phase reconstructions.

## Requirements

numpy
torch
imageio
scikit-image
scipy
deap
tqdm

## Input Image

USAF.png
