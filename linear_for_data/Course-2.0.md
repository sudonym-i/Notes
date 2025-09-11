# Linear Algebra Core Concepts

## 1. Linear Independence

### Definition
*   A set of vectors $\{v_1, v_2, \dots, v_k\}$ is **linearly independent** if the only way to form the zero vector as a linear combination of these vectors is by setting all the scalar coefficients to zero.
*   Mathematically: If $c_1v_1 + c_2v_2 + \dots + c_kv_k = 0$, then it must be that $c_1 = c_2 = \dots = c_k = 0$.

### Intuition
*   No vector in the set can be written as a linear combination of the others.
*   Each vector adds a "new dimension" or direction that cannot be achieved by combining the other vectors.
*   They are not redundant.

### How to Check
*   Form a matrix $A$ where the vectors are its columns.
*   Solve the homogeneous equation $Ax = 0$.
*   If the only solution is the trivial solution ($x = 0$), then the columns (vectors) are linearly independent.
*   This is equivalent to checking if the **Kernel (Null Space)** of $A$ contains only the zero vector.

## 2. Linear Transformations

### Definition
*   A function $T: V \to W$ (where $V$ and $W$ are vector spaces) is a **linear transformation** if it satisfies two properties for all vectors $u, v$ in $V$ and any scalar $c$:
    1.  **Additivity**: $T(u + v) = T(u) + T(v)$
    2.  **Homogeneity**: $T(cu) = cT(u)$

### Intuition
*   Linear transformations preserve the operations of vector addition and scalar multiplication.
*   They map lines to lines (or points), and the origin to the origin.
*   Common examples include rotations, reflections, scaling, and shears.

### Matrix Representation
*   Every linear transformation from $\mathbb{R}^n$ to $\mathbb{R}^m$ can be represented by an $m \times n$ matrix $A$.
*   If $T(x) = Ax$, then $A$ is the **standard matrix** of the linear transformation.
*   The columns of $A$ are the images of the standard basis vectors under the transformation: $A = [T(e_1) \ T(e_2) \ \dots \ T(e_n)]$.

## 3. Subspace

### Definition
*   A **subspace** $W$ of a vector space $V$ is a non-empty subset of $V$ that is itself a vector space under the same operations of vector addition and scalar multiplication defined on $V$.

### Properties (to be a subspace)
A non-empty subset $W$ of a vector space $V$ is a subspace if it satisfies these three conditions:
1.  **Contains the Zero Vector**: The zero vector of $V$ is in $W$ ($0 \in W$).
2.  **Closed Under Addition**: For any $u, v \in W$, their sum $u + v$ is also in $W$.
3.  **Closed Under Scalar Multiplication**: For any $u \in W$ and any scalar $c$, the product $cu$ is also in $W$.

### Examples
*   The set of all vectors that are multiples of a single non-zero vector (a line through the origin).
*   The set of all vectors that lie on a plane passing through the origin.
*   The **span** of a set of vectors is always a subspace.
*   The **Kernel (Null Space)** of a matrix $A$ (all $x$ such that $Ax=0$) is a subspace.
*   The **Column Space (Image)** of a matrix $A$ (the span of its columns) is a subspace.

## 4. Basis Vectors

### Definition
*   A **basis** for a vector space $V$ is a set of vectors $B = \{b_1, b_2, \dots, b_n\}$ within $V$ that satisfies two conditions:
    1.  The set $B$ is **linearly independent**.
    2.  The set $B$ **spans** $V$ (i.e., every vector in $V$ can be written as a linear combination of the vectors in $B$).

### Intuition
*   A basis is a minimal set of vectors that can generate the entire vector space.
*   It provides a "coordinate system" for the vector space.
*   Every vector in the space can be uniquely expressed as a linear combination of the basis vectors.

