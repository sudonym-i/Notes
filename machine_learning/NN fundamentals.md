## Course 1: Neural Networks and Deep Learning

**Focus:** Introduces the fundamental concepts of neural networks and deep learning, laying the groundwork for subsequent courses.

- **What is Deep Learning?**
    - Motivation for deep learning (data scale, computational power).
    - Supervised learning with neural networks.
    - Deep learning's impact on various industries.
- **Neural Network Basics:**
    - **Logistic Regression:** As a simple neural network.
    - **Perceptron:** The basic unit of a neural network.
    - **Activation Functions:** Sigmoid, ReLU, Leaky ReLU, Tanh – their properties and use cases.
    - **Forward Propagation:** Calculating outputs.
    - **Backward Propagation:** Calculating gradients.
    - **Gradient Descent:** The core optimization algorithm.
- **Deep Neural Networks:**
    - **Architecture:** Stacking layers, hidden layers.
    - **Vectorization:** Efficient computation using NumPy.
    - **Implementation:** Building a deep neural network from scratch.
    - **Hyperparameters:** Learning rate, number of iterations, number of hidden layers/units.

## Course 2: Improving Deep Neural Networks: Hyperparameter Tuning, Regularization and Optimization

**Focus:** Addresses practical aspects of building and training deep neural networks, focusing on techniques to improve performance and efficiency.

- **Practical Aspects of Deep Learning:**
    - **Train/Dev/Test Sets:** Proper data splitting for evaluation.
    - **Bias vs. Variance:** Understanding underfitting and overfitting.
    - **Basic Recipe for Machine Learning:** Iterative process of improving models.
- **Regularization:** Techniques to prevent overfitting.
    - **L2 Regularization:** Penalizing large weights.
    - **Dropout:** Randomly deactivating neurons during training.
    - **Data Augmentation:** Creating more training data from existing data.
    - **Early Stopping:** Halting training when validation error starts to increase.
- **Optimization Algorithms:** Speeding up and improving gradient descent.
    - **Mini-batch Gradient Descent:** Processing data in smaller batches.
    - **Exponentially Weighted Averages:** Smoothing gradients.
    - **Momentum:** Accelerating gradient descent in the right direction.
    - **RMSprop:** Adaptive learning rate optimization.
    - **Adam Optimization:** Combining Momentum and RMSprop (widely used).
    - **Learning Rate Decay:** Gradually reducing the learning rate.
- **Hyperparameter Tuning:** Strategies for finding optimal hyperparameters.
    - **Tuning Process:** Grid search vs. random search.
    - **Batch Normalization:** Normalizing activations within mini-batches to stabilize training.

## Course 3: Structuring Machine Learning Projects

**Focus:** Shifts from individual model improvement to the strategic aspects of building and deploying effective machine learning systems.

- **ML Strategy (1):**
    - **Orthogonalization:** Isolating effects of hyperparameter changes.
    - **Single Number Evaluation Metric:** Choosing appropriate metrics (e.g., F1 score, accuracy).
    - **Satisficing and Optimizing Metrics:** Balancing multiple objectives.
    - **Train/Dev/Test Set Distributions:** Ensuring consistency.
    - **Human-level Performance:** Using human performance as a benchmark.
    - **Avoidable Bias:** Understanding the gap between human-level error and training error.
    - **Error Analysis:** Systematically examining misclassified examples.
- **ML Strategy (2):**
    - **Mismatched Data Distributions:** Addressing scenarios where training and test data come from different distributions.
    - **Transfer Learning:** Reusing pre-trained models.
    - **Multi-task Learning:** Training a single model to perform multiple related tasks.
    - **End-to-End Deep Learning:** Building systems that learn directly from raw input to final output.

## Course 4: Convolutional Neural Networks (CNNs)

**Focus:** Delves into the architecture and application of CNNs, specifically designed for image and video data.

- **Foundations of CNNs:**
    - **Convolution Operation:** Filters, feature maps, stride, padding.
    - **Pooling Layers:** Max pooling, average pooling for dimensionality reduction.
    - **CNN Architecture:** Stacking convolutional, ReLU, and pooling layers.
    - **Why Convolutions?** Parameter sharing, sparsity of connections.
- **Deep Convolutional Models:**
    - **Classic Networks:** LeNet-5, AlexNet, VGG.
    - **ResNets (Residual Networks):** Using skip connections to train very deep networks.
    - **Inception Networks:** Using parallel convolutional layers with different filter sizes.
    - **MobileNet/EfficientNet (briefly mentioned):** Efficient architectures for mobile/edge devices.
- **Object Detection:**
    - **Localization:** Predicting bounding boxes.
    - **Landmark Detection:** Predicting specific points.
    - **Object Detection Algorithms:**
        - **Sliding Windows:** Inefficient approach.
        - **YOLO (You Only Look Once):** Real-time object detection.
        - **R-CNN family (briefly mentioned):** Region-based CNNs.
    - **Intersection Over Union (IoU):** Metric for bounding box accuracy.
    - **Non-max Suppression:** Filtering overlapping bounding boxes.
    - **Anchor Boxes:** Handling multiple objects in a single grid cell.
- **Special Applications:**
    - **Face Recognition:**
        - **One-Shot Learning:** Learning from a single example.
        - **Siamese Networks:** Learning similarity functions.
        - **Triplet Loss:** Training to distinguish between similar and dissimilar images.
    - **Neural Style Transfer:** Combining content from one image with style from another.
        - **Content Cost Function:** Measuring content similarity.
        - **Style Cost Function:** Measuring style similarity using Gram matrices.

## Course 5: Sequence Models

**Focus:** Explores neural networks designed for sequential data, such as natural language, audio, and time series.

- **Recurrent Neural Networks (RNNs):**
    - **Sequence Data:** Characteristics and challenges.
    - **RNN Architecture:** Processing sequences step-by-step, hidden states.
    - **Backpropagation Through Time (BPTT):** Training RNNs.
    - **Vanishing/Exploding Gradients:** Common problems in RNNs.
    - **Gated Recurrent Unit (GRU):** Addressing vanishing gradients with gates.
    - **Long Short-Term Memory (LSTM):** More powerful variant of GRU with cell state.
    - **Bidirectional RNNs:** Processing sequences in both directions.
    - **Deep RNNs:** Stacking multiple RNN layers.
- **Natural Language Processing (NLP) & Word Embeddings:**
    - **Word Representation:** One-hot encoding limitations.
    - **Word Embeddings:** Dense vector representations of words.
    - **Word2Vec (Skip-gram, CBOW):** Learning word embeddings.
    - **GloVe:** Global Vectors for Word Representation.
    - **Embedding Matrix:** Storing and using word embeddings.
    - **Debiasing Word Embeddings:** Addressing gender/racial bias.
- **Sequence Models & Attention Mechanism:**
    - **Sequence-to-Sequence Models:** Encoder-decoder architectures for translation, summarization.
    - **Beam Search:** Improving sequence generation.
    - **Attention Mechanism:** Allowing the decoder to focus on relevant parts of the input sequence.
    - **Speech Recognition:**
        - **Connectionist Temporal Classification (CTC):** For aligning audio to text.
    - **Trigger Word Detection:** Identifying specific keywords in audio.

---

This specialization provides a robust foundation for anyone looking to understand, implement, and apply deep learning techniques across various domains. It balances theoretical understanding with practical implementation, often using Python and TensorFlow/Keras.