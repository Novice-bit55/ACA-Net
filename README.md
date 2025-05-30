# ACA-Net: Adaptive Cloud-Aware Network for Thick Cloud Removal in Remote Sensing Images

![ACA-Net Architecture](./figures/main.jpg)  
*Figure 1: Architecture overview of ACA-Net*

Official PyTorch implementation of the paper "ACA-Net: Adaptive Cloud-Aware Network for Thick Cloud Removal for Remote Sensing Images" .

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Citation](#citation)

## Introduction
ACA-Net proposes an adaptive cloud-aware network architecture for effective thick cloud removal in remote sensing images through:

- 🌐 **Complete feature representation through spatial feature preservation and spectral detail integration.** 
- 🎯 **Adaptive reconstruction by optimizing frequency operations for different cloud occlusion ratios.** 
- 📊 **Stable convergence by mitigating the risk of gradient vanishing.** 

Key advantages:
- Maintains texture details under heavy cloud coverage
- Adapts to varying cloud occlusion
- Lightweight yet effective architecture

## Installation

### Requirements
- Python 3.8+
- PyTorch 1.12.1+
- CUDA 11.6+
- NVIDIA GPU with ≥8GB VRAM

### Setup
1. Clone repository:
```bash
git clone https://github.com/yourusername/ACA-Net.git && cd ACA-Net
```
Install dependencies:

```bash
pip install -r requirements.txt
```
## Usage
Data Organization
Organize datasets as:
```
dataset/
├── train/
│   ├── mask/   
│   │     ├── 1/ #Temporal-1 cloud mask
│   │     ├── 2/ #Temporal-2 cloud mask
│   │     └── 3/ #Temporal-3 cloud mask
│   └── gt/ 
│         ├── 1/ #Temporal-1 ground truth
│         ├── 2/ #Temporal-2 ground truth
│         └── 3/ #Temporal-3 ground truth
└── test/
    ├── mask/   
    │     ├── 1/ #Temporal-1 cloud mask
    │     ├── 2/ #Temporal-2 cloud mask
    │     └── 3/ #Temporal-3 cloud mask
    └── gt/ 
          ├── 1/ #Temporal-1 ground truth
          ├── 2/ #Temporal-2 ground truth
          └── 3/ #Temporal-3 ground truth
```
Training
Configure parameters in config.yaml and run:

```bash
python train.py
```
Inference
For cloud removal on test images:

```bash
python test.py
```

## Results

### Qualitative Comparison
![ACA-Net Compair](./figures/compair.png)
*Figure 2: Cloud removal comparison with SOTA methods*

### Quantitative Evaluation
 Quantitative Comparison of Different Models on 300 Test Images

| Model               | PSNR-T1 | PSNR-T2 | PSNR-T3 | SSIM-T1 | SSIM-T2 | SSIM-T3 | GFlops | Params(M) |
|---------------------|---------|---------|---------|---------|---------|---------|--------|-----------|
| STSCNN              | 37.72   | 40.85   | 42.04   | 0.9549  | 0.9777  | 0.9756  | 4.84   | 0.30      |
| PSTCR               | 31.56   | 36.22   | 36.61   | 0.9132  | 0.9532  | 0.9600  | 95.75  | 0.37      |
| PMAA*               | 34.50   | 34.50   | 34.50   | 0.9510  | 0.9510  | 0.9510  | 92.34  | 3.45      |
| DiffCR*             | 34.67   | 34.67   | 34.67   | 0.8794  | 0.8794  | 0.8794  | 45.86  | 22.91     |
| CMSN                | 42.80   | 44.43   | 46.95   | 0.9822  | 0.9495  | 0.9722  | 28.67  | 1.75      |
| **ACA-Net (Ours)**  | **43.44** | **46.88** | **49.23** | **0.9843** | **0.9936** | **0.9943** | 39.73  | 2.43      |

**Note:** Methods marked with (*) use modified single-channel input for fair comparison.
## Citation
```bibtex
@article{
  
}
```