### Key Properties
*   The number of vectors in any basis for a given vector space $V$ is always the same. This number is called the **dimension** of $V$.
*   For $\mathbb{R}^n$, the **standard basis** is $\{e_1, e_2, \dots, e_n\}$, where $e_i$ is a vector with a 1 in the $i$-th position and 0s elsewhere (e.g., for $\mathbb{R}^3$, $\{[1,0,0]^T, [0,1,0]^T, [0,0,1]^T\}$).

## Important fact:

For every *linear transformation* $T: V \to W$, where  and $W$ are finite-dimensional vector spaces, there exists a unique matrix $A$ such that $T(\mathbf{v}) = A\mathbf{v}$ for all $\mathbf{v} \in V$.

More specifically, if $V = \mathbb{R}^n$ and $W = \mathbb{R}^m$, then $A$ is an $m \times n$ matrix.

-----
# Basis Vectors in Linear Algebra

## What is a Basis?

A **basis** for a vector space $V$ is a special set of vectors that acts as a fundamental building block for that space. It's a set of vectors that is both:

1.  **Linearly Independent**: No vector in the set can be written as a linear combination of the others. They are "unique" in their direction.
2.  **Spans the Vector Space**: Every vector in the vector space $V$ can be expressed as a linear combination of the vectors in the basis set. They can "reach" every point in the space.

## Key Characteristics & Intuition

*   **Minimal Spanning Set**: A basis is the smallest possible set of vectors that can span the entire vector space. If you remove any vector from a basis, it will no longer span the space.
*   **Unique Representation**: For any given vector in the space, there is only *one unique way* to express it as a linear combination of the basis vectors. This uniqueness is what allows us to define coordinates.
*   **"Coordinate System"**: Think of a basis as defining the "axes" or "directions" for a vector space. Just like the x, y, and z axes in 3D space, basis vectors provide a framework.
*   **Dimension**: The number of vectors in any basis for a given vector space is always the same. This number is called the **dimension** of the vector space. For example, $\mathbb{R}^3$ (3D space) always has a basis with 3 vectors.

## Examples

### 1. Standard Basis (Canonical Basis)

*   This is the most common and intuitive basis for $\mathbb{R}^n$.
*   For $\mathbb{R}^2$: $\{ \begin{pmatrix} 1 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 1 \end{pmatrix} \}$
*   For $\mathbb{R}^3$: $\{ \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix} \}$
*   These vectors are mutually orthogonal (perpendicular) and have a length of 1.

### 2. Other Bases

*   A vector space can have infinitely many different bases.
*   For $\mathbb{R}^2$, the set $\{ \begin{pmatrix} 1 \\ 1 \end{pmatrix}, \begin{pmatrix} -1 \\ 1 \end{pmatrix} \}$ is also a basis.
    *   They are linearly independent (one is not a multiple of the other).
    *   They span $\mathbb{R}^2$ (any vector $\begin{pmatrix} x \\ y \end{pmatrix}$ can be written as $c_1 \begin{pmatrix} 1 \\ 1 \end{pmatrix} + c_2 \begin{pmatrix} -1 \\ 1 \end{pmatrix}$).

## Why are Basis Vectors Important?

*   **Understanding Structure**: They help us understand the fundamental structure and "size" (dimension) of a vector space.
*   **Coordinates**: They provide a way to assign unique coordinates to every vector in a space.
*   **Transformations**: Linear transformations are often defined by how they act on basis vectors.
*   **Simplification**: Many problems in linear algebra become simpler when expressed in terms of a suitable basis.

------
# Finding the Matrix of a Linear Transformation

## The Core Idea

Every linear transformation $T: \mathbb{R}^n \to \mathbb{R}^m$ can be represented by a unique $m \times n$ matrix $A$. This means that applying the transformation $T$ to a vector $\mathbf{x}$ is equivalent to multiplying $\mathbf{x}$ by the matrix $A$:

$T(\mathbf{x}) = A\mathbf{x}$

The key to finding this matrix $A$ lies in understanding how the transformation acts on the **standard basis vectors** of the domain space $\mathbb{R}^n$.

## The Standard Basis Vectors

