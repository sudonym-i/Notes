# Transformers in Machine Learning

A transformer is a deep learning model that processes sequential data, such as natural language, by weighing the importance of different parts of the input sequence. Unlike recurrent neural networks (RNNs), transformers do not require processing data in order, making them highly parallelizable and efficient.

## Intuitive Explanation

Imagine you're reading a long sentence, and you want to understand the meaning of a particular word. To do this, you don't just look at the words immediately before or after it. Instead, you consider how that word relates to *all* the other words in the sentence. Some words will be more important for understanding its meaning than others.

A transformer works similarly. When it processes a word in a sentence, it doesn't just look at its neighbors. It looks at every other word in the sentence and assigns an "attention score" to each of them, indicating how relevant they are to the current word. These scores are then used to create a weighted average of all the words, which becomes the new representation of the current word. This process is called "self-attention."

Now, imagine you have two people, one who is good at understanding the overall meaning of a sentence and another who is good at identifying specific grammatical relationships. A transformer uses multiple "attention heads," each acting like one of these specialized individuals, to capture different aspects of the relationships between words.

Finally, after understanding the relationships between words, the transformer passes this information through a standard neural network (a feed-forward network) to further process and refine the representation. This entire process is repeated multiple times in "encoder" and "decoder" layers, allowing the model to build up a sophisticated understanding of the input.

## Mathematical Explanation

Let's break down the core components of a transformer:

### 1. Input Embedding

First, each word (or token) in the input sequence is converted into a numerical vector. This is done using an embedding layer, which maps discrete tokens to continuous vector representations.
For a sequence of tokens $x_1, x_2, ..., x_n$, we get corresponding embeddings $e_1, e_2, ..., e_n$.

### 2. Positional Encoding

Since transformers don't inherently understand the order of words, we need to inject positional information. This is done by adding "positional encodings" to the input embeddings. These are typically sine and cosine functions of different frequencies:

$PE_{(pos, 2i)} = \sin(pos / 10000^{2i/d_{model}})$
$PE_{(pos, 2i+1)} = \cos(pos / 10000^{2i/d_{model}})$

Where:
* $pos$ is the position of the token in the sequence.
* $i$ is the dimension within the embedding vector.
* $d_{model}$ is the dimensionality of the model's embeddings.

The final input to the transformer block is the sum of the token embedding and its positional encoding: $x_i' = e_i + PE_i$.

### 3. Self-Attention Mechanism

The heart of the transformer is the self-attention mechanism. For each input vector $x_i'$, we create three new vectors:
* **Query (Q):** $Q = x_i' W^Q$
* **Key (K):** $K = x_i' W^K$
* **Value (V):** $V = x_i' W^V$

Where $W^Q, W^K, W^V$ are learnable weight matrices.

The attention score between a query vector $Q_i$ (for the $i$-th word) and a key vector $K_j$ (for the $j$-th word) is calculated as their dot product:

$score(Q_i, K_j) = Q_i \cdot K_j$

These scores are then scaled and passed through a softmax function to get attention weights:

$AttentionWeights_{ij} = \text{softmax}\left(\frac{Q_i \cdot K_j}{\sqrt{d_k}}\right)$

Where $d_k$ is the dimension of the key vectors, used for scaling to prevent large dot products from pushing the softmax into regions with tiny gradients.

Finally, the output of the self-attention for the $i$-th word is a weighted sum of the value vectors:

$Output_i = \sum_{j=1}^{n} AttentionWeights_{ij} \cdot V_j$

In matrix form, for an entire sequence:

$Attention(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$

### 4. Multi-Head Attention

Instead of performing a single attention function, transformers use "multi-head attention." This means the Q, K, and V matrices are split into $h$ "heads," and the attention function is applied independently to each head. The outputs from each head are then concatenated and linearly transformed:

$MultiHead(Q, K, V) = Concat(head_1, ..., head_h)W^O$
Where $head_i = Attention(QW_i^Q, KW_i^K, VW_i^V)$ and $W_i^Q, W_i^K, W_i^V, W^O$ are learnable weight matrices.

This allows the model to jointly attend to information from different representation subspaces at different positions.

### 5. Feed-Forward Network

After the multi-head attention layer, the output is passed through a position-wise fully connected feed-forward network. This network is applied independently to each position:

$FFN(x) = \max(0, xW_1 + b_1)W_2 + b_2$

This is typically a two-layer feed-forward network with a ReLU activation in between.

### 6. Residual Connections and Layer Normalization

Each sub-layer (multi-head attention and feed-forward network) in the transformer is wrapped with a residual connection and followed by layer normalization:

$LayerNorm(x + Sublayer(x))$

Residual connections help with training deep networks by allowing gradients to flow more easily. Layer normalization normalizes the inputs across the features, stabilizing training.

### 7. Encoder-Decoder Architecture

Transformers typically consist of an encoder and a decoder stack.

*   **Encoder:** The encoder takes the input sequence and produces a sequence of contextualized representations. It consists of $N$ identical layers, each with a multi-head self-attention mechanism and a position-wise feed-forward network.

*   **Decoder:** The decoder takes the encoder's output and generates the output sequence (e.g., translated text). It also consists of $N$ identical layers, but each layer has three sub-layers:
    1.  **Masked Multi-Head Self-Attention:** This is similar to the encoder's self-attention but with a mask to prevent attending to future positions in the output sequence during training (to ensure causality).
    2.  **Multi-Head Attention over Encoder Outputs:** This layer performs attention over the output of the encoder stack, allowing the decoder to focus on relevant parts of the input sequence.
    3.  **Position-wise Feed-Forward Network:** Same as in the encoder.

Finally, the output of the decoder stack is passed through a linear layer and a softmax function to produce the probability distribution over the vocabulary for each output token.

This detailed breakdown covers the fundamental mechanisms that make transformers so powerful in various sequence-to-sequence tasks.