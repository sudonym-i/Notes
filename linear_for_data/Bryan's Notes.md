***September 4th
- Underscoring is the standard for indicating vectors; every vector is a column by default; transposed is a column for indication
- All vectors can be decomposed into a linear combination of other vectors
- W (subspace) = span{v1, v2} = {k1v1 + k2v2}
- For linear independence, EVERY vector need to be outside the span of EVERY OTHER vector
- Set {v1, v2, ..., vk} is linearly independent iff the following holds: if i=1kcivi=0, then ci = 0 for all i
- If the Kernel or Null space is the zero vector, the columns are linearly independent
- Ker(A) = Null(A) = {c E R^n such that Ac = 0}

***September 9th
- Span{**v1, ... vk**} = {c1v1 + c2v2 + ... + ckvk such that ci E R} = w (subspace of Rn)
- Can have many vectors within Rn; k can be > or < than n
- n is the number of entries in the column vector
- u . v = E uivi = <u, v> = u^T v = ||u|| ||v|| cos(0)
- w(perp) is perpendicular compliment to W = {w E R4, such that w . v = 0 where v E W} = Ker(B) if B = (v1 v2) as (v1 v2) x = 0 and x is the Kernel

***September 11th
- if c1v1 + c2v2 + ... = 0, then c1 = c2 = ... = 0
- Ac = 0, then c = 0
- Rank is the dimension of the image space spanned by the vectors (the basis of the space)
- If C is a matrix representing 2 vectors that are linearly independent, then CT * C forms the identity matrix; called the Gram-Schmidt
- Let A be a set of three vectors not necessarily linearly independent and W as the span of A, C = orth(A), and F = null(A'), the F' * C = 0 matrix and rref([C F]) = Identity