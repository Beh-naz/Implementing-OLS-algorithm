# Implementing-OLS-algorithm

## Overview
This repository contains an implementation of Ordinary Least Squares (OLS) to fit a 2D surface to a dataset in R3 using both custom Python implementation and the lsfit function in R. The main goal is to approximate the quadratic surface of the form:

$z = g ( x , y ) = a_1 x^2 + a_2 y^2 + a_3 xy + a_4 x + a_5 y + a_6$

using a dataset consisting of 10,000 triplets <x, y, z> by minimizing the total vertical distance of data points to the surface.

## Problem Statement

### 1. Matrix-Vector Formulation

To frame this problem in the least-squares context, we seek to minimize the residual sum of squares:

$r = || Az - b ||^2$

where:

. $A$ is the design matrix. Each row of $A$ corresponds to an observation and contains the values $[x^2, y^2, xy, x, y, 1]$.

. $z$ is a column vector containing the coefficients $[a_1, a_2, a_3, a_4, a_5, a_6]$.

. $b$ is a column vector containing the observed $z$-values from the dataset.

## Implementation Steps

### 1- Import Data:

. Data is imported from a provided CSV file and saved as an array.

### 2- Matrix Construction:

. Construct matrix $X$ as a $ 10000 \times 6 $ matrix. Each row represents one pair $(x, y)$ and is of the form $[x^2, y^2, xy, x, y, 1]$.

. Construct vector $ Y $ as a $ 10000 \times 1 $ vector with entries sourced from the third column $(Z)$ of the imported data.

### 3- Matrix Multiplication and Inversion:

By using matrix transposition, inversion, and multiplication, calculate the matrix $w = (X^TX)^{-1}X^TY$. The resulting 6x1 matrix, 
$w$, contains coefficients of the desired quadratic surface. The calculated coefficients were:

2.00001558

2.9999851

5.00000588

6.99933268

10.9999725

13.5192896

### 4- Comparison with R:

Using lsfit in R for the same problem produced the following results:

2.000016

2.999985

5.000006

6.999333

10.999973

13.519290
​
 
The results from the manual Python implementation and R are almost identical. The slight difference can be attributed to R's rounding.

## Conclusion

The custom implementation in Python provided results consistent with R's lsfit function, validating the accuracy of the Python implementation.

​

