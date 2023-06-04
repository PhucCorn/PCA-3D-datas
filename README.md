# PCA 3D data
## Feature extraction
Feature extraction is the process of detecting and isolating the desired features of patterns. It is the activity of identifying and interpreting meaningful information from data. This is the preprocessing step important in pattern recognition. This process will create a new dataset with a smaller number of features than the original number of features. These new features are created based on the original features (then removes the original features). New features such as a truncation summarize most of the information contained in the original feature set. This technique is done to reduce the size of the input data into smaller groups that are easy to process.
![Feature extraction algorithm](https://miro.medium.com/v2/resize:fit:800/0*sQzmiOf8Yb_18HX1.png)

And PCA is one of the feature extraction algorithm.
## Principal Component Analysis - PCA
### Introduce
PCA stands for Principal Component Analysis, which is a method of reducing the data dimension by converting some correlated attributes into a smaller number of uncorrelated attributes, these attributes are called principal components. This is a statistical algorithm that uses orthogonal transformation to transform a data set from a high-dimensional space to a new, less-dimensional space. Simply, we will analyze the data and then find the main components of the data toS keep those components. The main components here are essentially linear independent vectors chosen so that when projecting data points onto that vector, the data points have the largest variance (the most variation). Then the data will be widely distributed, not clustered in one place easily for the classification process. The method will create several advantages for the data:
- Reduce the number of dimensions of the data space when it has a large number of dimensions
- Build new coordinate axes capable of representing the data equally well, and ensure the variability of the data on each new dimension.
- Easier to visualize data to help us have a more intuitive view.
- Make sure that the coordinate axes in the new space are always orthogonal to each other, even though in the original space the axes may not be orthogonal.
### Step-by-step
Steps to implement PCA algorithm:
- Calculate mean of each attribute in the data set X
- Subtract each data point from mean of the entire data
- Calculate the covariance matrix of the data set X
- Calculate eigenvalues and eigenvectors of the covariance matrix, sorted in descending order of eigenvalues
![PCA procedure](.\img\pca_procedure.png)
## Applying PCA to feature extraction of 3D dataset
### Dataset
The dataset is a set of 20 data points, each data point includes feature 1, feature 2 and label:
(1, 1, 1), (1, 2, 1), (1, 3, 1), (2, 1, 1), (2, 2, 1), (2, 3, 1), (2, 3.5, 1), (2.5, 2, 1), (3.5, 1, 1), (3.5, 2,
1), (3.5, 3, 2), (3.5, 4, 2), (4.5, 1, 2), (4.5, 2, 2), (4.5, 3, 2), (5, 4, 2), (5, 5, 2), (6, 3, 2), (6, 4, 2),
(6, 5, 2)

### Extract dataset by PCA
Perform data set X (original data set) into the model:
![Start algorithm](./img/train.png)

Where the matrix X is a matrix of size D × N, where D is the number of dimensions of a data point and N is the number of samples in the data set. Each matrix column is a data point:
![Input matrix X](./img/matrix_X.png)

As a result, the vectors of the eigenvectors of the covariance matrix are the column vectors of the matrix

![Eigenvalue matrix X](./img/eigenvalue.png)

We can obtain the matrix containing the original data set in the new base system

![New matrix](./img/new%20matrix.png)

The histogram shows the ratio of variance through each component and the amount of information remaining after removing each component with the ascending order number of eigenvalues.

![Graph](./img/graph.png)

##Conclusion
Choosing a value for the n_components parameter has great significance for the algorithm because it determines the amount of information to be retained, the discarded information will be considered as redundant data and discarded. For the above case, we choose n_components = 2 as the maximum number of components that can be selected, because the number of components cannot be greater than the number of attributes of a data point. Since the number of components selected is 2 equal to the number of attributes of an original data point, any original data retained is not transferred to the new base system. Therefore, when we perform the conversion back to the original base system, no data loss occurs. This is shown in the chart above, when the number of components is 2, the variance ratio is 1. When choosing n_components = 1, there will be data loss and inverse matrix implementation will not be like the original matrix.

Inverse matrix with n_components = 1

![Inverse matrix with n_components = 1](./img/inverse%20matrix.png)
