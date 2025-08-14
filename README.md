# Gold Mineral Prospectivity Mapping

This repository contains code for **gold mineral prospectivity mapping** using multiple machine learning models. The workflow includes data preprocessing, model training, evaluation, and prospectivity map generation.  
The models implemented include:
- **Fuzzy-kernel Extreme Learning Machine (FKELM)**
- **Wasserstein GAN with Gradient Penalty + CNN (WGAN-GP_CNN)**
- **Raw Convolutional Neural Network (RCNN)**
- **Support Vector Machines (SVM)**
- **Gradient Boosting (GB)**

## Project Structure
```
Gold_mineral_prospectivity_mapping.ipynb  # Main Jupyter Notebook
gold_mineral_prospectivity_mapping.py     # Python script version of the notebook
```

## Models Overview
### 1. **FKELM**
- Uses fuzzy-kernel functions with type-2 fuzzy sets and Hamacher conorms.
- Trains an Extreme Learning Machine with kernel transformation.
- Outputs **fkelm_prospectivity_map.csv**.

### 2. **WGAN-GP + CNN**
- Generates synthetic geological data using a Wasserstein GAN with Gradient Penalty.
- Trains a CNN classifier with both real and generated samples.
- Outputs **Wgangpcnn_prospectivity_map.csv**.

### 3. **Raw CNN**
- Directly trains a CNN on scaled geochemical features.
- Outputs **cnn_prospectivity_map.csv**.

### 4. **SVM**
- Trains an RBF-kernel Support Vector Machine with noisy features.
- Outputs **svm_prospectivity_map.csv**.

### 5. **Gradient Boosting**
- Uses `sklearn.ensemble.GradientBoostingClassifier` for classification.
- Applies post-prediction boosting and bias adjustment.
- Outputs **gb_prospectivity_map.csv**.

## Input Data
The models require:
- `positive_samples.csv` – Known mineralized locations with geochemical features.
- `negative_samples.csv` – Non-mineralized locations.
  
Both files should include:
- Latitude, Longitude
- Geochemical features: `Cu`, `Pb`, `Zn`, `Ni`, `Co`, `Sb`, `As`, `Ag`, `Au`

## Output
Each model produces:
- **Prospectivity probability map** (`*_prospectivity_map.csv`) with:
  - Latitude
  - Longitude
  - Prospectivity probability

## Requirements
```bash
pip install numpy pandas matplotlib scikit-learn torch torchvision h5py
```

## ▶Usage
Run the script:
```bash
python gold_mineral_prospectivity_mapping.py
```
Or open the notebook:
```bash
jupyter notebook Gold_mineral_prospectivity_mapping.ipynb
```

## Visualization
Each model outputs ROC curves showing classification performance.  
Generated maps can be visualized in GIS software for spatial analysis.

