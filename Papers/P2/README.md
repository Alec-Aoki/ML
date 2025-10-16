# Addressing Class Overlap under Imbalanced Distribution: An Improved Method and Two Metrics
## Existing Overlap Metrics
To estimate the level of class overlap, there are two metrics, the $R$ value and the $R_{aug}$ value. 

### Notations
- $N$: number of samples
- $n$: number of classes
- $C_l$: set of samples belonging to class $l$, $l \in [1,n]$
- $U$: set of all samples, $U = C_1 \cup ... \cup C_i \cup ... \cup C_n$
- $x_i^l$: the $i$-th sample of $C_l$
- $k-NN(x_i^l, U - C_l)$: the set of samples in $k$-nearest nighbor samples of $x_i^l$ that belong to the class different from $C_l$
- $\lambda(z)$: a 0-1 function that returns $1$ whn $z \gt 0$ and returns $0$ otherwise
- $\theta$: a treshold value within the range $[0, k/2]$

### $R$ Value
It's based on the assumption that a sample from class $C_l$ is overlapped with other samples if the number of samples that is in its $k$ nearest neighbors and also belong to a class rather than $C_l$ is at least $\theta + 1$.

The $R$ value can be considered as the ratio of samples in the overlapping area. The range of the $R$ value is $[0, 1]$. 

### $R_{aug}$ Value
The $R$ value on some imbalanced data sets with different imbalanced ratios showed that its value is almost constant, while the classification performance decreases with a larger imbalance ratio.

The $R_{aug}$ value is dominated by the $R$ value of the minority class for datasets with large *IR*, and it is equal to $R$ value for balanced datasets.

### Proposed Metric
The $k$ used for nearest-neighbor overlap detection should not be uniform across classes in an imbalanced setting.

In the traditional $R$ method, the same 
$k$ is used for all samples regardless of class. But in an imbalanced dataset, the “density” of neighbors differs across classes (many more majority samples), which skews overlap detection.

A class-dependent $k$ value is proposed, specifically $k_{minority} = ⌈\frac{k}{\text{IR}}⌉$ where IR = imbalance ratio (majority count ÷ minority count). 

Thus, for minority class samples, one uses a smaller $k$ (proportionally) to decide overlap. 

This adjustment helps to balance the “reach” of neighborhoods across classes, so that minority-class samples are not unfairly forced into overlap just because they are sparse.