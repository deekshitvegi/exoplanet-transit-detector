
# Exoplanet Transit Detector

This project focuses on detecting exoplanet transits using deep learning techniques. The workflow includes:
- Simulating light curves for exoplanet transits, no transits, and false positives
- Training a Transformer Encoder model and a Logistic Regression baseline
- Comparing their performances on a test set
- Visualizing results like UMAP clustering, confusion matrices, and orbit simulation

## Dataset
Instead of using real telescope datasets (which can be noisy, incomplete, and too small), we generate synthetic data that mimics real astronomical light curves:
- **Transit**: a planet passes in front of a star, causing a drop in flux
- **No Transit**: flat flux with only noise
- **False Positive**: a flux drop that does not correspond to a real planet (e.g., noise spike)

Each light curve contains 1000 flux measurements over 30 days.

---

## Models
- **Baseline Model**: Logistic Regression trained on scaled flux values
- **Transformer Encoder Model**: Deep learning model trained to classify light curves and predict physical parameters (radius, period, duration)

---

## Training
- 150,000 light curves were generated
- 80/20 stratified train/test split
- Training involved EarlyStopping and Learning Rate Scheduling
- Focal Loss used for classification to handle slight class imbalance

---

## Results
| Model | Accuracy | F1 Score (Macro Avg) |
|:-----:|:--------:|:--------------------:|
| Logistic Regression (Baseline) | 78.6% | 78.5% |
| Transformer Encoder | 73.9% | 74.0% |

---

## Visualizations
- Light Curve Examples
- Training Curves (Accuracy and Loss over Epochs)
- Confusion Matrices
- ROC Curves
- UMAP Projection
- 3D Exoplanet Orbit Simulation

---

## Deployment
A Gradio App allows users to upload a CSV of flux points and get predictions:
- Transit
- No Transit
- False Positive
- 3D orbit visualization based on predicted radius and period

---

## Setup Instructions

1. Clone the repository:
```bash
git clone https://github.com/yourusername/exoplanet-transit-detector.git
cd exoplanet-transit-detector
```

2. Open and run the notebook or deploy the Gradio app.

---

## License
This project is licensed under the **MIT License** — free to use, modify, and share with proper attribution.