For $\mathbb{R}^n$, the standard basis vectors are:
*   $\mathbf{e}_1 = \begin{pmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{pmatrix}$
*   $\mathbf{e}_2 = \begin{pmatrix} 0 \\ 1 \\ \vdots \\ 0 \end{pmatrix}$
*   ...
*   $\mathbf{e}_n = \begin{pmatrix} 0 \\ 0 \\ \vdots \\ 1 \end{pmatrix}$

Any vector $\mathbf{x} = \begin{pmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{pmatrix}$ in $\mathbb{R}^n$ can be written as a unique linear combination of these standard basis vectors:
$\mathbf{x} = x_1\mathbf{e}_1 + x_2\mathbf{e}_2 + \dots + x_n\mathbf{e}_n$

## The Method

Since $T$ is a linear transformation, it preserves addition and scalar multiplication:
$T(\mathbf{x}) = T(x_1\mathbf{e}_1 + x_2\mathbf{e}_2 + \dots + x_n\mathbf{e}_n)$
$T(\mathbf{x}) = x_1T(\mathbf{e}_1) + x_2T(\mathbf{e}_2) + \dots + x_nT(\mathbf{e}_n)$

Now, if we define the matrix $A$ such that its columns are the transformed standard basis vectors:
$A = \begin{pmatrix} | & | & & | \\ T(\mathbf{e}_1) & T(\mathbf{e}_2) & \dots & T(\mathbf{e}_n) \\ | & | & & | \end{pmatrix}$

Then, multiplying $A$ by $\mathbf{x}$ gives:
$A\mathbf{x} = \begin{pmatrix} | & | & & | \\ T(\mathbf{e}_1) & T(\mathbf{e}_2) & \dots & T(\mathbf{e}_n) \\ | & | & & | \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{pmatrix} = x_1T(\mathbf{e}_1) + x_2T(\mathbf{e}_2) + \dots + x_nT(\mathbf{e}_n)$

This is exactly $T(\mathbf{x})$!

**Therefore, to find the matrix $A$ for a linear transformation $T$:**
1.  Determine the images of the standard basis vectors under the transformation $T$.
2.  Form the matrix $A$ by using these images as its columns.

## Examples

### Example 1: Rotation in $\mathbb{R}^2$

Let $T: \mathbb{R}^2 \to \mathbb{R}^2$ be a rotation counter-clockwise by an angle $\theta$.

1.  **Find $T(\mathbf{e}_1)$:**
    *   $\mathbf{e}_1 = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$ (a vector along the positive x-axis).
    *   Rotating $\mathbf{e}_1$ by $\theta$ gives $\begin{pmatrix} \cos\theta \\ \sin\theta \end{pmatrix}$.
    *   So, $T(\mathbf{e}_1) = \begin{pmatrix} \cos\theta \\ \sin\theta \end{pmatrix}$.

2.  **Find $T(\mathbf{e}_2)$:**
    *   $\mathbf{e}_2 = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$ (a vector along the positive y-axis).
    *   Rotating $\mathbf{e}_2$ by $\theta$ gives $\begin{pmatrix} -\sin\theta \\ \cos\theta \end{pmatrix}$.
    *   So, $T(\mathbf{e}_2) = \begin{pmatrix} -\sin\theta \\ \cos\theta \end{pmatrix}$.

3.  **Form the matrix $A$:**
    $A = \begin{pmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{pmatrix}$

This is the standard rotation matrix.

### Example 2: Projection onto the x-axis in $\mathbb{R}^2$

Let $T: \mathbb{R}^2 \to \mathbb{R}^2$ be the projection of a vector onto the x-axis. This means $T\begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} x \\ 0 \end{pmatrix}$.

1.  **Find $T(\mathbf{e}_1)$:**
    *   $\mathbf{e}_1 = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$.
    *   $T\begin{pmatrix} 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$.
    *   So, $T(\mathbf{e}_1) = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$.

2.  **Find $T(\mathbf{e}_2)$:**
    *   $\mathbf{e}_2 = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$.
    *   $T\begin{pmatrix} 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$.
    *   So, $T(\mathbf{e}_2) = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$.

3.  **Form the matrix $A$:**
    $A = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}$

### Example 3: Transformation from $\mathbb{R}^3$ to $\mathbb{R}^2$

Let $T: \mathbb{R}^3 \to \mathbb{R}^2$ be defined by $T\begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \begin{pmatrix} x_1 - x_2 \\ x_2 + x_3 \end{pmatrix}$.

1.  **Find $T(\mathbf{e}_1)$:**
    *   $\mathbf{e}_1 = \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}$.
    *   $T\begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 - 0 \\ 0 + 0 \end{pmatrix} = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$.

