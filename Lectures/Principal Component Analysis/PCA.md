# Dimensionality Reduction
Does not change data

Transforming features for visualizations

## PCA
Eigen-decomposition of the covariance matrix: (x^T\*x)

x = \[]
- n: sample
- m: features
- x = nxm matrix

x^T
- mxn

x^T\*x
- mxm (square)

Eigen decomposition (x^T\*x)
- W: eigenvectors
- λ: eigenvalues

T = x\*W (transformation)
- x = nxm
- W = mxm
- T = nxm

W = 
- | ............ |
- | w1 w2 ... wm |
- | ............ |

W
- Ordered by λ
- w1 explains more variation tahn w2, w3, ... wm

T = x\*Wk
- x = nxm
- W = mxk
- T = nxk

Algorithm: PCA
- Preprocessing step:
    * standardize
    * mean normalization
- Eigen decomposition: W
- Reduction: T = x\*Wk