## Hash Table

## Overview
A hash table is a data structure that implements an associative array (map) abstract data type. It uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.

## Core Concept: The Hash Function

The hash function is the heart of the hash table. It transforms a key (which could be a string, number, object, etc.) into an array index.

### Properties of Good Hash Functions

1. **Deterministic**: Same key always produces same hash value
2. **Uniform Distribution**: Keys spread evenly across buckets to minimize collisions
3. **Fast Computation**: O(1) time to compute hash
4. **Minimize Collisions**: Different keys should rarely hash to same index

### Common Hash Function Techniques

**Division Method**: `hash(key) = key % table_size`
- Simple and fast
- Table size should be prime to reduce clustering

**Multiplication Method**: `hash(key) = floor(m * (key * A mod 1))`
- A is constant between 0 and 1 (often golden ratio ≈ 0.618)
- Works well with any table size

**String Hashing**: For string keys
```
hash = 0
for each character c in string:
    hash = (hash * prime) + value(c)
return hash % table_size
```
- Common primes: 31, 37, 53
- Polynomial rolling hash

### Hash Function Quality: Critical Considerations

A quality hash function directly impacts hash table performance. Poor hash functions lead to clustering and collisions, degrading O(1) operations to O(n).

#### Essential Requirements

1. **Repeatability (Deterministic)**
   - Given key must ALWAYS produce the same hash value
   - If `hash("apple") = 47` once, it must always equal 47
   - Non-negotiable requirement for correctness

2. **Uniform Distribution**
   - Hash values should spread evenly across entire range
   - Prevents all keys from clustering in small subset of buckets
   - Goal: Each bucket has approximately equal probability of being chosen

3. **Avoid Clustering (especially for linear probing)**
   - Keys should not hash to consecutive indices
   - Clustering causes long probe sequences
   - Particularly problematic with linear probing

#### Hashing Primitive Values (Integers)

**Simple case**: Integer keys in small range
- If values are already distributed (e.g., random integers), use them directly as hash values
- If values fit table size range, minimal processing needed

**Problem**: Small range integers (e.g., 1 to 100)
- Using directly causes clustering in first 100 buckets
- **Solution**: Bit shifting or multiplication to expand range
- Example: `hash = (key * large_prime) % table_size`

#### Hashing Strings: Common Pitfalls

**Bad Hash Function #1: Sum of ASCII values**
```java
long hash1(String str) {
    long h = 0;
    for (int i = 0; i < str.length(); i++) {
        h += str.charAt(i);
    }
    return h;
}
```

**Critical Problems:**
1. **Ignores character order**
   - "dog" and "god" produce identical hash values
   - hash("dog") = 100 + 111 + 103 = 314
   - hash("god") = 103 + 111 + 100 = 314
   - Many anagrams collide!

2. **Limited range for short strings**
   - For table size 10,000, only very long strings reach higher values
   - Short strings cluster in low indices
   - Poor distribution

**Better Hash Function #2: Positional weighting**
```java
long hash2(String str) {
    long h = 0;
    for (int i = 0; i < str.length(); i++) {
        h = h * 31 + str.charAt(i);
    }
    return h;
}
```

**Why this works:**
- Character position matters: "dog" ≠ "god"
  - hash("dog") = ((100 × 31 + 111) × 31) + 103
  - hash("god") = ((103 × 31 + 111) × 31) + 100
  - Different results!
- Multiplier (31) spreads values across range
- Used by Java String.hashCode()

**Why 31?**
- Prime number (reduces patterns/collisions)
- Odd (better bit mixing)
- Small enough for fast computation
- Can be optimized: `31 * h = (h << 5) - h` (bit shift)

#### Hashing Complex Objects

**Strategy**: Combine hash values of key components

**Example**: Hashing a Person object with name and age
```java
class Person {
    String name;
    int age;

    public int hashCode() {
        int result = 17;  // Start with prime
        result = 31 * result + name.hashCode();
        result = 31 * result + age;
        return result;
    }
}
```

**Recipe:**
1. Start with small prime (e.g., 17)
2. For each significant field:
   - Multiply result by prime (e.g., 31)
   - Add field's hash value