2.  **Find $T(\mathbf{e}_2)$:**
    *   $\mathbf{e}_2 = \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}$.
    *   $T\begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix} = \begin{pmatrix} 0 - 1 \\ 1 + 0 \end{pmatrix} = \begin{pmatrix} -1 \\ 1 \end{pmatrix}$.

3.  **Find $T(\mathbf{e}_3)$:**
    *   $\mathbf{e}_3 = \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}$.
    *   $T\begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix} = \begin{pmatrix} 0 - 0 \\ 0 + 1 \end{pmatrix} = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$.

4.  **Form the matrix $A$:**
    $A = \begin{pmatrix} 1 & -1 & 0 \\ 0 & 1 & 1 \end{pmatrix}$


____
# Matrix Multiplication as a Linear Combination of Columns

## The Core Idea

When a matrix $A$ multiplies a vector $\mathbf{x}$ ($A\mathbf{x}$), the result is a new vector that is a **linear combination of the columns of $A$**, with the entries of $\mathbf{x}$ serving as the scalar coefficients.

## Formal Definition

Let $A$ be an $m \times n$ matrix, with columns $\mathbf{a}_1, \mathbf{a}_2, \dots, \mathbf{a}_n$.
So, $A = \begin{pmatrix} | & | & & | \\ \mathbf{a}_1 & \mathbf{a}_2 & \dots & \mathbf{a}_n \\ | & | & & | \end{pmatrix}$.

