UECM3033 Assignment #2 Report
========================================================

- Prepared by: Koe Wei Shiang
- Tutorial Group: T2

--------------------------------------------------------

## Task 1 --  $LU$ Factorization or SOR method

The reports, codes and supporting documents are to be uploaded to Github at: 

https://github.com/jacksonkoe/UECM3033_assign2/blob/master/task1.py

Explain your selection criteria here.

As written in the python code that is np.count_nonzero(A) > 1/2*len(A) , we will choose LU decomposition to solve the problem when the nonzero are bigger than the half of length of matrix A. In corresponding with LU factorization , we use SOR method to solve because it is more suitable for sparse matrix compared to other iterative method.

Explain how you implement your `task1.py` here.

We first define the LU decomposition and SOR method in python.

For the LU decomposition, we define A = LU => Ax = LUx = b and letting Ux = y , we obtain Ly = b where L is the lower triangular matrix, U is the upper triangular matrix. Therefore, we can get our x matrix after solving for the y matrix.

For the SOR method, we must set up the omega value. If the value of omega is larger than 2, SOR method will not converge. However, if the value of omega is in between 0 and 1, SOR method converges but the rate of convergence is slower than Gauss-Seidel method. Therefore, we assumed the value of omega to be 1.03 as which in between 1 and 2 that will converge for any initial vector if matrix A is symmetric and positive definite. 

We also need to set the iteration limit because we do not want the infinite loop occur in this method. In this case, the limit is set to 100. The first x matrix is initialized as zero vector and eventually we will get the following result.

The solutions to the first set of 3-variables system of linear equations are [1. 1. 1.].

The solutions to the second set of 6-variables system of linear equations are [ 1. -1. 4. -3.5 7. -1. ].

---------------------------------------------------------

## Task 2 -- SVD method and image compression

Put here your picture file (Lenna.png)

https://github.com/jacksonkoe/UECM3033_assign2/blob/master/assassin.jpg

How many non zero element in $\Sigma$?

The number of non zero elements in $\Sigma$ is 800.

Put here your lower and better resolution pictures. Explain how you generate
these pictures from `task2.py`.

https://github.com/jacksonkoe/UECM3033_assign2/blob/master/rgb_low.jpg

First, the original image is split into 3 components that is red, green and blue. For each of the component, the predefined linalg.svd() function is used to perform singular value decomposition. We input n = 30 as an input parameter to the function reso(n,U,sigma,V) for all the components. It means that only the first 30 singular values in $\Sigma$ are non-zeros. Since most of the singular values are set to zeros, we can see the quality of the image has go down. The picture has now become a lower resolution picture.

https://github.com/jacksonkoe/UECM3033_assign2/blob/master/rgb_better.jpg

Instead of n = 30, we now replace the value of n with 200. This mean now we have 200 non-zeros singular values in $\Sigma$. Therefore, the quality of the image has become better and the picture has better resolution.

What is a sparse matrix?

A sparse matrix is a matrix where most of the elements are zero. If most of the elements are nonzero, then the matrix is considered dense. In image compression with SVD, our $\Sigma$ is considered as the sparse matrix.

-----------------------------------

<sup>last modified: 12nd March 2016/sup>
