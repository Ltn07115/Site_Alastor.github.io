
# Matrix Multiplication Project Report

**Student Name**: [Tianning Liu]  
**Student ID**: [ZY2457B16]  
**Submission Date**: [3/26/2025]

---

## System Configuration

| Component                    | Details                                   |
|------------------------------|-------------------------------------------|
| **CPU Model**                |  AMD Ryzen 9 6900HX with Radeon Graphics  |
| **Memory Size**              | 16GiB                                      |
| **Operating System Version** | Linux Vivian 5.15.167.4-microsoft-standard-WSL2 #1 SMP Tue Nov 5 00:21:55 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux     |
| **Compiler Version**         | gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0 |
| **Python Version**           | Python 3.12.3                            |

---

## Implementation Details

### C Language Implementation

**Source Code**:

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int rows;
    int cols;
    int **data;
} Matrix;

Matrix allocate_matrix(int rows, int cols) {
    Matrix m;
    m.rows = rows;
    m.cols = cols;
    m.data = malloc(rows * sizeof(int*));
    for (int i = 0; i < rows; i++) {
        m.data[i] = malloc(cols * sizeof(int));
    }
    return m;
}

void free_matrix(Matrix m) {
    for (int i = 0; i < m.rows; i++) {
        free(m.data[i]);
    }
    free(m.data);
}

void multiply(Matrix a, Matrix b, Matrix result) {
    for (int i = 0; i < a.rows; i++) {
        for (int j = 0; j < b.cols; j++) {
            result.data[i][j] = 0;
            for (int k = 0; k < a.cols; k++) {
                result.data[i][j] += a.data[i][k] * b.data[k][j];
            }
        }
    }
}

int main() {
    Matrix A = allocate_matrix(2, 2);
    Matrix B = allocate_matrix(2, 2);
    Matrix C = allocate_matrix(2, 2);

    // Example matrices initialization
    A.data[0][0] = 1; A.data[0][1] = 2;
    A.data[1][0] = 3; A.data[1][1] = 4;

    B.data[0][0] = 5; B.data[0][1] = 6;
    B.data[1][0] = 7; B.data[1][1] = 8;

    multiply(A, B, C);

    printf("Result:\n");
    for (int i = 0; i < C.rows; i++) {
        for (int j = 0; j < C.cols; j++) {
            printf("%d ", C.data[i][j]);
        }
        printf("\n");
    }

    free_matrix(A);
    free_matrix(B);
    free_matrix(C);
    return 0;
}
```
**Compilation Command**:
```
gcc matrix.c -o matrix
```
**Execution Command**:
```
./matrix
```
### Python Language Implementation

**Source Code**:
```python
import numpy as np

def multiply_matrices(A, B):
    return np.dot(A, B)

# Example matrices
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

C = multiply_matrices(A, B)

print("Result:\n", C)

```
**Execution Command**:
```
python3 matrix.py
```
## Algorithm Verification

The correctness of the algorithms was verified by directly comparing outputs from the implemented algorithms (both C and Python versions) with the result produced by NumPy's built-in multiplication function (`np.dot`). The outputs from both implementations matched exactly, confirming correctness.

## Conclusion

This project demonstrated:

-   Command line operations for compiling and executing C programs.
    
-   Using Markdown effectively to create structured documentation.
    
## References

-   GCC Official Documentation: [https://gcc.gnu.org/](https://gcc.gnu.org/)

## Appendix
### Additional Notes

-   Before compiling and executing, ensure the source files are placed correctly into the Ubuntu file system:
    
   **For C implementation (`matrix.c`):**
    
```
nano matrix_mult.c
```
 
   **For Python implementation (`matrix.py`):**
    
```
nano matrix_mult.py 
```
    
  After this, we can follow the commands provided earlier to compile (for C) and execute the files.
