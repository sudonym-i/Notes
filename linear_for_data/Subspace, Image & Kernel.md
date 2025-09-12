# Linear Algebra Core Concepts (Simplified & Intuitive)

## 1. Linear Independence

**Definition:**  
A set of vectors $\{v_1, v_2, \dots, v_k\}$ is *linearly independent* if the only way their weighted sum equals the zero vector is if all weights (scalars) are zero:
$$
c_1v_1 + c_2v_2 + \dots + c_kv_k = 0 \implies c_1 = c_2 = \dots = c_k = 0
$$

**Intuition:**  
- No vector "copies" another; you can't build one from the others.
- Each vector points in a genuinely new direction.
- The set contains NO redundancy.

**How to Check:**  
- Put the vectors as columns in a matrix $A$.
- Solve $Ax = 0$.
- If $x = 0$ is the *only* solution, the vectors are independent.
- In other words: the *kernel (null space)* of $A$ just contains the zero vector.

---

## 2. Linear Transformations

**Definition:**  
A function $T: V \to W$ is a *linear transformation* if, for any vectors $u, v$ and any scalar $c$:
1. $T(u + v) = T(u) + T(v)$  (*additivity*)
2. $T(cu) = cT(u)$  (*homogeneity*)

**Intuition:**  
- Linear transformations keep addition and scaling "working the same" after the transformation.
- They always send the origin to the origin.
- Examples: rotations, reflections, scaling, shearing.

**Matrix Representation:**  
Every linear transformation from $\mathbb{R}^n$ to $\mathbb{R}^m$ can be written as multiplying by an $m \times n$ matrix $A$:
$$
T(x) = Ax
$$
The columns of $A$ are the images of the standard basis vectors:
$$
A = [T(e_1)\ T(e_2)\ \dots\ T(e_n)]
$$

---

## 3. Subspace

**Definition:**  
A *subspace* $W$ of vector space $V$ is a non-empty subset of $V$ that itself forms a vector space (using the usual addition and scalar multiplication).

**To be a Subspace, $W$ must:**
1. Contain the zero vector ($0 \in W$).
2. Be closed under addition: If $u, v \in W$, then $u + v \in W$.
3. Be closed under scalar multiplication: If $u \in W$ and $c$ is any scalar, then $cu \in W$.

**Examples:**
- All multiples of a single nonzero vector (line through origin).
- All vectors in a plane through the origin.
- *Span* of any set of vectors.
- *Kernel* (null space) of a matrix $A$ ($Ax = 0$).
- *Column space* (span of columns) of $A$.

---

## 4. Basis Vectors

**Definition:**  
A *basis* for a vector space $V$ is a set $B = \{b_1, b_2, \dots, b_n\}$ such that:
1. $B$ is linearly independent.
2. $B$ spans $V$ (every vector in $V$ can be made from $B$).

**Intuition:**  
- A basis is the smallest set of vectors needed to "build" the whole space.
- It gives a coordinate system for the space.
- Every vector in $V$ can be written *uniquely* as a combination of the basis vectors.

**Key Properties:**  
- The number of vectors in any basis for $V$ is always the same, called the *dimension* of $V$.
- For $\mathbb{R}^n$, the *standard basis* is $\{e_1, e_2, \dots, e_n\}$, where $e_i$ has a 1 in the $i$th place and zeros elsewhere.

---

### Important Fact

For every *linear transformation* $T: V \to W$ between finite-dimensional vector spaces, there is a unique matrix $A$ so that $T(\mathbf{v}) = A\mathbf{v}$ for all $\mathbf{v} \in V$.  
If $V = \mathbb{R}^n$ and $W = \mathbb{R}^m$, then $A$ is $m \times n$.

---

# Basis Vectors in Linear Algebra

## What is a Basis?

A *basis* is a special set of vectors that:
1. Are linearly independent.
2. Span the space (can reach every vector in the space).

