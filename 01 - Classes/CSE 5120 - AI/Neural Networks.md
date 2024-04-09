2024/04/08 13:32
Status: #idea
Tags: [[Lecture 12 Part One]], [[Computer Vision]]

# Neural Networks

**Neurons**:

Neurons are the basic building blocks of the nervous system, including the brain, spinal cord, and nerves. They are specialized cells that process and transmit information through electrical and chemical signals.

**Anatomy of Neurons**:

1. **Cell Body (Soma)**: The main part of the neuron that contains the nucleus and most of the cell's organelles. It integrates incoming signals and generates outgoing signals.
    
2. **Dendrites**: Branch-like structures that extend from the cell body. They receive signals from other neurons and transmit them to the cell body.
    
3. **Axon**: A long, slender projection that extends from the cell body. It carries signals away from the cell body to other neurons, muscles, or glands.
    
4. **Axon Terminal**: The end of the axon, which forms connections (synapses) with other neurons. Neurotransmitters are released from here to transmit signals to the next neuron.
    

**Artificial Neural Networks (ANNs)**:

Artificial Neural Networks are computational models inspired by the structure and function of biological neurons. They consist of interconnected nodes (artificial neurons) organized in layers. Each neuron receives input signals, processes them, and produces an output signal. The connections between neurons have associated weights, which are adjusted during training to learn patterns and make predictions.

### 2. Neural Networks

**Explanation**: Neural Networks are a set of algorithms, modeled loosely after the human brain, that are designed to recognize patterns. They interpret sensory data through a kind of machine perception, labeling, or clustering of raw input. The patterns they recognize are numerical, contained in vectors, into which all real-world data, whether images, sound, text, or time series, must be translated.

**LaTeX Expression**: The output of a neuron in a neural network is typically calculated using a weighted sum of its inputs, followed by the application of an activation function. This can be represented as:$$
o = f\left(\sum_{i=1}^{n} w_i x_i\right)
$$
#### Activation Functions

Activation functions in neural networks are crucial because they introduce non-linear properties to the network, enabling it to learn complex data patterns that linear functions cannot. Here are some of the most commonly used activation functions, along with brief notes on each:

### 1. Sigmoid (Logistic) Function

- **Expression**: $$
\sigma(x) = \frac{1}{1 + e^{-x}}
$$
- **Notes**: The sigmoid function outputs values between 0 and 1, making it suitable for applications where we need probabilities. It has been historically used for binary classification. However, it suffers from vanishing gradient problem and is not commonly used in deep networks today.

### 2. Hyperbolic Tangent Function (tanh)

- **Expression**: $$
\tanh(x) = \frac{e^{x} - e^{-x}}{e^{x} + e^{-x}}
$$​
- **Notes**: Tanh outputs values between -1 and 1. It is zero-centered, making convergence faster for some problems compared to the sigmoid function. However, it also suffers from the vanishing gradient problem in deep networks.

### 3. Rectified Linear Unit (ReLU)

- **Expression**:$$
f(x) = \max(0, x)
$$
- **Notes**: ReLU is very popular in deep learning because it allows for faster training without significant risk of vanishing gradients for positive values. However, it can suffer from the "dying ReLU" problem, where neurons stop learning entirely due to consistently negative inputs.

### 4. Leaky Rectified Linear Unit (Leaky ReLU)

- **Expression**: $$
f(x) = \max(\alpha x, x)
$$
- **Notes**: This is a variant of ReLU designed to fix the dying ReLU problem by allowing a small, non-zero gradient ($\alpha$ is a small constant) when the input is less than zero. It helps to keep the gradient flow alive during the training process.

### 5. Exponential Linear Unit (ELU)

- **Expression**: $$
f(x) = \begin{cases} x & \text{if } x > 0 \\ \alpha(e^x - 1) & \text{if } x \leq 0 \end{cases}
$$
- **Notes**: ELU aims to combine the best of ReLU and its variants by using an exponential function for negative inputs. It helps to reduce the vanishing gradient problem, and the mean output for the ELU function can be closer to zero, which aids in faster convergence.

### 6. Softmax Function

- **Expression**: $$
\sigma(\mathbf{z})_i = \frac{e^{z_i}}{\sum_{j}e^{z_j}}
$$
- **Notes**: The softmax function is used primarily in the output layer of a neural network model for multi-class classification problems. It squashes the outputs to be between 0 and 1 and also divides by the sum of the outputs to make them add up to 1. Thus, it converts the output scores from neurons into probabilities.

---
# References
