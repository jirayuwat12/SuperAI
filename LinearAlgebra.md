# Linear Algebra

## **vector**

- a point in the *M*-dimention space
- **v** = a*i* +b*j* + c*k* + ....
- treat as **Data point**

## **Matrix**

- a series of *N* points in the *M*-dim space
- Denoted by **A**,**B**,...
- treat as **set of Data point**

```
ex  [ x1, x2, x3]  
    | y1, y2, y3|  M = 3
    [ z1, z2, z3]
        N = 3
```

**operation** 
1. transpose ( T )
    - a<sub>*i, j*</sub> -> a<sub>*j, i*</sub>
1. Conjugate transport ( * )
    - a<sub>*i, j*</sub> -> Conjugate of a<sub>*j, i*</sub>
1. Scalar multiplication
    - const x **M**
1. Euclidean norm
    - norm( **M** ) = ( sum of all element<sup>2</sup> )<sup>0.5</sup>

1. Trace
    - trace( **M** ) = sum of all diagonal

# Transformation and Determinant

1. Linear Transformation
$ A \times B$ projects each data point $b^{(k)}$ in $B$ onto an **affine space**, where each axis is specified by each column vector in $A$ 

$$
A \times B =
\begin{bmatrix} 
    2 & 1 \\
    1 & 2
\end{bmatrix} \times
\begin{bmatrix} 
    1 & 0 & 2\\
    0 & 1 & 3
\end{bmatrix}
= C=
\begin{bmatrix} 
    2 & 1 & 7\\
    1 & 2 & 8
\end{bmatrix}
$$
2. Determinant
    - scaling factor (volume) of transformation
        - computed by laplace expansion


## application in CV

image in form of column vector matrix 
$$ A =  
\begin{bmatrix}
    x \\ y \\ bit map
\end{bmatrix}
$$
1. translation 
$$ translation\ matrix =  
\begin{bmatrix}
    1 & 0 & t_x \\ 
    0 & 1 & t_y \\ 
    0 & 0 & 1
\end{bmatrix} \times A = 
\begin{bmatrix}
    x+t_x \\ y + t_y \\ bitmap
\end{bmatrix}
$$
2. scaling 
$$ scaling\ matrix =  
\begin{bmatrix}
    s_x & 0 & 0 \\ 
    0 & s_y & 0 \\ 
    0 & 0 & 1
\end{bmatrix} \times A = 
\begin{bmatrix}
    s_xx \\ s_yy  \\ bitmap
\end{bmatrix}
$$

3. rotation 
$$ rotation\ matrix =  
\begin{bmatrix}
    cos\theta & -sin\theta & 0 \\ 
    sin\theta & cos\theta & 0 \\ 
    0 & 0 & 1
\end{bmatrix} \times A = 
\begin{bmatrix}
    x\ cos\theta - y\ sin\theta \\
    x\ sin\theta + y\ cos\theta   \\ bitmap
\end{bmatrix}
$$


## Eigenvectors

- an **eigenvector** $v$ of $A$ is a direction in which $A$ is projected to obtain a simpler representation while retaining the characteristic information of $A$ as much as possible
$$ A\ v = \lambda\ v$$

$$ v = eigen\ vector (ทิศทางของเงา)\\
\lambda = eigan\ value (ความชัดของเงา)\\
that\ represent\ A\ in\ form\ of\ projection\ ( A \times v) (เงา)

$$


- Iterative Power Method -> finding the **dominant** eiganvector by 
- Deflation -> find another eigan value

## Singular Value Decomposition ( SVD )
- decomposing a non-square matrix (dim $M \leq$ data size $N$ )
$$
A_{M\times N} = U_{M\times M} \times \varSigma _{M\times N} \times V^{*}_{N\times N}
$$

- sometimes we can trade off the accuracy with the speed by discarding some non-dominant eigenvector using **Truncated SVD**
- finding Pseudo-Inverse with SVD
$$
A^{-1}_{M\times N} = (V^{*}_{N\times N})^{-1} \times \varSigma ^{-1}_{M\times N} \times U^{-1}_{M\times M}
$$
$$
A^{-1}_{M\times N} = V_{N\times N} \times \varSigma ^{-1}_{์์N\times M} \times U^{*}_{M\times M}
$$
- finding Power of Square Matrix with SVD

$$
A^p_{M\times N} = U^p_{M\times M} \times \varSigma ^p_{M\times N} \times (V^{*}_{N\times N})^p
$$
$$
A^p_{M\times N} = U_{M\times M} \times \varSigma ^p_{M\times N} \times V^{*}_{N\times N}
$$
