# RSRT-GD
Official dataset page for RSRT-GD, a road-topology reference dataset for urban remote sensing image geolocation.
# RSRT-GD: Remote Sensing Image to Road Topology Geolocation Dataset

RSRT-GD is a remote sensing image geolocation dataset designed for direct geolocation of urban remote sensing images using lightweight road-vector references. The dataset uses road topology rather than a large-scale reference image database as the geographic control reference.

This repository provides the official dataset description, download instructions, file structure, citation information, license terms, and update records. Source code is not included in this release.

## Dataset Overview

RSRT-GD is designed to support research on remote sensing image geolocation based on lightweight vector reference data. The dataset contains remote sensing image tiles, road-topology masks, road-vector references, metadata, and train/validation/test split files.

The dataset covers ten cities in Henan Province, China, including Zhengzhou, Anyang, Kaifeng, Luoyang, Xinxiang, Xuchang, Pingdingshan, Shangqiu, Xinyang, and Zhumadian.

## Key Features

- A dedicated dataset for urban remote sensing image geolocation using road-vector references.
- Road-vector data are used as lightweight control references instead of reference image databases.
- The dataset supports known-region cross-temporal geolocation and extended study-region geolocation.
- The data include image tiles, road-topology masks, road-vector references, coordinate metadata, and split files.
- The dataset is suitable for studying direct geolocation, vector-guided matching, road-topology constraints, and lightweight geospatial reference construction.

## Dataset Statistics

| Item | Value |
|---|---:|
| Number of cities | 10 |
| Training image tiles | 26,964 |
| Orthophoto tiles in training set | 12,348 |
| GaoFen-7 tiles in training set | 14,616 |
| Validation image tiles | 8,415 |
| Validation anchor regions | 935 |
| Test image tiles | 109,222 |
| GaoFen-7 scenes for test set | 32 |
| Image tile coverage | approximately 637.5 m × 637.5 m |
| Vector reference coverage | 1,964.59 km² |
| Total road length | 18,267.08 km |
| Average road density | 9.30 km/km² |
| Vector data size | 13.55 MB |

## Data Splits

The dataset contains three main subsets.

### Training Set

The training set is constructed from anchor coordinates and corresponding remote sensing image tiles. Positive pairs are formed by pairing image tiles with road-topology masks generated from the same anchor coordinate. Negative pairs are formed by pairing image tiles with masks generated from different anchor coordinates.

### Validation Set

The validation set follows the same construction strategy as the training set. It contains GaoFen-7 image tiles acquired at different times and road-topology masks generated from validation anchor coordinates.

### Test Set

The test set is designed for real geolocation scenarios without precise positional priors. Image tiles are randomly cropped from GaoFen-7 scenes within the urban areas of the ten cities. During testing, candidate coordinate points are generated within the coarse geolocation range and matched against road-vector references.

## Recommended Data Organization

After downloading and extracting the dataset, the recommended structure is:

```text
RSRT-GD/
├── images/
│   ├── train/
│   ├── val/
│   └── test/
├── masks/
│   ├── train/
│   ├── val/
│   └── test/
├── vectors/
│   └── osm_roads/
├── metadata/
│   ├── train_metadata.csv
│   ├── val_metadata.csv
│   └── test_metadata.csv
├── splits/
│   ├── train.txt
│   ├── val.txt
│   └── test.txt
└── README.txt
