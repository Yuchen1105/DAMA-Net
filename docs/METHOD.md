# Method

DAMA-Net addresses polyp segmentation by coordinating local structure modeling and long-range contextual modeling in an efficient U-shaped network.

## Overall Architecture

The network uses a lightweight stem, four hierarchical DFF encoder stages, one MA bottleneck block, and a decoder with skip connections. The channel dimensions are 32, 64, 128, 256, and 512.

## Discrepancy-Aware Feature Fusion Encoder

The DFF encoder contains two branches:

- A local branch using depthwise and pointwise convolution to preserve fine-grained spatial details.
- A contextual branch using convolution followed by bidirectional RWKV-style sequence mixing to model long-range dependencies.

The absolute difference between the two branches estimates local-global discrepancy. This discrepancy produces adaptive weights that fuse local and contextual features. The fused representation is refined by 3x3 and 5x5 depthwise convolution branches with spatial and channel recalibration.

## Multi-Scale Aggregation Block

The MA block is placed at the bottleneck. It uses three branches:

- 1x7 followed by 7x1 depthwise convolution.
- 5x5 depthwise convolution.
- 1x11 followed by 11x1 depthwise convolution.

Adaptive scale weighting recalibrates the multi-scale branches, and a second context weighting stage refines the aggregated bottleneck feature before decoding.

## Why the Two Modules Fit Together

DFF handles the mismatch between local boundary/detail cues and global contextual responses in the encoder. MA then works on the deepest semantic feature, where the model needs broader receptive fields to recognize polyps with different scales and appearances. Together, they form a coherent local-global and multi-scale modeling story: DFF decides how to fuse complementary representations, while MA decides how to aggregate context at the semantic bottleneck.