**Key Points:**
- *Minimal Spanning Set:* Removing any vector destroys the spanning property.
- *Unique Coordinates:* Every vector can be written in one and only one way as a combination of the basis vectors.
- *Acts like axes:* Just like x, y, z axes, basis vectors provide directions.
- *Dimension:* The number of vectors in any basis = the dimension of the space.

**Examples:**
- *Standard basis for $\mathbb{R}^2$*: $\left\{ \begin{pmatrix} 1 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 1 \end{pmatrix} \right\}$
- *Standard basis for $\mathbb{R}^3$*: $\left\{ \begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}, \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix} \right\}$
- Other bases are possible, e.g. $\left\{ \begin{pmatrix} 1 \\ 1 \end{pmatrix}, \begin{pmatrix} -1 \\ 1 \end{pmatrix} \right\}$ for $\mathbb{R}^2$.

**Why are Bases Important?**
- They help us understand the structure and dimension of spaces.
- They allow us to assign coordinates.
- Transformations are defined by their action on basis vectors.
- They simplify problems.

---

# Finding the Matrix for a Linear Transformation

## The Idea

Every linear transformation $T: \mathbb{R}^n \to \mathbb{R}^m$ can be written as multiplying by a matrix $A$:
$$
T(\mathbf{x}) = A\mathbf{x}
$$
To *find* $A$, look at what $T$ does to the standard basis vectors.

## How to Do It

1. For $\mathbb{R}^n$, the standard basis vectors are:
   - $\mathbf{e}_1$, $\mathbf{e}_2$, ..., $\mathbf{e}_n$
2. Every vector $\mathbf{x}$ can be written as:
   $$\mathbf{x} = x_1\mathbf{e}_1 + x_2\mathbf{e}_2 + \cdots + x_n\mathbf{e}_n$$
3. Because $T$ is linear:
   $$T(\mathbf{x}) = x_1T(\mathbf{e}_1) + x_2T(\mathbf{e}_2) + \cdots + x_nT(\mathbf{e}_n)$$
4. Create $A$ by putting $T(\mathbf{e}_1), T(\mathbf{e}_2), \dots$ as its columns:
   $$
   A = \left[ T(\mathbf{e}_1)\ T(\mathbf{e}_2)\ \cdots\ T(\mathbf{e}_n) \right]
   $$
5. Then $A\mathbf{x}$ produces $T(\mathbf{x})$.

## Examples

1. **Rotation in $\mathbb{R}^2$ by $\theta$:**
   - $T(\mathbf{e}_1) = \begin{pmatrix} \cos\theta \\ \sin\theta \end{pmatrix}$
   - $T(\mathbf{e}_2) = \begin{pmatrix} -\sin\theta \\ \cos\theta \end{pmatrix}$
   - $A = \begin{pmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{pmatrix}$

2. **Projection onto x-axis in $\mathbb{R}^2$:**
   - $T(\mathbf{e}_1) = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$
   - $T(\mathbf{e}_2) = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$
   - $A = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}$

3. **$T: \mathbb{R}^3 \to \mathbb{R}^2$, $T\begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \begin{pmatrix} x_1 - x_2 \\ x_2 + x_3 \end{pmatrix}$:**
   - $T(\mathbf{e}_1) = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$
   - $T(\mathbf{e}_2) = \begin{pmatrix} -1 \\ 1 \end{pmatrix}$
   - $T(\mathbf{e}_3) = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$
   - $A = \begin{pmatrix} 1 & -1 & 0 \\ 0 & 1 & 1 \end{pmatrix}$

---

# Matrix Multiplication as a Linear Combination of Columns

**Core Idea:**  
Multiplying a matrix $A$ by vector $\mathbf{x}$ ($A\mathbf{x}$) means taking a *weighted sum* of $A$'s columns, where the weights come from $\mathbf{x}$.

