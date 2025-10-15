# Basic Concepts
Source: https://medium.com/@souvikp663/classification-problems-class-imbalance-class-overlap-and-noise-c422149f522b

**Class imbalance**: occurs when the number of data points in one class is much greater than the number of data points in another class. This can be a problem for classification algorithms because they may be biased towards the majority class.

There are a number of ways to handle class imbalance, including:
- *Undersampling*: This involves randomly removing data points from the majority class until the class distribution is more balanced.
- *Oversampling*: This involves creating synthetic data points for the minority class until the class distribution is more balanced.
- *Cost-sensitive learning*: This involves training the classification algorithm with different costs for different classes. This can help to bias the algorithm towards the minority class.

**Class overlap**: occurs when there is ambiguity between two or more classes. These samples
are called overlapping samples for they usually reside in overlapping regions in the feature space. This can also be a problem for classification algorithms because they may make incorrect predictions for data points that fall near the class boundary.

There are a number of ways to handle class overlap, including:
- *Feature engineering*: This involves creating new features that are more discriminative between the different classes.
- *Ensemble learning*: This involves training a number of different classification algorithms and combining their predictions.
- *Active learning*: This involves querying the user for labels on difficult data points.

**Noise**: refers to data points that are incorrectly labeled or that do not belong to any class. Noise can also degrade the performance of classification algorithms.

There are a number of ways to handle noise, including:
- *Data cleaning*: This involves identifying and removing noisy data points from the training dataset.
- *Regularization*: This involves adding a penalty to the classification algorithm for making complex predictions. This can help to prevent the algorithm from overfitting to the noisy data.
- *Robust learning*: This involves training the classification algorithm on data that is similar to the production data, including noise.