Let $\mathbf{x}$ be an $n \times 1$ column vector:
$\mathbf{x} = \begin{pmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{pmatrix}$.

The product $A\mathbf{x}$ is defined as:
$A\mathbf{x} = x_1\mathbf{a}_1 + x_2\mathbf{a}_2 + \dots + x_n\mathbf{a}_n$

## Why This is Important

*   **Geometric Interpretation**: It provides a powerful geometric understanding of matrix-vector multiplication. Instead of just a mechanical process of dot products, it shows that $A\mathbf{x}$ is a vector formed by "mixing" the columns of $A$ according to the weights in $\mathbf{x}$.
*   **Span and Column Space**: The set of all possible vectors that can be formed by $A\mathbf{x}$ (for all possible $\mathbf{x}$) is precisely the **span of the columns of $A$**. This is also known as the **column space** (or image) of $A$.
*   **Linear Transformations**: This perspective directly connects matrix multiplication to linear transformations. If $T(\mathbf{x}) = A\mathbf{x}$, then the output of the transformation is always a vector in the column space of $A$.
*   **Solving $A\mathbf{x} = \mathbf{b}$**: The equation $A\mathbf{x} = \mathbf{b}$ has a solution if and only if $\mathbf{b}$ can be expressed as a linear combination of the columns of $A$ (i.e., $\mathbf{b}$ is in the column space of $A$).

## Example

Let $A = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{pmatrix}$ and $\mathbf{x} = \begin{pmatrix} 2 \\ -1 \\ 3 \end{pmatrix}$.

Here, the columns of $A$ are:
$\mathbf{a}_1 = \begin{pmatrix} 1 \\ 4 \\ 7 \end{pmatrix}$, $\mathbf{a}_2 = \begin{pmatrix} 2 \\ 5 \\ 8 \end{pmatrix}$, $\mathbf{a}_3 = \begin{pmatrix} 3 \\ 6 \\ 9 \end{pmatrix}$.

And the entries of $\mathbf{x}$ are $x_1 = 2$, $x_2 = -1$, $x_3 = 3$.

According to the linear combination definition:
$A\mathbf{x} = x_1\mathbf{a}_1 + x_2\mathbf{a}_2 + x_3\mathbf{a}_3$
$A\mathbf{x} = 2\begin{pmatrix} 1 \\ 4 \\ 7 \end{pmatrix} + (-1)\begin{pmatrix} 2 \\ 5 \\ 8 \end{pmatrix} + 3\begin{pmatrix} 3 \\ 6 \\ 9 \end{pmatrix}$

Let's calculate this:
$A\mathbf{x} = \begin{pmatrix} 2 \\ 8 \\ 14 \end{pmatrix} + \begin{pmatrix} -2 \\ -5 \\ -8 \end{pmatrix} + \begin{pmatrix} 9 \\ 18 \\ 27 \end{pmatrix}$
$A\mathbf{x} = \begin{pmatrix} 2 - 2 + 9 \\ 8 - 5 + 18 \\ 14 - 8 + 27 \end{pmatrix} = \begin{pmatrix} 9 \\ 21 \\ 33 \end{pmatrix}$

## Comparison with Row-Vector Dot Products

While the linear combination view is powerful, it's worth noting that matrix multiplication can also be seen as a series of dot products between the rows of $A$ and the vector $\mathbf{x}$.

For the same example:
$A\mathbf{x} = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{pmatrix} \begin{pmatrix} 2 \\ -1 \\ 3 \end{pmatrix}$

Row 1: $(1)(2) + (2)(-1) + (3)(3) = 2 - 2 + 9 = 9$
Row 2: $(4)(2) + (5)(-1) + (6)(3) = 8 - 5 + 18 = 21$
Row 3: $(7)(2) + (8)(-1) + (9)(3) = 14 - 8 + 27 = 33$

Result: $\begin{pmatrix} 9 \\ 21 \\ 33 \end{pmatrix}$

Both methods yield the same result, but the linear combination perspective offers deeper insight into the geometric and conceptual meaning of the operation.

-------
# Image and Kernel in Linear Algebra

The concepts of the Image (also known as Column Space or Range) and the Kernel (also known as Null Space) are fundamental to understanding linear transformations and matrices. They describe key properties of how a linear transformation maps vectors from one space to another.

## 1. The Image (Column Space / Range)

### Definition
*   The **Image** of an $m \times n$ matrix $A$ (denoted as $\text{Im}(A)$ or $\text{Col}(A)$) is the set of all possible vectors $\mathbf{b}$ in $\mathbb{R}^m$ such that the equation $A\mathbf{x} = \mathbf{b}$ has at least one solution.
*   Equivalently, it is the **span of the columns of $A$**.
*   If $T: \mathbb{R}^n \to \mathbb{R}^m$ is a linear transformation with standard matrix $A$, then the Image of $T$ (denoted as $\text{Im}(T)$ or $\text{Range}(T)$) is the set of all vectors $\mathbf{w}$ in $\mathbb{R}^m$ that are the output of $T$ for some input $\mathbf{v}$ in $\mathbb{R}^n$.

### Intuition
*   The Image represents all the vectors that can be "reached" by the transformation $T$ (or by multiplying by matrix $A$).
*   It's the "output space" or the "reach" of the transformation.
*   It tells you which vectors $\mathbf{b}$ allow the system $A\mathbf{x} = \mathbf{b}$ to be consistent.

### Properties
*   The Image of $A$ is a **subspace of $\mathbb{R}^m$**.
*   The **dimension of the Image** is called the **rank** of the matrix $A$ (denoted as $\text{rank}(A)$).
*   To find a basis for the Image:
    1.  Row reduce the matrix $A$ to its Row Echelon Form (REF) or Reduced Row Echelon Form (RREF).
    2.  Identify the columns in the *original* matrix $A$ that correspond to the pivot columns in the row-reduced form. These original columns form a basis for the Image.

### Example
Let $A = \begin{pmatrix} 1 & 2 & 0 \\ 0 & 1 & 1 \\ 1 & 3 & 1 \end{pmatrix}$.
1.  Row reduce $A$:
    $\begin{pmatrix} 1 & 2 & 0 \\ 0 & 1 & 1 \\ 1 & 3 & 1 \end{pmatrix} \xrightarrow{R_3 - R_1} \begin{pmatrix} 1 & 2 & 0 \\ 0 & 1 & 1 \\ 0 & 1 & 1 \end{pmatrix} \xrightarrow{R_3 - R_2} \begin{pmatrix} 1 & 2 & 0 \\ 0 & 1 & 1 \\ 0 & 0 & 0 \end{pmatrix}$
2.  Pivot columns are column 1 and column 2.
3.  Basis for $\text{Im}(A)$ (using original columns): $\left\{ \begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}, \begin{pmatrix} 2 \\ 1 \\ 3 \end{pmatrix} \right\}$.
4.  $\text{rank}(A) = 2$.

