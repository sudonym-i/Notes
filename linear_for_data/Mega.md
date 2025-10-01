# Complex Numbers: Fundamentals

Complex numbers extend the concept of real numbers by introducing an imaginary unit, $i$, defined as the square root of -1. They are fundamental in many areas of mathematics, physics, and engineering.

## 1. Definition of a Complex Number

A complex number $z$ is typically expressed in the form:

$z = a + bi$

Where:
* $a$ is the **real part** of $z$, denoted as $Re(z)$.
* $b$ is the **imaginary part** of $z$, denoted as $Im(z)$.
* $i$ is the **imaginary unit**, where $i^2 = -1$.

**Examples:**
* $3 + 2i$ (Real part = 3, Imaginary part = 2)
* $-5i$ (Real part = 0, Imaginary part = -5)
* $7$ (Real part = 7, Imaginary part = 0 - this is a real number, which is a subset of complex numbers)

## 2. Basic Operations with Complex Numbers

Let $z_1 = a + bi$ and $z_2 = c + di$ be two complex numbers.

### a. Addition
To add complex numbers, add their real parts and their imaginary parts separately.

$z_1 + z_2 = (a + bi) + (c + di) = (a + c) + (b + d)i$

**Example:**
$(2 + 3i) + (1 - 5i) = (2 + 1) + (3 - 5)i = 3 - 2i$

### b. Subtraction
To subtract complex numbers, subtract their real parts and their imaginary parts separately.

$z_1 - z_2 = (a + bi) - (c + di) = (a - c) + (b - d)i$

**Example:**
$(4 + 2i) - (1 + 7i) = (4 - 1) + (2 - 7)i = 3 - 5i$

### c. Multiplication
Multiply complex numbers like binomials, remembering that $i^2 = -1$.

$z_1 \cdot z_2 = (a + bi)(c + di) = ac + adi + bci + bdi^2$
$z_1 \cdot z_2 = ac + (ad + bc)i - bd$
$z_1 \cdot z_2 = (ac - bd) + (ad + bc)i$

**Example:**
$(2 + 3i)(1 - i) = (2)(1) + (2)(-i) + (3i)(1) + (3i)(-i)$
$= 2 - 2i + 3i - 3i^2$
$= 2 + i - 3(-1)$
$= 2 + i + 3$
$= 5 + i$

### d. Division
Division involves using the **complex conjugate** of the denominator. The complex conjugate of $c + di$ is $c - di$. Multiplying a complex number by its conjugate results in a real number: $(c + di)(c - di) = c^2 - (di)^2 = c^2 - d^2i^2 = c^2 + d^2$.

To divide $z_1$ by $z_2$:

$\frac{z_1}{z_2} = \frac{a + bi}{c + di} = \frac{a + bi}{c + di} \cdot \frac{c - di}{c - di}$
$= \frac{(a + bi)(c - di)}{c^2 + d^2}$
$= \frac{(ac + bd) + (bc - ad)i}{c^2 + d^2}$
$= \frac{ac + bd}{c^2 + d^2} + \frac{bc - ad}{c^2 + d^2}i$

**Example:**
$\frac{2 + 3i}{1 - i} = \frac{2 + 3i}{1 - i} \cdot \frac{1 + i}{1 + i}$
$= \frac{(2)(1) + (2)(i) + (3i)(1) + (3i)(i)}{1^2 + (-1)^2}$
$= \frac{2 + 2i + 3i + 3i^2}{1 + 1}$
$= \frac{2 + 5i - 3}{2}$
$= \frac{-1 + 5i}{2}$
$= -\frac{1}{2} + \frac{5}{2}i$

## 3. Modulus of a Complex Number

The **modulus** (or absolute value) of a complex number $z = a + bi$, denoted as $|z|$, represents its distance from the origin $(0,0)$ in the complex plane. It is calculated using the Pythagorean theorem.

$|z| = \sqrt{a^2 + b^2}$

**Properties of the Modulus:**
* $|z| \ge 0$
* $|z| = 0$ if and only if $z = 0$
* $|z_1 z_2| = |z_1| |z_2|$
* $|\frac{z_1}{z_2}| = \frac{|z_1|}{|z_2|}$ (for $z_2 \ne 0$)
* $|z|^2 = z \cdot \bar{z}$ (where $\bar{z}$ is the complex conjugate)