3. Combines values while maintaining order sensitivity

#### Implementation in Java

**The hashCode() method:**
- Every Java object inherits `hashCode()` from Object class
- Returns an `int` value (not long, despite examples above)
- Used automatically by HashMap, HashSet, etc.

**Critical Contract:**
- If `a.equals(b)` is true, then `a.hashCode() == b.hashCode()` MUST be true
- Converse not required: different objects can have same hash (collisions OK)
- **Violating this breaks hash tables!**

**Example violation:**
```java
// BROKEN CODE - DO NOT USE
class BadPerson {
    String name;

    public boolean equals(Object o) {
        return ((BadPerson)o).name.equals(this.name);
    }

    // hashCode() not overridden - uses Object.hashCode()
    // Different instances with same name will have different hashes
    // Breaks hash table lookups!
}
```

**Correct implementation:**
```java
class GoodPerson {
    String name;

    public boolean equals(Object o) {
        if (!(o instanceof GoodPerson)) return false;
        return ((GoodPerson)o).name.equals(this.name);
    }

    public int hashCode() {
        return name.hashCode();  // Consistent with equals
    }
}
```

**Modern Java shortcut:**
```java
public int hashCode() {
    return Objects.hash(name, age, email);  // Java 7+
}
```

### The Pigeonhole Principle and Collisions

**Why collisions are inevitable:**
- If we have unlimited possible keys but finite array size, collisions must occur
- Example: Hashing all possible strings into array of size 1000
- Even with perfect distribution, collisions happen as load factor increases

**Birthday Paradox**: With just √m items in a table of size m, probability of collision is ~50%

## How Hash Tables Work

### Core Components

1. **Hash Function**: Maps keys to array indices
   - Takes a key as input
   - Returns an integer (hash code)
   - Should distribute keys uniformly across the array

2. **Array/Buckets**: Storage for key-value pairs
   - Fixed or dynamically sized
   - Each index may store one or more entries

3. **Collision Resolution**: Handles multiple keys mapping to the same index

### Basic Operations

**Insertion**:
1. Compute hash of the key: `index = hash(key) % array_size`
2. Store key-value pair at the computed index
3. Handle collision if necessary

**Lookup**:
1. Compute hash of the key
2. Access the bucket at that index
3. Find the matching key (if collision resolution is used)

**Deletion**:
1. Compute hash of the key
2. Find the entry in the bucket
3. Remove the key-value pair

## Collision Resolution Strategies

When two keys hash to the same index, we need a strategy to handle this collision.

### 1. Chaining (Separate Chaining)

Each bucket contains a linked list (or other data structure like binary search tree) that stores all entries with the same hash.

**How it works:**
```
Table[0] -> NULL
Table[1] -> (key1, val1) -> (key2, val2) -> NULL
Table[2] -> (key3, val3) -> NULL
Table[3] -> NULL
```

**Detailed Analysis:**
- **Insertion**: O(1) - add to front of list
- **Search**: O(1 + α) where α is load factor, must traverse chain
- **Delete**: O(1 + α) - find then remove from list

**When to use:**
- Unknown number of elements
- High load factors acceptable
- Memory overhead acceptable

**Improvements:**
- Use self-balancing BST instead of linked list (Java 8 HashMap does this)
- Reduces worst-case search to O(log n) per bucket

### 2. Open Addressing

All entries stored directly in the array. When collision occurs, probe for next available slot using a probe sequence.

**General formula**: `index = (hash(key) + probe(i)) % table_size`

#### Linear Probing

**Probe sequence**: `probe(i) = i`
- Try: hash(k), hash(k)+1, hash(k)+2, ...

**Primary Clustering Problem:**
- Long runs of occupied slots form
- Increases search time for nearby keys
- New insertions more likely to extend clusters

**Example:**
```
Insert keys hashing to index 3:
[_, _, _, A, _, _, _]  // Insert A at 3
[_, _, _, A, B, _, _]  // Insert B, collision, probe to 4
[_, _, _, A, B, C, _]  // Insert C, collision, probe to 5
// Cluster grows!
```

#### Quadratic Probing

