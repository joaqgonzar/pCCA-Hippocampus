# pCCA-Hippocampus
Codes and Examples to apply partial canonical correlation analysis (pCCA) on neuronal population recordings. 
Papers applying this code: (doi:10.64898/2025.12.31.697203).

Examples \& Tutorials:
Four  notebooks are provided showing: 1) how to load data from the hippocampal-neocortical DANDI set on a local machine; 2) how to load data from the hippocampal-neocortical DANDI set on a colab notebook straight from DANDI server; 3) how to run pCCA on a simple Poisson spiking network (colab notebook); 4) how to run pCCA on real spiking data collected from CA3-CA1-RSC areas during novel maze learning on mice (jupyter notebook to be run locally).
All recordings can be downloaded from: 
https://dandiarchive.org/dandiset/001695/draft

Installation
```
pip install partial_CCA
```
Quick Start
The PartialCCA class follows the standard scikit-learn API (fit, transform, score).

Usage in Python:
```
import numpy as np
from partial_CCA import PartialCCA

# Generate dummy data: 100 samples, 20 neurons in X, 15 in Y, 5 in Z
X = np.random.randn(100, 20)
Y = np.random.randn(100, 15)
Z = np.random.randn(100, 5)

# Initialize and fit the model
model = PartialCCA()
model.fit(X, Y, Z)

# Transform data into canonical components
proj_x, proj_y = model.transform(X, Y)

# Get canonical correlations
print(model.canonical_correlations_)
```
Features:
If no variable Z is provided, the model automatically defaults to standard Canonical Correlation Analysis (CCA).
Statistical Validation: Includes a surrogate\_test method that uses circular shifting to calculate p-values for the observed correlations.

Authors:
Joaquin Gonzalez (https://scholar.google.com/citations?user=rcGEkDgAAAAJ&hl=en).
Postdoc, Buzsaki Lab (https://buzsakilab.com/wp/) and Chen Lab (https://cn3laboratory.org/pi.html).
New York University
