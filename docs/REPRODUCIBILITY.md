# Reproducibility

## Training Protocol

The manuscript reports the following shared protocol for all compared methods:

- Framework: PyTorch
- Image size: 256x256
- Split: train/validation/test = 8:1:1
- Seed: 3407
- Optimizer: AdamW
- Initial learning rate: 3e-4
- Batch size: 8
- Weight decay: 1e-4
- Loss: Dice loss + cross-entropy loss with equal weights
- Hardware: NVIDIA RTX 3090 GPU

## Evaluation Metrics

Dice and IoU are used as the main segmentation metrics. The reported comparison table also includes Wilcoxon signed-rank p-values between each competing method and DAMA-Net.

## Fair Comparison

All compared methods are re-implemented and trained under identical experimental settings. This keeps the comparison focused on the architecture differences rather than on training protocol variation.