---

## 2. The Kernel (Null Space)

### Definition
*   The **Kernel** of an $m \times n$ matrix $A$ (denoted as $\text{Ker}(A)$ or $\text{Null}(A)$) is the set of all vectors $\mathbf{x}$ in $\mathbb{R}^n$ such that $A\mathbf{x} = \mathbf{0}$.
*   If $T: \mathbb{R}^n \to \mathbb{R}^m$ is a linear transformation with standard matrix $A$, then the Kernel of $T$ (denoted as $\text{Ker}(T)$) is the set of all vectors $\mathbf{v}$ in $\mathbb{R}^n$ that are mapped to the zero vector in $\mathbb{R}^m$ by $T$.

### Intuition
*   The Kernel represents all the vectors that "disappear" or are "crushed" to the zero vector by the transformation $T$ (or by multiplying by matrix $A$).
*   It tells you which distinct inputs lead to the same output (the zero vector).
*   It's related to the "loss of information" or "degeneracy" of the transformation.

### Properties
*   The Kernel of $A$ is a **subspace of $\mathbb{R}^n$**.
*   The **dimension of the Kernel** is called the **nullity** of the matrix $A$ (denoted as $\text{nullity}(A)$).
*   To find a basis for the Kernel:
    1.  Solve the homogeneous system $A\mathbf{x} = \mathbf{0}$.
    2.  Express the solution in parametric vector form.
    3.  The vectors that multiply the free variables form a basis for the Kernel.

### Example
Let $A = \begin{pmatrix} 1 & 2 & 0 \\ 0 & 1 & 1 \\ 1 & 3 & 1 \end{pmatrix}$. (Same matrix as above)
1.  We already row-reduced $A$ to $\begin{pmatrix} 1 & 2 & 0 \\ 0 & 1 & 1 \\ 0 & 0 & 0 \end{pmatrix}$.
2.  Now solve $A\mathbf{x} = \mathbf{0}$:
    $\begin{pmatrix} 1 & 2 & 0 \\ 0 & 1 & 1 \\ 0 & 0 & 0 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$
    From the second row: $x_2 + x_3 = 0 \implies x_2 = -x_3$.
    From the first row: $x_1 + 2x_2 = 0 \implies x_1 = -2x_2 = -2(-x_3) = 2x_3$.
3.  Let $x_3 = t$ (free variable).
    Then $\mathbf{x} = \begin{pmatrix} 2t \\ -t \\ t \end{pmatrix} = t \begin{pmatrix} 2 \\ -1 \\ 1 \end{pmatrix}$.
4.  Basis for $\text{Ker}(A)$: $\left\{ \begin{pmatrix} 2 \\ -1 \\ 1 \end{pmatrix} \right\}$.
5.  $\text{nullity}(A) = 1$.