**Example:**
For $z = 3 + 4i$:
$|z| = \sqrt{3^2 + 4^2} = \sqrt{9 + 16} = \sqrt{25} = 5$

For $z = -2i$:
$|z| = \sqrt{0^2 + (-2)^2} = \sqrt{4} = 2$
------
# Norm of a Vector with Complex Components

The concept of a vector's norm (or magnitude) extends naturally to vectors whose components are complex numbers. Just as with real vectors, the norm represents the "length" or "size" of the vector.

## 1. Definition of a Complex Vector

A complex vector is a vector where at least one of its components is a complex number. For example, a 2D complex vector $\mathbf{v}$ can be written as:

$\mathbf{v} = \begin{pmatrix} z_1 \\ z_2 \end{pmatrix}$

Where $z_1 = a_1 + b_1i$ and $z_2 = a_2 + b_2i$ are complex numbers.

In general, for an $n$-dimensional complex vector $\mathbf{v}$:

$\mathbf{v} = \begin{pmatrix} z_1 \\ z_2 \\ \vdots \\ z_n \end{pmatrix}$

Where each $z_k$ is a complex number.

## 2. The Dot Product (Inner Product) for Complex Vectors

Before defining the norm, it's crucial to understand the **Hermitian dot product** (or inner product) for complex vectors. Unlike the standard dot product for real vectors, one of the vectors is conjugated. This ensures that the norm squared is always a non-negative real number.

