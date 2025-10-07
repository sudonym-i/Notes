

**One way of thinking about projections, is as finding the projection
is the same as finding the closest point along v to x**

## Matrix Projections

### Definition
A projection matrix P satisfies the property: **P² = P** (idempotent)

This means applying the projection twice gives the same result as applying it once.

### Orthogonal Projections
For an orthogonal projection onto a subspace:
- **P = A(A^T A)^(-1) A^T** where A's columns span the subspace
- The projection is **symmetric**: P^T = P
- Projects vectors onto the column space of A
- The complementary projection is **(I - P)**, which projects onto the orthogonal complement

### Properties
- **Pv** gives the component of v in the subspace
- **(I - P)v** gives the component perpendicular to the subspace
- **||v||² = ||Pv||² + ||(I-P)v||²** (Pythagorean theorem)

### Example: Projection onto a line
For a unit vector u, the projection matrix is: **P = uu^T**

## Hermitian Matrices

### Definition
A Hermitian matrix satisfies: **A = A^H** where A^H is the conjugate transpose

For real matrices, Hermitian = symmetric (A = A^T)

### Key Properties
1. **Eigenvalues are real**
2. **Eigenvectors corresponding to distinct eigenvalues are orthogonal**
3. **Always diagonalizable**: A = QΛQ^H where Q is unitary
4. **Preserves inner products** in a certain sense

### Spectral Theorem
Every Hermitian matrix can be written as:
**A = Σ λᵢ vᵢvᵢ^H**

where λᵢ are real eigenvalues and vᵢ are orthonormal eigenvectors.

### Connection to Projections
- Hermitian matrices with eigenvalues only 0 and 1 are **orthogonal projection matrices**
- Any Hermitian matrix can be thought of as a weighted sum of orthogonal projections

### Physical Interpretation
In quantum mechanics, Hermitian operators represent **observable quantities** (like position, momentum, energy) because their eigenvalues are real.


$$proj = \sum_{i=1}^k v_i v^*_i$$
$$\implies proj{(v_1, v_2)} = v_1 v_1^* + v_2 v_2^*$$

Another way of writing this:
$$A \in \text{Orthonormal columns} \implies A \space{} A^* = P  
\implies   v_1 v_1^* + v_2 v_2^*$$
	