**Probe sequence**: `probe(i) = i²`
- Try: hash(k), hash(k)+1, hash(k)+4, hash(k)+9, ...

**Benefits:**
- Reduces primary clustering
- Keys don't form long contiguous blocks

**Drawbacks:**
- Secondary clustering: keys with same hash follow same probe sequence
- May not probe all slots (need table size to be prime or power of 2)

#### Double Hashing

**Probe sequence**: `probe(i) = i * hash2(key)`
- Uses two hash functions
- `hash2(key)` should never return 0
- Common choice: `hash2(key) = prime - (key % prime)` where prime < table_size

**Benefits:**
- Best distribution among open addressing methods
- Different keys with same initial hash follow different probe sequences
- Minimizes both primary and secondary clustering

**Example:**
```
hash1(key) = 3
hash2(key) = 5
Probe sequence: 3, 8, 13, 18, 23, ... (mod table_size)
```

### 3. Open Addressing: Deletion Challenges

**Problem**: Can't just delete entry - breaks probe sequence for later entries

**Solution**: Tombstones (lazy deletion)
- Mark slot as "deleted" rather than empty
- Search continues past tombstones
- Insert can reuse tombstone slots

**Trade-off**: Too many tombstones degrade performance - need periodic rehashing

## Time Complexity

### Average Case (with good hash function and low load factor)

**All operations: O(1)**

**Why O(1)?**
- Hash computation: O(1)
- Array access: O(1)
- With low load factor and uniform distribution:
  - Chaining: Expected chain length ≈ α (constant)
  - Open addressing: Expected probes ≈ 1/(1-α) (constant when α < 0.7)

### Worst Case

**All operations: O(n)**

**When does this occur?**
1. **Poor hash function**: All keys hash to same bucket
   - Chaining: Single chain with n elements
   - Open addressing: Must probe through all n slots
2. **Adversarial input**: Attacker deliberately chooses keys that collide
3. **High load factor**: Near-full table increases probe lengths

### Space Complexity

**O(n)** where n is number of entries

**But actual space depends on implementation:**
- **Chaining**: O(n + m) where m is table size
  - Additional pointer overhead per entry
  - Typically m ≈ n, so effectively O(n)

- **Open addressing**: O(m) where m ≥ n
  - No pointer overhead
  - More wasted empty slots
  - Memory is contiguous (better cache performance)

### Load Factor Impact (α = n / m)

The load factor is the single most important performance metric.

**Chaining:**
- Expected chain length = α
- Search cost ≈ 1 + α/2 (successful search)
- Can exceed α = 1 (more entries than buckets)

**Open Addressing:**
- **Cannot exceed α = 1** (table becomes full)
- Search cost grows rapidly as α approaches 1

**Expected probes for successful search:**
- Linear probing: `½(1 + 1/(1-α))`
  - α = 0.5: ~1.5 probes
  - α = 0.75: ~2.5 probes
  - α = 0.9: ~5.5 probes

- Double hashing: `-(1/α) * ln(1-α)`
  - α = 0.5: ~1.4 probes
  - α = 0.75: ~1.8 probes
  - α = 0.9: ~2.6 probes

**Typical thresholds:**
- Java HashMap: resize at α = 0.75
- Python dict: resize at α = 2/3
- C++ unordered_map: resize at α = 1.0

### Resizing and Rehashing

**When to resize:** Load factor exceeds threshold

**Process:**
1. Allocate new array (typically 2x size)
2. Rehash every entry into new array
3. Free old array

**Cost:**
- Single resize: O(n) to rehash all entries
- **Amortized cost: O(1)** per insertion
  - Cost spread over many insertions
  - Doubling strategy: each element rehashed O(log n) times over table's lifetime

**Why doubling works:**
```
Insertions: 1, 2, 4, 8, 16, ...
Resize costs: 1, 2, 4, 8, 16, ...
Total cost after n insertions: 1 + 2 + 4 + ... + n ≈ 2n
Average cost per insertion: 2n/n = 2 = O(1)
```

## Advantages
- Fast average-case lookups, insertions, deletions
- Flexible key types (with appropriate hash function)
- Cache-friendly (open addressing)