Let $\mathbf{u} = \begin{pmatrix} u_1 \\ u_2 \\ \vdots \\ u_n \end{pmatrix}$ and $\mathbf{v} = \begin{pmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{pmatrix}$ be two complex vectors.

The Hermitian dot product is defined as:

$\mathbf{u} \cdot \mathbf{v} = \mathbf{u}^H \mathbf{v} = \sum_{k=1}^{n} \bar{u_k} v_k$

Where $\bar{u_k}$ is the complex conjugate of $u_k$, and $\mathbf{u}^H$ denotes the conjugate transpose (or Hermitian transpose) of $\mathbf{u}$.

**Example:**
Let $\mathbf{u} = \begin{pmatrix} 1 + i \\ 2 - i \end{pmatrix}$ and $\mathbf{v} = \begin{pmatrix} 3 \\ 1 + 2i \end{pmatrix}$.

$\mathbf{u} \cdot \mathbf{v} = \overline{(1 + i)}(3) + \overline{(2 - i)}(1 + 2i)$
$= (1 - i)(3) + (2 + i)(1 + 2i)$
$= (3 - 3i) + (2 + 4i + i + 2i^2)$
$= (3 - 3i) + (2 + 5i - 2)$
$= (3 - 3i) + (5i)$
$= 3 + 2i$

## 3. Calculating the Norm of a Complex Vector

The norm of a complex vector $\mathbf{v}$, denoted as $||\mathbf{v}||$, is defined as the square root of the Hermitian dot product of the vector with itself.

$||\mathbf{v}|| = \sqrt{\mathbf{v} \cdot \mathbf{v}} = \sqrt{\sum_{k=1}^{n} \bar{v_k} v_k}$

Since $\bar{v_k} v_k = |v_k|^2$ (the squared modulus of the complex component $v_k$), the formula simplifies to:

$||\mathbf{v}|| = \sqrt{\sum_{k=1}^{n} |v_k|^2}$

This is often called the **Euclidean norm** or **$L_2$ norm** for complex vectors.

**Steps to calculate the norm:**
1.  For each complex component $v_k$, calculate its modulus squared: $|v_k|^2 = (\text{Re}(v_k))^2 + (\text{Im}(v_k))^2$.
2.  Sum all these squared moduli.
3.  Take the square root of the sum.

**Example:**
Let $\mathbf{v} = \begin{pmatrix} 1 + i \\ 2 - i \end{pmatrix}$.

1.  Calculate the modulus squared for each component:
    *   $|1 + i|^2 = 1^2 + 1^2 = 1 + 1 = 2$
    *   $|2 - i|^2 = 2^2 + (-1)^2 = 4 + 1 = 5$

2.  Sum the squared moduli:
    $2 + 5 = 7$

3.  Take the square root of the sum:
    $||\mathbf{v}|| = \sqrt{7}$

**Another Example:**
Let $\mathbf{w} = \begin{pmatrix} 3 \\ 4i \\ 1 - 2i \end{pmatrix}$.

1.  Calculate the modulus squared for each component:
    *   $|3|^2 = 3^2 + 0^2 = 9$
    *   $|4i|^2 = 0^2 + 4^2 = 16$
    *   $|1 - 2i|^2 = 1^2 + (-2)^2 = 1 + 4 = 5$

2.  Sum the squared moduli:
    $9 + 16 + 5 = 30$

3.  Take the square root of the sum:
    $||\mathbf{w}|| = \sqrt{30}$

## 4. Why the Conjugate is Important

If we didn't use the conjugate in the dot product, we might end up with a complex number for the "length squared," which doesn't make physical sense.

Consider $\mathbf{v} = \begin{pmatrix} i \end{pmatrix}$.
If we used a simple dot product without conjugation: $i \cdot i = i^2 = -1$. The square root of -1 is $i$, which is not a positive real number representing length.

Using the Hermitian dot product:
$\mathbf{v} \cdot \mathbf{v} = \bar{i} \cdot i = (-i)(i) = -i^2 = -(-1) = 1$.
Then $||\mathbf{v}|| = \sqrt{1} = 1$. This is a real, non-negative length, as expected.

The use of the complex conjugate ensures that the norm squared is always a real, non-negative value, consistent with the geometric interpretation of length.

--------
# Orthogonal Complements

In linear algebra, the concept of an **orthogonal complement** is a fundamental idea that extends the geometric notion of perpendicularity to higher-dimensional vector spaces. It's crucial for understanding projections, least squares, and the structure of vector spaces.

## 1. Prerequisites: Inner Product and Orthogonality

Before defining orthogonal complements, let's quickly review two key concepts:

### a. Inner Product (Dot Product)
An inner product is a generalization of the dot product. For two vectors $\mathbf{u}$ and $\mathbf{v}$ in a vector space $V$:
*   In $\mathbb{R}^n$, the standard dot product is $\mathbf{u} \cdot \mathbf{v} = \sum_{i=1}^n u_i v_i$.
*   In $\mathbb{C}^n$, the standard Hermitian inner product is $\mathbf{u} \cdot \mathbf{v} = \sum_{i=1}^n \bar{u_i} v_i$.

The inner product allows us to define angles and lengths in a vector space.

### b. Orthogonality
Two vectors $\mathbf{u}$ and $\mathbf{v}$ are **orthogonal** (or perpendicular) if their inner product is zero:

$\mathbf{u} \cdot \mathbf{v} = 0$

A vector $\mathbf{v}$ is orthogonal to a **subspace** $W$ if $\mathbf{v}$ is orthogonal to *every* vector in $W$.

## 2. Definition of the Orthogonal Complement

Let $W$ be a subspace of an inner product space $V$. The **orthogonal complement of $W$**, denoted as $W^\perp$ (read as "W perp"), is the set of all vectors in $V$ that are orthogonal to every vector in $W$.

Formally:

$W^\perp = \{ \mathbf{v} \in V \mid \mathbf{v} \cdot \mathbf{w} = 0 \text{ for all } \mathbf{w} \in W \}$

## 3. Key Properties of Orthogonal Complements

### a. $W^\perp$ is a Subspace
The orthogonal complement $W^\perp$ is always a subspace of $V$.
*   It contains the zero vector (since $\mathbf{0} \cdot \mathbf{w} = 0$ for any $\mathbf{w}$).
*   It is closed under vector addition: If $\mathbf{v}_1, \mathbf{v}_2 \in W^\perp$, then $(\mathbf{v}_1 + \mathbf{v}_2) \cdot \mathbf{w} = \mathbf{v}_1 \cdot \mathbf{w} + \mathbf{v}_2 \cdot \mathbf{w} = 0 + 0 = 0$. So $\mathbf{v}_1 + \mathbf{v}_2 \in W^\perp$.
*   It is closed under scalar multiplication: If $\mathbf{v} \in W^\perp$ and $c$ is a scalar, then $(c\mathbf{v}) \cdot \mathbf{w} = c(\mathbf{v} \cdot \mathbf{w}) = c(0) = 0$. So $c\mathbf{v} \in W^\perp$.

### b. Intersection with $W$
The only vector common to both $W$ and $W^\perp$ is the zero vector:

$W \cap W^\perp = \{ \mathbf{0} \}$

This is because if $\mathbf{v} \in W$ and $\mathbf{v} \in W^\perp$, then $\mathbf{v}$ must be orthogonal to itself, meaning $\mathbf{v} \cdot \mathbf{v} = 0$. The only vector whose inner product with itself is zero is the zero vector (for positive-definite inner products).

### c. Direct Sum Decomposition
For any finite-dimensional inner product space $V$ and any subspace $W$, $V$ can be expressed as the **direct sum** of $W$ and $W^\perp$:

$V = W \oplus W^\perp$

This means that every vector $\mathbf{v} \in V$ can be uniquely written as the sum of a vector from $W$ and a vector from $W^\perp$:

$\mathbf{v} = \mathbf{w} + \mathbf{w}^\perp$, where $\mathbf{w} \in W$ and $\mathbf{w}^\perp \in W^\perp$.

### d. Dimension Relationship
If $V$ is finite-dimensional, then:

$\dim(V) = \dim(W) + \dim(W^\perp)$

### e. Double Orthogonal Complement
The orthogonal complement of the orthogonal complement of $W$ is $W$ itself:

$(W^\perp)^\perp = W$

## 4. Finding the Orthogonal Complement

Let $W$ be a subspace spanned by a set of vectors $\{ \mathbf{w}_1, \mathbf{w}_2, \dots, \mathbf{w}_k \}$.
A vector $\mathbf{v}$ is in $W^\perp$ if and only if $\mathbf{v}$ is orthogonal to *each* of the spanning vectors $\mathbf{w}_i$.

This means $\mathbf{v} \cdot \mathbf{w}_i = 0$ for all $i=1, \dots, k$.

If we form a matrix $A$ whose rows (or columns) are the spanning vectors of $W$, then $W^\perp$ is related to the null space of $A$.

**Specifically:**
*   If $W = \text{span}\{\mathbf{w}_1, \dots, \mathbf{w}_k\}$, and we form a matrix $A$ where the **rows** are $\mathbf{w}_1^T, \dots, \mathbf{w}_k^T$, then $W^\perp = \text{Null}(A)$.
*   If $W = \text{Col}(A)$ (the column space of $A$), then $W^\perp = \text{Null}(A^T)$.
*   If $W = \text{Row}(A)$ (the row space of $A$), then $W^\perp = \text{Null}(A)$.

These relationships are part of the **Four Fundamental Subspaces** theorem.

**Example in $\mathbb{R}^3$:**
Let $W$ be the subspace spanned by $\mathbf{w}_1 = \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}$ (the x-axis).
We are looking for all vectors $\mathbf{v} = \begin{pmatrix} x \\ y \\ z \end{pmatrix}$ such that $\mathbf{v} \cdot \mathbf{w}_1 = 0$.

$\begin{pmatrix} x \\ y \\ z \end{pmatrix} \cdot \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix} = x(1) + y(0) + z(0) = x = 0$

So, $W^\perp = \{ \begin{pmatrix} 0 \\ y \\ z \end{pmatrix} \mid y, z \in \mathbb{R} \}$. This is the yz-plane, which is indeed orthogonal to the x-axis.

**Example with a plane in $\mathbb{R}^3$:**
Let $W$ be the plane defined by the equation $x - 2y + 3z = 0$.
This plane is the null space of the matrix $A = \begin{pmatrix} 1 & -2 & 3 \end{pmatrix}$.
So, $W = \text{Null}(A)$.

The orthogonal complement $W^\perp$ is the row space of $A$:
$W^\perp = \text{Row}(A) = \text{span} \{ \begin{pmatrix} 1 \\ -2 \\ 3 \end{pmatrix} \}$.
This means $W^\perp$ is the line passing through the origin in the direction of the normal vector to the plane. This makes perfect geometric sense.
