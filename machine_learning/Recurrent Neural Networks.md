# Recurrent Neural Networks (RNNs)

Recurrent Neural Networks (RNNs) are a class of neural networks designed to process sequential data. Unlike traditional feed-forward neural networks, RNNs have internal memory that allows them to use information from previous inputs to influence the processing of current inputs. This makes them particularly well-suited for tasks involving sequences, such as natural language processing, speech recognition, and time series prediction.

## Intuitive Explanation

Imagine you're reading a story. To understand the current sentence, you often need to remember what happened in previous sentences. A traditional neural network would treat each sentence in isolation, forgetting the context. An RNN, however, has a "memory" that allows it to carry information forward from one step to the next in the sequence.

Think of it like this: when an RNN processes a word in a sentence, it doesn't just look at that word. It also considers a "hidden state" which is a summary of all the words it has processed *so far*. This hidden state is then updated with the information from the current word, and this updated hidden state is passed on to the next word in the sequence. This continuous flow of information allows the RNN to understand the context and dependencies within a sequence.

However, this simple memory can sometimes be a problem. If the story is very long, the RNN might start to "forget" important details from the beginning of the story by the time it reaches the end. This is where more advanced types of RNNs come in, with better mechanisms for remembering and forgetting information selectively.

## Mathematical Explanation

The core idea of an RNN is the recurrent connection, where the output of a hidden layer at time step $t$ is fed back as an input to the same hidden layer at time step $t+1$.

For a simple RNN, the hidden state $h_t$ at time $t$ is calculated as:

$h_t = f(W_{hh}h_{t-1} + W_{xh}x_t + b_h)$

And the output $y_t$ at time $t$ is calculated as:

$y_t = g(W_{hy}h_t + b_y)$

Where:
* $x_t$ is the input at time step $t$.
* $h_t$ is the hidden state at time step $t$.
* $h_{t-1}$ is the hidden state from the previous time step.
* $W_{hh}$, $W_{xh}$, $W_{hy}$ are weight matrices.
* $b_h$, $b_y$ are bias vectors.
* $f$ and $g$ are activation functions (e.g., tanh, ReLU, softmax).

This recurrent connection allows information to persist across time steps.

## Types of Recurrent Neural Networks

While the basic RNN structure is powerful, it suffers from issues like vanishing and exploding gradients, making it difficult to learn long-range dependencies. To address these limitations, more sophisticated RNN architectures have been developed.

### 1. Simple (Vanilla) RNN

As described above, the simple RNN is the most basic form. It processes sequences by updating its hidden state at each time step based on the current input and the previous hidden state.

**Pros:**
*   Conceptually simple.
*   Can model sequential data.

**Cons:**
*   **Vanishing/Exploding Gradients:** During backpropagation through time (BPTT), gradients can become extremely small or large, making it hard to learn long-term dependencies. This means the network struggles to remember information from many time steps ago.
*   Limited memory capacity for long sequences.

### 2. Long Short-Term Memory (LSTM) Networks

LSTMs were specifically designed to overcome the vanishing gradient problem and better capture long-term dependencies. They achieve this through a more complex internal structure called a "cell state" and several "gates" that control the flow of information.

**Intuitive Explanation:**
Imagine the cell state as a conveyor belt that runs through the entire sequence, carrying information. The gates are like turnstiles that decide what information gets added to the conveyor belt, what gets removed, and what gets read out.

*   **Forget Gate:** Decides what information from the previous cell state should be thrown away.
*   **Input Gate:** Decides what new information from the current input should be stored in the cell state.
*   **Output Gate:** Decides what part of the cell state should be outputted as the hidden state.

**Mathematical Explanation:**
An LSTM unit at time $t$ has a cell state $C_t$ and a hidden state $h_t$. The gates are typically sigmoid functions, and the candidate values are tanh functions.

*   **Forget Gate:** $f_t = \sigma(W_f \cdot [h_{t-1}, x_t] + b_f)$
*   **Input Gate:** $i_t = \sigma(W_i \cdot [h_{t-1}, x_t] + b_i)$
*   **Candidate Cell State:** $\tilde{C}_t = \tanh(W_C \cdot [h_{t-1}, x_t] + b_C)$
*   **Update Cell State:** $C_t = f_t \odot C_{t-1} + i_t \odot \tilde{C}_t$
*   **Output Gate:** $o_t = \sigma(W_o \cdot [h_{t-1}, x_t] + b_o)$
*   **Hidden State:** $h_t = o_t \odot \tanh(C_t)$

Where $\sigma$ is the sigmoid function, $\odot$ is element-wise multiplication, and $W$ and $b$ are weight matrices and bias vectors.

**Pros:**
*   Excellent at capturing long-term dependencies.
*   Mitigates vanishing gradient problem.
*   Widely used and highly effective for many sequence tasks.

**Cons:**
*   More complex architecture than simple RNNs.
*   Computationally more expensive due to multiple gates.

### 3. Gated Recurrent Unit (GRU) Networks

GRUs are a simplified version of LSTMs. They combine the forget and input gates into a single "update gate" and merge the cell state and hidden state. This makes them computationally less expensive than LSTMs while still being effective at handling long-term dependencies.

**Intuitive Explanation:**
GRUs are like a more streamlined version of LSTMs. They still have mechanisms to decide what to remember and what to forget, but with fewer gates, making them a bit faster and simpler to implement.

*   **Update Gate:** Decides how much of the past information (from the previous hidden state) should be carried forward and how much new information should be added.
*   **Reset Gate:** Decides how much of the previous hidden state should be "forgotten" before combining with the new input.

**Mathematical Explanation:**
A GRU unit at time $t$ has a hidden state $h_t$.

*   **Update Gate:** $z_t = \sigma(W_z \cdot [h_{t-1}, x_t] + b_z)$
*   **Reset Gate:** $r_t = \sigma(W_r \cdot [h_{t-1}, x_t] + b_r)$
*   **Candidate Hidden State:** $\tilde{h}_t = \tanh(W_h \cdot [r_t \odot h_{t-1}, x_t] + b_h)$
*   **Hidden State:** $h_t = (1 - z_t) \odot h_{t-1} + z_t \odot \tilde{h}_t$

**Pros:**
*   Effective at capturing long-term dependencies, similar to LSTMs.
*   Fewer parameters and less complex than LSTMs, leading to faster training and less computational cost.
*   Often performs comparably to LSTMs on many tasks.

**Cons:**
*   May not always outperform LSTMs on very complex tasks requiring finer control over memory.

In summary, RNNs, especially LSTMs and GRUs, are fundamental building blocks for processing sequential data, providing the ability to learn from context and dependencies over time.