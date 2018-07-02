<p align="center">
  <img width="150" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/documentation/Latex/Documentation/images/logo.png"/>
</p>

# SNV Classifier
Project for the bioinformatics course of professor Valentini, Unimi.

<p align="center">
  <img src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/results.png"/>
</p>

## Documentation
The documentation of the project is available [here](https://github.com/LucaCappelletti94/snv_classifier/blob/master/documentation/Latex/Documentation/main.pdf) and shows an analysis and visualizations of the datasets, modelling of the network and results.

## Doubts over obtained results
Some doubts have been raised by the extremely quick "overfitting" on the test set when using simple networks, such as a 2 layer with 3 neurons each. This is probably motivated (experimental proof in the PCA notebook) by the distribution of the test set that does not reflect the distribution of the train set, but is actually extremely more easily separable.

<p align="center">
  <img src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/documentation/Latex/Documentation/images/doubts.png"/>
</p>

## Batch of neural networks
To verify if 36/40 is the maximum of precision that a common neural network an reach over the given dataset I have trained 136 networks with a gradient of architectures for 100 generations each.

All the trained models and weights are available [here](https://github.com/LucaCappelletti94/snv_classifier/tree/master/meta_networks).

### Errors and issues with this approach
- Deeper networks need more epochs to converge.
- I **forgot** to reset the random seed for each network, so the networs start from different random weights. I will retrain the networks resetting the seeds as soon as I get the time.

<p align="center">
  <img alt="Meta Training Confusion" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/meta%20training/Meta%20Testing%20Confusion.png"/>
  <img alt="Meta Testing Confusion" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/meta%20training/Meta%20Training%20Confusion.png"/>
  <img alt="Meta Training Auroc" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/meta%20training/Meta%20Testing%20Auroc.png"/>
  <img alt="Meta Testing Auroc" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/meta%20training/Meta%20Training%20Auroc.png"/>
  <img alt="Meta Training AuPRC" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/meta%20training/Meta%20Testing%20Auprc.png"/>
  <img alt="Meta Testing AuPRC" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/meta%20training/Meta%20Training%20Auprc.png"/>
</p>


## Jupyter Notebooks
Various jupyter notebooks with explanations are available:

### Keras neural network
A jupyter notebook implementing the [project neural network](https://github.com/LucaCappelletti94/snv_classifier/blob/master/documentation/Latex/Documentation/images/network.png) in keras is available [here](https://github.com/LucaCappelletti94/snv_classifier/blob/master/Bioinformatica%20-%20Keras.ipynb).

<img width="300" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/documentation/Latex/Documentation/images/network.png?raw=true"/>

#### Network trained model usage example
A jupyter notebook implementing a usage example of the trained model is available [here](https://github.com/LucaCappelletti94/snv_classifier/blob/master/Bioinformatica%20-%20Loading%20saved%20model.ipynb) or just below here:

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-
import numpy as np
from keras.models import load_model

def number_to_class(value):
    """Map class identifier to class name."""

    if value:
        return 'Positive'
    return 'Negative'

EXAMPLE_DATASET = 'Mendelian.normalized.example.test.tsv'

model = load_model('model.h5')
model.load_weights('weights.h5')
data_points = np.loadtxt(EXAMPLE_DATASET, delimiter='\t')

for prediction in model.predict_classes(data_points):
    print 'I believe %s to be %s' % (number_to_class(1),
            number_to_class(prediction))

"""
  I believe Positive to be Positive
  I believe Positive to be Positive
  I believe Positive to be Positive
  I believe Positive to be Positive
  I believe Positive to be Positive
  I believe Positive to be Positive
  I believe Positive to be Negative
  I believe Positive to be Positive
  I believe Positive to be Positive
  I believe Positive to be Negative
"""
```

### Scatter plot
A jupyter notebook generating a [scatter plot](https://github.com/LucaCappelletti94/snv_classifier/blob/master/scatter_plot.png?raw=true) from the dataset is available [here](https://github.com/LucaCappelletti94/snv_classifier/blob/master/Bioinformatica%20-%20Scatter%20plot.ipynb).

<img width="300" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/scatter_plot.png?raw=true"/>


### Correlation matrices
A jupyter notebook generating a [correlation matrix](https://github.com/LucaCappelletti94/snv_classifier/blob/master/correlation_matrix.png?raw=true) from the dataset is available [here](https://github.com/LucaCappelletti94/snv_classifier/blob/master/Bioinformatica%20-%20Correlation.ipynb).

<img width="300" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/correlation_matrix.png?raw=true"/>


### PCA
A jupyter notebook generating [PCA 2D visualization](https://github.com/LucaCappelletti94/snv_classifier/tree/master/documentation/Latex/Documentation/images/pca) of the dataset is available [here](https://github.com/LucaCappelletti94/snv_classifier/blob/master/Bioinformatica%20-%20PCA.ipynb).

<img width="300" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/documentation/Latex/Documentation/images/pca/training.png?raw=true"/>


### TSNE
A jupyter notebook generating [TSNE 2D visualization](https://github.com/LucaCappelletti94/snv_classifier/tree/master/documentation/Latex/Documentation/images/tsne) of the dataset is available [here](https://github.com/LucaCappelletti94/snv_classifier/blob/master/Bioinformatica%20-%20TSNE.ipynb).

<img width="300" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/documentation/Latex/Documentation/images/tsne/testing.png?raw=true"/>


### Dataset plots
A jupyter notebook generating [dataset plots](https://github.com/LucaCappelletti94/snv_classifier/tree/master/documentation/Latex/Documentation/images/plot) is available [here](https://github.com/LucaCappelletti94/snv_classifier/blob/master/Bioinformatica%20-%20Metrics%20plots.ipynb).

<img width="300" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/documentation/Latex/Documentation/images/plot/CpGobsExp.png?raw=true"/>


### Dataset distributions
A jupyter notebook generating [dataset distributions](https://github.com/LucaCappelletti94/snv_classifier/tree/master/documentation/Latex/Documentation/images/distributions) is available [here](https://github.com/LucaCappelletti94/snv_classifier/blob/master/Bioinformatica%20-%20Metric%20distributions.ipynb).

<img width="300" src="https://github.com/LucaCappelletti94/snv_classifier/blob/master/documentation/Latex/Documentation/images/distributions/CpGperCpG.png?raw=true"/>
