# Anomaly-Detection-for-Faulty-Products-in-Manufacturing

Ensuring product quality is paramount in manufacturing industries. Anomalies such as defects, irregularities, or deviations from expected standards can lead to costly product recalls, customer dissatisfaction, and financial losses. This project aims to address these challenges by developing a Convolutional Neural Network (CNN) model for anomaly detection in manufacturing processes. By accurately identifying defects, faults, or unexpected variations in products, we aim to enhance quality control and reduce production errors.

# Dataset

THE MVTEC ANOMALY DETECTION DATASET (MVTEC AD)

MVTec AD is a dataset for benchmarking anomaly detection methods with a focus on industrial inspection. It contains over 5000 high-resolution images divided into fifteen different object and texture categories. Each category comprises a set of defect-free training images and a test set of images with various kinds of defects as well as images without defects.
![mvtec_dataset](https://github.com/user-attachments/assets/5278cb86-2345-4aa9-b381-cdfc4ac311ae)

Link dataset: https://www.mvtec.com/company/research/datasets/mvtec-ad

# Convolutional Neural Networks (CNNs)
**Convolutional Neural Networks (CNNs)** is the extended version of artificial neural networks (ANN) which is predominantly used to extract the feature from the grid-like matrix dataset. For example visual datasets like images or videos where data patterns play an extensive role.

**Why CNN?**

CNNs

* **Exploit spatial hierarchies:** CNNs can capture patterns and relationships between pixels in an image. 
* **Use shared weights (filters):** Filters are applied repeatedly across the image, reducing the number of parameters and making the network more efficient.
* **Have convolutional and pooling layers:** These layers extract features and reduce dimensionality, respectively.

Simple ANNs
 
* **Treat input as a flat vector:** Input data is flattened into a one-dimensional array, ignoring spatial information.
* **Lack spatial awareness:** Unable to capture spatial relationships within data.
* **Use fully connected layers:** Every neuron in one layer is connected to every neuron in the next, leading to a large number of parameters. 


**CNN Architecture**

The convolutional neural network is made of three main parts.
1) Convolutional layers
2) Pooling layers
3) Fully connected layers

![Schematic-diagram-of-a-basic-convolutional-neural-network-CNN-architecture-26](https://github.com/user-attachments/assets/c28dda9d-ed47-4fda-a634-d12b406fe867)

**Convolutional layer**

The convolutional layer is the fundamental building block of a CNN. Its core operation is convolution: applying a sliding filter (or kernel) to an image represented as a pixel matrix. This filter is designed to detect specific image features. The convolution process involves calculating the dot product between the filter and a region of the image, producing a single output value. This operation is repeated as the filter slides across the image, generating a feature map.

The size of the feature map is determined by three factors:

* **Filter size:** The number of filters used directly impacts the depth of the output feature map. Multiple filters create multiple feature maps.
* **Stride:** This defines the movement of the filter across the image. A larger stride results in a smaller output feature map.
* **Padding:** Adding zeros around the image edges (zero-padding) can affect the output size.
![2D_Convolution_Animation](https://github.com/user-attachments/assets/4dc1b2ff-252f-4d4d-9464-f24ffffa1686) 

After convolution, a Rectified Linear Unit (ReLU) is typically applied to introduce non-linearity into the feature map. 

**Pooling Layer**

The pooling layer downsamples feature maps by extracting dominant features. This process reduces dimensionality, computational cost, and the risk of overfitting. Common pooling techniques include:

* **Max pooling:** Selects the maximum value within a specified region of the feature map.
* **Average pooling:** Calculates the average of values within a specified region of the feature map. 
* **Sum pooling:** Computes the sum of values within a specified region of the feature map. 

**Fully Connected Layers**

Fully connected layers are typically the final layers in a convolutional neural network. They receive flattened input from the preceding pooling layer. These layers introduce non-linearity through the use of activation functions like ReLU. The output layer often employs a softmax function to generate probability distributions for each possible class. The class with the highest probability is selected as the final prediction. 

