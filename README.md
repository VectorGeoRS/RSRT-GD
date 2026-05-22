# RSRT-GD: Remote Sensing Image to Road Topology Geolocation Dataset

RSRT-GD (Remote Sensing Image to Road Topology Geolocation Dataset) is a dataset designed for direct geolocation of urban remote sensing images. Instead of relying on large-scale reference image databases, the dataset uses road vector data as a lightweight geographic reference. It is intended to support research on remote sensing image geolocation based on road-topology constraints and vector references.

This repository is the official documentation page for the RSRT-GD dataset. It provides an overview of the dataset, data structure, download instructions, citation information, license terms, and update records. Source code is not included in this release.

## Dataset Overview

Remote sensing image geolocation aims to recover the geographic coordinates of an input remote sensing image when precise location priors are unavailable. Existing reference-image retrieval methods usually require the construction of large-scale reference image databases, which leads to high costs in data acquisition, storage, and maintenance. RSRT-GD uses road vector data as the control reference and provides spatial constraints for urban remote sensing image geolocation through road topology. This design reduces the storage cost of reference data and supports more lightweight geolocation research.

RSRT-GD covers urban areas in ten cities of Henan Province, China, including Zhengzhou, Anyang, Kaifeng, Luoyang, Xinxiang, Xuchang, Pingdingshan, Shangqiu, Xinyang, and Zhumadian. The dataset contains remote sensing image tiles, anchor coordinates, vector references, and corresponding metadata files. Road-topology masks are not released as pre-generated files. Instead, users can dynamically clip and rasterize them from the vector reference according to anchor coordinates or candidate coordinates.

## Key Features

- The first remote sensing image geolocation dataset that uses road vectors as reference data.
- Supports research on direct geolocation of urban remote sensing images based on lightweight vector references.
- Covers urban areas in ten cities of Henan Province and includes remote sensing images acquired across multiple time phases, seasons, and imaging conditions.
- Supports dynamic generation of road-topology masks from road vector references, facilitating the study of correspondences between image features and road structures.
- Supports experimental settings such as cross-temporal geolocation in known regions and geolocation in extended study regions.
- Compared with a reference image database covering the same area, the road vector reference has lower storage cost and better dynamic generation capability.

## Dataset Composition

RSRT-GD mainly consists of a training set, a validation set, and a test set.

### Training and Validation Sets

Both the training set and the validation set are constructed using controlled sampling based on anchor coordinates. The dataset provides remote sensing image tiles, corresponding anchor coordinates, and a unified vector reference.

These subsets are mainly used for model training, parameter selection, and performance validation. Researchers can set the clipping range, road width, and rasterization resolution according to their experimental requirements to generate road-topology masks corresponding to the image tiles.

### Test Set

The test set is constructed for realistic geolocation scenarios where precise location priors are unavailable. It also provides only remote sensing image tiles, anchor coordinates, and the vector reference. The anchor coordinates are mainly used for result evaluation and should not be used as prior inputs during model geolocation.

## Data Description

The core data of RSRT-GD consists of remote sensing image tiles, anchor coordinates, and the vector reference. Road-topology masks are intermediate data dynamically generated from the vector reference and are not released as independent data files. This design reduces redundant data storage and allows researchers to flexibly generate road-topology representations under different experimental settings.

## Recommended Directory Structure

After downloading and extracting the dataset, the recommended data organization is as follows:

```text
RSRT-GD/
├── train/
│   ├── images/
│   └── anchors.csv
├── val/
│   ├── images/
│   └── anchors.csv
├── test/
│   ├── images/
│   └── anchors.csv
├── vector_reference/
│   ├── vector_reference.shp
│   ├── vector_reference.shx
│   ├── vector_reference.dbf
│   ├── vector_reference.prj
│   └── rasterization_config.json
├── auxiliary_structure_data/
│   ├── images/
│   ├── road_masks/
└── README.md
```

The actual file structure may be adjusted in the official release. Please refer to the download page and the documentation files included in the data package.

## Download

The RSRT-GD dataset will be released through cloud storage. The GitHub repository serves only as the dataset homepage and download entry and does not directly host the full data files.

Official download links:

- Baidu Netdisk: To be released upon paper acceptance
- Google Drive: To be released upon paper acceptance

Dataset DOI: To be released upon paper acceptance

The associated paper is still under submission or review, so the download links are not publicly available yet. After the official release, this page will be updated with the dataset download links, DOI, and citation format.

## Usage

When using RSRT-GD, please select the appropriate data split according to your research task.

For training and validation experiments, the image tiles, anchor coordinates, and vector reference provided in the training and validation sets can be used. Road-topology masks can be generated from the vector reference according to the required clipping range, road width, and rasterization resolution. For test experiments, it is recommended to follow the experimental settings described in the paper, generate candidate coordinate points within the test region, and use the road vector reference to generate road-topology masks for candidate locations.

Researchers can use RSRT-GD to study the following topics:

- Direct geolocation of remote sensing images
- Image geolocation based on road-topology constraints
- Cross-modal matching between images and vector data
- Construction of lightweight geographic reference data
- Cross-temporal geolocation of urban remote sensing images
- Geolocation methods based on public vector data such as OpenStreetMap

## License and Usage Restrictions

RSRT-GD is provided for academic research purposes only. Users should comply with the dataset license agreement and the relevant regulations of the original data sources when using this dataset.

Remote sensing image tiles may only be used for academic research within the scope permitted by the data provider. Without explicit authorization from the data provider or dataset maintainers, the remote sensing image tiles may not be used for commercial purposes or redistributed.

The road vector data are derived from OpenStreetMap. Users should comply with the relevant OpenStreetMap license terms.

Any papers, reports, or public results that use RSRT-GD should cite this dataset and its associated paper.

The citation format will be updated after the associated paper is officially published.

## Version History

### v1.0.0

Initial release. This version provides the RSRT-GD dataset description, data structure, download instructions, citation information, and license statement.

## Disclaimer

This repository only provides the official documentation and download guidance for the RSRT-GD dataset and does not include source code. The dataset is provided as is, and the maintainers are not responsible for any issues caused by improper use of the dataset.
