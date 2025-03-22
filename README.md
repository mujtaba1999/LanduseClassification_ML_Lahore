# LanduseClassification_ML_Lahore
This project classifies built-up areas in Lahore using Sentinel-2 imagery and machine learning (SVM &amp; Random Forest) in Google Earth Engine. Optimized through hyperparameter tuning, it assesses urban expansion, and compares classifier performance. The classified images are exported for further GIS analysis.

# Built-Up Area Classification using SVM and Random Forest in Google Earth Engine

## Overview
This project classifies built-up areas in Lahore, Pakistan, using Sentinel-2 satellite imagery and machine learning models (SVM & Random Forest) in Google Earth Engine. The classification is optimized through hyperparameter tuning, and results include urban expansion insights and Green-Built Ratio Index (GBRI) calculations.

## Dataset
- **Satellite Imagery:** Sentinel-2 (COPERNICUS/S2) from 2020
- **Bands Used:** B2, B3, B4, B8, B11, B12, and Normalized Difference Built-Up Index (NDBI)
- **Training Data:** Manually labeled points (built-up and non-built-up)
- **Region of Interest:** Lahore, Pakistan

## Methodology
1. **Preprocessing:** Filtering Sentinel-2 images for 2020 with <10% cloud cover.
2. **Feature Extraction:** Computing NDBI for built-up area enhancement.
3. **Training Data Preparation:** Importing labeled shapefiles and assigning class labels.
4. **Model Training:**
   - **SVM:** Tuning kernel type and cost parameters.
   - **Random Forest:** Adjusting tree count, minimum leaf population, variable split, and max nodes.
5. **Validation & Accuracy Assessment:** Evaluating classifiers with overall accuracy, confusion matrices, and kappa coefficients.
6. **Final Classification:** Applying the best-performing model to the entire image.
7. **Exporting Results:** Saving classified images to Google Drive for further analysis.

## Implementation
### Prerequisites
- Google Earth Engine account
- Sentinel-2 data and labeled training points
- Basic JavaScript and remote sensing knowledge

### Running the Code
#### **SVM Classification**
- **Code:** [Google Earth Engine SVM Script](https://code.earthengine.google.com/5440df2ec13ad85a5695d0ce9d95660c)
- Steps:
  1. Load Sentinel-2 data and filter by AOI.
  2. Compute NDBI and add it to the dataset.
  3. Train an SVM classifier with different kernel types and cost values.
  4. Select the best model based on validation accuracy.
  5. Apply and evaluate the trained classifier.
  6. Export results.

#### **Random Forest Classification**
- **Code:** [Google Earth Engine RF Script](https://code.earthengine.google.com/b0bac074e6591bdd7019194c6cd08e1a)
- Steps:
  1. Load and preprocess Sentinel-2 data.
  2. Compute NDBI and integrate it with the dataset.
  3. Train an RF classifier with various hyperparameter settings.
  4. Choose the best model based on validation accuracy.
  5. Apply and evaluate the final model.
  6. Export results.

## Results
| Classifier     | Best Parameters                           | Accuracy | Kappa  |
|--------------|---------------------------------|---------|--------|
| **SVM**       | Kernel: Linear, Cost: 100            | 80.11%  | 0.57   |
| **Random Forest** | Trees: 10, Min Leaf: 5, Vars per Split: sqrt, Max Nodes: 10 | 90.24%  | 0.77   |

### Additional Findings
- **Green-Built Ratio Index (GBRI):**
  - Vegetation Area: 401,400 m²
  - Built-Up Area: 232,200 m²
  - GBRI: 1.7287
- **Hyperparameter Optimization:**
  - Best RF Parameters: `n_estimators: 4000, min_samples_split: 5, min_samples_leaf: 1, max_depth: 10, criterion: entropy`
  - Cross-Validation Score: 62%
  - Test Accuracy: 62%
- **Class Weights & SVM Performance:**
  - Higher misclassification in barren land & water classes due to imbalance.
  - Assigning higher weights to underrepresented classes improved balance.

## Visualization
- **SVM Classification:** White (Non-Built-Up), Red (Built-Up)
- **Random Forest Classification:** Green (Non-Built-Up), Red (Built-Up)

## Exported Results
Classified images are saved to Google Drive in `EarthEngineExports` for further GIS analysis.

## Future Improvements
- Adding spectral indices like NDVI and MNDWI.
- Using deep learning models for better accuracy.
- Expanding study area to analyze urbanization trends in other cities.

## Contributors
- **Mujtaba Qasim**  
  S.No: 3194922  
  Group No: 4

## License
This project is open-source and available under the MIT License.

