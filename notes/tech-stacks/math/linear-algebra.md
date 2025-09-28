# Linear Algebra

## Solving Systems of Linear Equations

### 1. Solving a system of linear equations

- Find a particular solution to `Ax = b`.
    -   Build the augmented matrix in the form of `[A|b]`.
    -   _**Elementary transformation**_: transform the matrix to the row-echelon form (REF).
-   Find all solutions to `Ax = 0`.
    -   _**Gaussian elimination**_: transformed the matrix A to the reduced REF.
    -   or _**Minus-1 Trick**_: adding rows at the places where the pivots on the diagonal are missing.
    -   Derive all solutions for `Ax = 0` .
-   Combine the solutions from steps 1 and 2 to the general solution.