**Definition:**  
Let $A$ have columns $\mathbf{a}_1, ..., \mathbf{a}_n$ and $\mathbf{x}$ = $(x_1, ..., x_n)^T$:
$$
A\mathbf{x} = x_1\mathbf{a}_1 + x_2\mathbf{a}_2 + \cdots + x_n\mathbf{a}_n
$$

**Why This Matters:**
- Geometrically, $A\mathbf{x}$ is just "mixing" the columns of $A" using $\mathbf{x}$ as instructions.
- The set of all possible $A\mathbf{x}$ is the *column space* (span of columns).
- If $T(\mathbf{x}) = A\mathbf{x}$, outputs always land in the column space.
- $A\mathbf{x} = \mathbf{b}$ has a solution *only if* $\mathbf{b}$ is in the column space of $A$.

**Example:**
Let $A = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{pmatrix}$, $\mathbf{x} = \begin{pmatrix} 2 \\ -1 \\ 3 \end{pmatrix}$

$A\mathbf{x} = 2\begin{pmatrix} 1 \\ 4 \\ 7 \end{pmatrix} + (-1)\begin{pmatrix} 2 \\ 5 \\ 8 \end{pmatrix} + 3\begin{pmatrix} 3 \\ 6 \\ 9 \end{pmatrix} = \begin{pmatrix} 9 \\ 21 \\ 33 \end{pmatrix}$

Alternatively, you get the same result using row-wise dot products.

---

# Image and Kernel (Column Space & Null Space)

## 1. Image (Column Space / Range)

**Definition:**  
The *Image* of matrix $A$ (written as $\text{Im}(A)$ or $\text{Col}(A)$) is all vectors $\mathbf{b}$ for which $A\mathbf{x} = \mathbf{b}$ has a solution.  
It's the *span of the columns* of $A$.

**Intuition:**  
- The image is all the output vectors you can produce with $A$.
- It's the "reach" of the transformation.

**Properties:**  
- The image is a subspace of $\mathbb{R}^m$.
- Its dimension is the *rank* of $A$.
- To find a basis: row-reduce $A$, and pick the columns in the original $A$ matching the pivot columns.

**Example:**  
Let $A = \begin{pmatrix} 1 & 2 & 0 \\ 0 & 1 & 1 \\ 1 & 3 & 1 \end{pmatrix}$
- Row reduce to REF: $\begin{pmatrix} 1 & 2 & 0 \\ 0 & 1 & 1 \\ 0 & 0 & 0 \end{pmatrix}$
- Pivot columns: 1 and 2.
- Basis: $\left\{ \begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}, \begin{pmatrix} 2 \\ 1 \\ 3 \end{pmatrix} \right\}$
- Rank: 2

---

## 2. Kernel (Null Space)

**Definition:**  
The *Kernel* of $A$ ($\text{Ker}(A)$ or $\text{Null}(A)$) is all vectors $\mathbf{x}$ such that $A\mathbf{x} = 0$.

**Intuition:**  
- The kernel is all vectors that get "flattened" to zero by $A$.
- It describes what gets lost by the transformation.

**Properties:**  
- The kernel is a subspace of $\mathbb{R}^n$.
- Its dimension is the *nullity* of $A$.
- To find a basis: Solve $A\mathbf{x} = 0$, write solutions using free variables, and the vectors attached to those free variables form a basis.

**Example:**  
Using $A$ from above:

Row-reduced form yields:
- $x_2 + x_3 = 0 \implies x_2 = -x_3$
- $x_1 + 2x_2 = 0 \implies x_1 = -2x_2 = 2x_3$

Set $x_3 = t$ (free):  
$\mathbf{x} = \begin{pmatrix} 2t \\ -t \\ t \end{pmatrix} = t \begin{pmatrix} 2 \\ -1 \\ 1 \end{pmatrix}$

- Basis for kernel: $\left\{ \begin{pmatrix} 2 \\ -1 \\ 1 \end{pmatrix} \right\}$
- Nullity: 1
