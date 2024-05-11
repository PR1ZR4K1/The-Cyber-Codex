2024/04/08 14:02
Status: #idea
Tags: [[Neural Networks]]

# Convolutional Neural Networks

### 1. Convolution + Activation

**Convolution Layer**: The convolution layer is the core building block of a CNN. It applies a number of filters to the input image to create a feature map. Each filter detects spatial features such as edges or textures. The operation involves sliding the filter over the image and computing the dot product of the filter with the local regions of the input image.

$(f * g)(t) = \int_{-\infty}^{\infty} f(\tau)g(t - \tau) d\tau$

***Activation Function**: After applying the convolution operation, an activation function is applied to introduce non-linear properties to the system. The Rectified Linear Unit (ReLU) is the most commonly used activation function in CNNs due to its computational efficiency and ability to mitigate the vanishing gradient problem.*

**ReLU Activation Function**:

f(x) = \max(0, x)

### 2. Pooling

**Pooling Layer**: Pooling (also known as subsampling or downsampling) reduces the dimensionality of each feature map but retains the most important information. Pooling can be of different types, such as max pooling or average pooling.

- **Max Pooling**: Selects the maximum element from the region of the feature map covered by the filter.
- **Average Pooling**: Calculates the average of the elements in the region of the feature map covered by the filter.

Pooling helps to make the detection of features invariant to scale and orientation changes and also reduces the computational complexity for the layers that follow.

### 3. Flattening

**Flattening Layer**: After several convolutional and pooling layers, the high-level reasoning in the neural network is done via fully connected layers. Before connecting the convolutional/pooling layers to fully connected layers, the feature maps are flattened into a single vector of values.

Flattening transforms the 2D matrix of features into a vector that can be fed into a fully connected neural network classifier.

### 4. Full Connection (Fully Connected Layers)

**Fully Connected Layer**: This layer takes the flattened output of the previous layers and predicts the best label to describe the image. It works on the principle where every input is connected to every output by a weight (hence fully connected). This layer combines all the learned features from the previous layers across the image to identify specific features.

Fully connected layers are usually placed at the end of CNN architectures and are used to perform classification on the features extracted by the convolutional layers and pooled by the pooling layers. They are similar to the layers in a standard neural network and are used for high-level reasoning in the neural network.

- **Mathematical Representation of a Fully Connected Layer**:
    
    
    `y = f(Wx + b)`
    
    where $y$ is the output, $f$ is an activation function, $W$ represents the weight matrix, $x$ is the input vector, and $b$ is the bias vector.

These components work together in a CNN to process and transform input data (like images) through various layers of convolution, activation, pooling, and fully connected layers to produce a prediction output that can be used for classification, detection, and more.m 







---
# References
