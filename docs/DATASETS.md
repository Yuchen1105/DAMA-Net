# Datasets

The manuscript evaluates DAMA-Net on four public polyp segmentation datasets:

- CVC-300
- CVC-ClinicDB
- ETIS
- Kvasir-SEG

Expected folder layout:

```text
data/
  CVC-300/
    images/
    masks/
  CVC-ClinicDB/
    images/
    masks/
  ETIS/
    images/
    masks/
  Kvasir-SEG/
    images/
    masks/
```

For fair comparison, images are resized to 256x256 and each dataset is split into training, validation, and test subsets using an 8:1:1 ratio with seed 3407.

Dataset files are not included in this repository. Please download them from their official release pages and keep the original license terms.
