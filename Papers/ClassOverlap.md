# Classification with Class Overlapping
## Basic Concepts
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

## Classiﬁcation with Class Overlapping: A Systematic Study
Class overlapping combined with class imbalance. Five widely used classiﬁers and three overlapping-class modeling schemes were employed for the comparative study. Results found:
1. The *separating* scheme is the best among the other two (*discarding* and *merging*) to model the data set with class overlapping;
2. The distance-based classifiers are more sensitive than the rule-based ones on the class overlapping problem;
3. As the class imbalance ratio increases, the separating scheme showed higher improvements to the classification perfomance (in particular for the well-known SVMs).

### SVM x SVDD
The objective of Support Vector Data Description (SVDD) is to find a sphere or domain with minimum volume containing all or most of the data by minimizing the radius of the sphere with the constraint that the distance between a center and data is smaller than the radius.

Support vectors define the boundary of training data. So, SVDD can be used to find overlapping region. The data dropped in both two spheres can be thought as the overlapping data which is close to or overlaps with each other.

### Schemes for dealing with class overlapping problem
Schemes for dealing with class overlapping problem, which can be divided into two strategies. One is to merge the overlapping classes into a meta-class and ignore the boundary between these classes. The other is to separate the overlapping classes by refining the classification boundary in the feature space.

**The discarding scheme**: this scheme ignores the data in overlapping regions and learns on the data in non-overlapping region. Each test data will be tested on the model learned by this scheme.

**The merging scheme**: this scheme merges the data from overlapping regions as new class, labeled "overlapping". Then the model focuses on the whole data with the "overlapping" class added, and another model is trained for the data in the overlapping region. Each test data will be firstly tested on the first model. If it is classified as "overlapping", it will be tested on the second model to determine its original class.

**The separating scheme**: this scheme learns on data in overlapping and non-overlapping regions separately. It gets two models. One is the model of the data in overlapping region, and the other is the model of the data in the non-overlapping region. Each test data will be tested on the model
which is determined by that if the test data is lying on non-overlapping re-
gions or overlapping regions.

As the value of overlapping ratio increases, the *separating* scheme performs much better than the *discarding* scheme and the performance gap is broad. This is because ignoring this data may lose some important information of each two classes. If the overlapping ratio is high, more information will be discarded to bring lower F-measure.

The five classifiers can be divided into two types. *C4.5* and *RIPPER* are rule-based classifiers. *NB*, *k-NN* and *SVMs* are distance-based classifiers. The distance-based classifiers are more sensitive than the rule-based ones to the class overlapping problem.

As the degree of class imbalance increases, the separating scheme showed higher improvements to the classification performance, in particular for the well-known SVMs.

## Addressing Class Overlap under Imbalanced Distribution: An Improved Method and Two Metrics
### Existing Overlap Metrics
To estimate the level of class overlap, there are two metrics, the $R$ value and the $R_{aug}$ value. 

#### Notations
- $N$: number of samples
- $n$: number of classes
- $C_l$: set of samples belonging to class $l$, $l \in [1,n]$
- $U$: set of all samples, $U = C_1 \cup ... \cup C_i \cup ... \cup C_n$
- $x_i^l$: the $i$-th sample of $C_l$
- $k-NN(x_i^l, U - C_l)$: the set of samples in $k$-nearest nighbor samples of $x_i^l$ that belong to the class different from $C_l$
- $\lambda(z)$: a 0-1 function that returns $1$ whn $z \gt 0$ and returns $0$ otherwise
- $\theta$: a treshold value within the range $[0, k/2]$

#### $R$ Value
It's based on the assumption that a sample from class $C_l$ is overlapped with other samples if the number of samples that is in its $k$ nearest neighbors and also belong to a class rather than $C_l$ is at least $\theta + 1$.

The $R$ value can be considered as the ratio of samples in the overlapping area. The range of the $R$ value is $[0, 1]$. 

#### $R_{aug}$ Value
The $R$ value on some imbalanced data sets with different imbalanced ratios showed that its value is almost constant, while the classification performance decreases with a larger imbalance ratio.

The $R_{aug}$ value is dominated by the $R$ value of the minority class for datasets with large *IR*, and it is equal to $R$ value for balanced datasets.

#### Proposed Metric
The $k$ used for nearest-neighbor overlap detection should not be uniform across classes in an imbalanced setting.

In the traditional $R$ method, the same 
$k$ is used for all samples regardless of class. But in an imbalanced dataset, the “density” of neighbors differs across classes (many more majority samples), which skews overlap detection.

A class-dependent $k$ value is proposed, specifically $k_{minority} = ⌈\frac{k}{\text{IR}}⌉$ where IR = imbalance ratio (majority count ÷ minority count). 

Thus, for minority class samples, one uses a smaller $k$ (proportionally) to decide overlap. 

This adjustment helps to balance the “reach” of neighborhoods across classes, so that minority-class samples are not unfairly forced into overlap just because they are sparse.

## Analysing the Footprint of Classifiers in Overlapped and Imbalanced Contexts
