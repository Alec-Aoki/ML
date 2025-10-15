# Classiﬁcation with Class Overlapping: A Systematic Study
Class overlapping combined with class imbalance. Five widely used classiﬁers and three overlapping-class modeling schemes were employed for the comparative study. Results found:
1. The *separating* scheme is the best among the other two (*discarding* and *merging*) to model the data set with class overlapping;
2. The distance-based classifiers are more sensitive than the rule-based ones on the class overlapping problem;
3. As the class imbalance ratio increases, the separating scheme showed higher improvements to the classification perfomance (in particular for the well-known SVMs).

## SVM x SVDD
The objective of Support Vector Data Description (SVDD) is to find a sphere or domain with minimum volume containing all or most of the data by minimizing the radius of the sphere with the constraint that the distance between a center and data is smaller than the radius.

Support vectors define the boundary of training data. So, SVDD can be used to find overlapping region. The data dropped in both two spheres can be thought as the overlapping data which is close to or overlaps with each other.

## Schemes for dealing with class overlapping problem
Schemes for dealing with class overlapping problem, which can be divided into two strategies. One is to merge the overlapping classes into a meta-class and ignore the boundary between these classes. The other is to separate the overlapping classes by refining the classification boundary in the feature space.

**The discarding scheme**: this scheme ignores the data in overlapping regions and learns on the data in non-overlapping region. Each test data will be tested on the model learned by this scheme.

**The merging scheme**: this scheme merges the data from overlapping regions as new class, labeled "overlapping". Then the model focuses on the whole data with the "overlapping" class added, and another model is trained for the data in the overlapping region. Each test data will be firstly tested on the first model. If it is classified as "overlapping", it will be tested on the second model to determine its original class.

**The separating scheme**: this scheme learns on data in overlapping and non-overlapping regions separately. It gets two models. One is the model of the data in overlapping region, and the other is the model of the data in the non-overlapping region. Each test data will be tested on the model
which is determined by that if the test data is lying on non-overlapping re-
gions or overlapping regions.

As the value of overlapping ratio increases, the *separating* scheme performs much better than the *discarding* scheme and the performance gap is broad. This is because ignoring this data may lose some important information of each two classes. If the overlapping ratio is high, more information will be discarded to bring lower F-measure.

The five classifiers can be divided into two types. *C4.5* and *RIPPER* are rule-based classifiers. *NB*, *k-NN* and *SVMs* are distance-based classifiers. The distance-based classifiers are more sensitive than the rule-based ones to the class overlapping problem.

As the degree of class imbalance increases, the separating scheme showed higher improvements to the classification performance, in particular for the well-known SVMs.