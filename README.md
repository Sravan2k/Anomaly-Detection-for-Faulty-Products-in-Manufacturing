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

# Architecture

A pre-trained ResNet-50 model is used. While the original model extracts 2048 features from its final layers, this architecture extracts features from intermediate layers. Specifically, the features from layer 2 and layer 3 are extracted using PyTorch's hook feature and concatenated, resulting in a 1536-dimensional feature vector. This combined feature vector is then input into the fully connected layers for model training. 
![ResNet-50-architecture-26-shown-with-the-residual-units-the-size-of-the-filters-and](https://github.com/user-attachments/assets/fe74e5a8-61bf-4e41-8ae1-afca879381d5)

# Model
A statistical model is employed, where the Mean Squared Error (MSE) between a feature and its reconstruction serves as the anomaly score. If this anomaly score exceeds a predefined threshold, a fault is indicated at that point. The distribution of anomaly scores often approximates a Gaussian curve, suggesting that a suitable threshold can be estimated as the mean plus three times the standard deviation. However, the optimal threshold can also be determined more precisely using the F1 score. 
<img width="452" alt="gaussian_graph" src="https://github.com/user-attachments/assets/73cf695e-8793-46b5-8790-1ac5155d33a0">

# Results
**ROC curve**

<img width="455" alt="AOC-ROC curve" src="https://github.com/user-attachments/assets/6e44261a-0722-4a28-ae33-cafb29c44f27">

Area under curve and 45 degree diagonal will be same as the AUC-ROC
AUC-ROC Score = 0.9839486356340289

We get the best optimal threshold by the F1-score = 0.025749897584319115

**Confusion matrix**
   
   <img width="421" alt="confussion_matrix" src="https://github.com/user-attachments/assets/c60f9d7d-350c-4c69-95ae-6994cfccc566">

# Test Samples
<img width="884" alt="1" src="https://github.com/user-attachments/assets/153b7512-0ff9-4930-93ce-75166031a5f5">

<img width="882" alt="2" src="https://github.com/user-attachments/assets/e09ffa66-9053-4096-b1dc-526972ce31f8">

<img width="886" alt="3" src="https://github.com/user-attachments/assets/677d248c-5469-467a-823b-51e638f99271">

<img width="883" alt="4" src="https://github.com/user-attachments/assets/78e05cf9-97be-4e72-ac6f-3002c23f86d3">

<img width="884" alt="5" src="https://github.com/user-attachments/assets/60a2faea-cf4f-458c-95ab-5dcf066a09ba">

<img width="849" alt="6" src="https://github.com/user-attachments/assets/74077396-bc8a-47d5-8167-c8c3000dc01b">