## Disadvantages
- No ordering of elements
- Poor worst-case performance
- Requires good hash function
- Wasted space or collision overhead
- Resizing can be expensive

## Advanced Topics

### Universal Hashing

**Problem**: Fixed hash function can be exploited with adversarial input

**Solution**: Choose hash function randomly from a universal family at runtime

**Universal family property**: For any two distinct keys k₁, k₂:
```
Pr[h(k₁) = h(k₂)] ≤ 1/m
```
where m is table size and probability is over random choice of h

**Example family**: `h(k) = ((a*k + b) mod p) mod m`
- p is prime > maximum key value
- a, b chosen randomly where 1 ≤ a < p and 0 ≤ b < p

**Benefit**: Guarantees expected O(1) operations regardless of input

### Perfect Hashing

**Goal**: Zero collisions for static set of keys (no insertions/deletions)

**Two-level hashing:**
1. First level: Hash n keys into m buckets (with collisions)
2. Second level: Each bucket i with nᵢ keys gets secondary hash table of size nᵢ²
   - With nᵢ² slots, can find perfect hash function with zero collisions

**Space**: O(n) total (mathematical proof shows expected space is linear)

**Lookups**: O(1) worst-case (guaranteed no collisions)

**Use cases**: Compiler keyword tables, reserved words, constants

### Cuckoo Hashing

**Idea**: Use two hash functions and two tables

**Insertion:**
1. Try to insert in table1[hash1(key)]
2. If occupied, evict existing item and insert new one
3. Evicted item tries table2[hash2(key)]
4. If occupied, evict again and go back to table1
5. Continue until all items placed (or cycle detected)

**Lookup**: O(1) worst-case - check both positions only

**Deletion**: O(1) - remove from whichever table contains it

**Problem**: Cycles can form, requiring rebuild with new hash functions

### Robin Hood Hashing

**Enhancement to open addressing:**
- Track "probe distance" for each entry
- When inserting, if new key has probed further than existing key at position, swap them
- Rich entries (close to home) give way to poor entries (far from home)

**Benefit**: Reduces variance in probe lengths, more predictable performance

### Bloom Filters (Related Structure)

**Space-efficient probabilistic data structure**
- Tests whether element is in set
- Can have false positives, but no false negatives
- Much more space-efficient than hash table for membership testing

## Comparison with Other Data Structures

| Operation | Hash Table | BST | Array (unsorted) | Array (sorted) |
|-----------|------------|-----|------------------|----------------|
| Search    | O(1) avg   | O(log n) | O(n) | O(log n) |
| Insert    | O(1) avg   | O(log n) | O(1) | O(n) |
| Delete    | O(1) avg   | O(log n) | O(n) | O(n) |
| Min/Max   | O(n)       | O(log n) | O(n) | O(1) |
| Ordered traversal | No | Yes | No | Yes |
| Space     | O(n)       | O(n) | O(n) | O(n) |

**When to use hash tables:**
- Need fast lookups/insertions/deletions
- Don't need ordering
- Keys are hashable
- Can tolerate some wasted space

**When NOT to use hash tables:**
- Need ordered traversal
- Need range queries (find all keys in range)
- Need min/max operations
- Extreme memory constraints
- Need predictable worst-case performance

## Real-World Applications

**Databases:**
- Hash indexes for equality lookups
- Join operations (hash join)
- Deduplication during aggregation

**Caching:**
- In-memory caches (Redis, Memcached)
- CPU caches (set-associative caches use hash-like indexing)
- Browser caches

**Programming Languages:**
- Symbol tables in compilers/interpreters
- Object property lookup (JavaScript objects)
- Dictionary/map implementations (Python dict, Java HashMap, C++ unordered_map)
- Set implementations (HashSet)

**Algorithms:**
- Two-sum problem: O(n) with hash table vs O(n²) brute force
- Finding duplicates: O(n) with hash table
- Frequency counting
- Subarray sum problems

**Security:**
- Password storage (cryptographic hash functions)
- Digital signatures
- Blockchain (hash pointers)

**Systems:**
- File systems (directory lookups)
- Network routing tables
- DNS lookup
- Load balancing (consistent hashing)

