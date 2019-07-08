
# Convolutional Neural Network

   **Reading List**
   
   - [Create your own COCO-style datasets](https://patrickwasp.com/create-your-own-coco-style-dataset/)
   - [Image Processing in Python With Pillow](https://dzone.com/articles/image-processing-in-python-with-pillow?fromrel=true)
   - [Semantic Segmentation using Fully Convolutional Networks over the years](https://meetshah1995.github.io/semantic-segmentation/deep-learning/pytorch/visdom/2017/06/01/semantic-segmentation-over-the-years.html)
   - [Types of Filters](https://lodev.org/cgtutor/filtering.html)
   - [Finding the Cost Function of Neural Networks](https://towardsdatascience.com/step-by-step-the-math-behind-neural-networks-490dc1f3cfd9)
   - [Improving Performance of Convolutional Neural Network!](https://medium.com/@dipti.rohan.pawar/improving-performance-of-convolutional-neural-network-2ecfe0207de7)
   - [Forward And Backpropagation in Convolutional Neural Network](https://medium.com/@2017csm1006/forward-and-backpropagation-in-convolutional-neural-network-4dfa96d7b37e)

### Convolution

Kernel convolution is not only used in CNNs, but is also a key element of many other Computer Vision algorithms. It is a process where we take a small matrix of numbers (called kernel or filter), we pass it over our image and transform it based on the values from filter. Subsequent feature map values are calculated according to the following formula, where the input image is denoted by f and our kernel by h. The indexes of rows and columns of the result matrix are marked with m and n respectively.

 ![](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/KernelConvo-equation.gif)
 
After placing our filter over a selected pixel, we take each value from kernel and multiply them in pairs with corresponding values from the image. Finally we sum up everything and put the result in the right place in the output feature map.

![](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/Kernel%20Convolutional.gif)

![](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/EdgeDetection.gif)


### Valid and Same Convolution

when we perform convolution over the 6x6 image with a 3x3 kernel, we get a 4x4 feature map. This is because there are only 16 unique positions where we can place our filter inside this picture. Since our image shrinks every time we perform convolution, we can do it only a limited number of times, before our image disappears completely. What’s more, if we look at how our kernel moves through the image we see that the impact of the pixels located on the outskirts is much smaller than those in the center of image. This way we lose some of the information contained in the picture. Below you can see how the position of the pixel changes its influence on the feature map.

To solve both of these problems we can pad our image with an additional border. For example, if we use 1px padding, we increase the size of our photo to 8x8, so that output of the convolution with the 3x3 filter will be 6x6. Usually in practice we fill in additional padding with zeroes. Depending on whether we use padding or not, we are dealing with two types of convolution — Valid and Same. Naming is quite unfortunate, so for the sake of clarity: Valid — means that we use the original image, Same — we use the border around it, so that the images at the input and output are the same size. In the second case, the padding width, should meet the following equation, where p is padding and f is the filter dimension (usually odd).

![Kernel Position](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/Pixel%20Position.gif)


### Strided Convolution

we always shifted our kernel by one pixel. However, step length can also be treated as one of convolution layer hyperparameters. In Figure, we can see how the convolution looks like if we use larger stride. When designing our CNN architecture, we can decide to increase the step if we want the receptive fields to overlap less or if we want smaller spatial dimensions of our feature map. The dimensions of the output matrix - taking into account padding and stride - can be calculated using the following formula.

![Strided Convolution](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/StridedConvolution.gif)

![Stride Equation](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/StrideEquation.gif)


### Convolutional Over Volume

onvolution over volume is a very important concept, which will allow us not only to work with color images, but even more importantly to apply multiple filters within a single layer. The first important rule is that the filter and the image you want to apply it to, must have the same number of channels. Basically, we proceed very much like in the example from Figure 3, nevertheless this time we multiply the pairs of values from the three-dimensional space. If we want use multiple filters on the same image, we carry out the convolution for each of them separately, stack the results one on top of the other and combine them into a whole. The dimensions of the received tensor (as our 3D matrix can be called) meet the following equation, in which: n — image size, f — filter size, nc — number of channels in the image, p —used padding, s — used stride, nf — number of filters.

![Convolutional Over Volume](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/VolumeEquation.gif)

![Convolutional Over Volume](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/OverVolume.png)


### Convolution Layers

The time has finally come to use everything we have learned today and to build a single layer of our CNN. Our methodology is almost identical to the one we used for densely connected neural networks, the only difference is that instead of using a simple matrix multiplication, this time we will use the convolution. **Forward propagation consists of two steps. The first one is to calculate the intermediate value Z, which is obtained as a result of the convolution of the input data from the previous layer with W tensor (containing filters), and then adding bias b.** The second is the application of a non-linear activation function to our intermediate value (our activation is denoted by g). Fans of matrix equations will find appropriate mathematical formulas below.

![TensorDimension](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/TensorDimestion.gif)


 - **Connections Cutting and Parameters Sharing**

At the beginning of the article I mentioned that densely connected neural networks are poor at working with images, due to the huge number of parameters that would need to be learned. Now that we understand what convolution is all about, let’s consider how it allows us to optimize the calculations. On the Figure below, the 2D convolution has been visualized in a slightly different way — neurons marked with numbers 1–9 form the input layer that receives brightness of subsequent pixels, while units A-D denotes calculated feature map elements. Last but not least, I-IV are the subsequent values from kernel — these must be learned.

![Paramter sharing](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/ParameterSharing.gif)

Now, let’s focus on the two very important attributes of convolution layers. First of all, you can see that not all neurons in the two consecutive layers are connected to each other. For example, unit 1 only affects the value of A. Secondly, we see that some neurons share the same weights. Both of these properties mean that we have much less parameters to learn. **By the way, it is worth noting that a single value from the filter affects every element of the feature map — it will be crucial in the context of backpropagation.**


- **Convolutional Layer Backpropagation**

Anyone who has ever tried to code their own neural network from scratch knows, that forward propagation is less than half the success. The real fun starts when you want to go back. Nowadays, we don’t need to bother with backpropagation — deep learning frameworks do it for us, but I feel it’s worth knowing what’s going on under the hood. Just like in densely connected neural networks, our goal is to calculate derivatives and later use them to update the values of our parameters in a process called gradient descent.

In our calculations we will use a chain rule — which I mentioned in previous articles. We want to assess the influence of the change in the parameters on the resulting features map, and subsequently on the final result. Before we start to go into the details, let us agree on the mathematical notation that we will use — in order to make my life easier, I will abandon the full notation of the partial derivative in favour of the shortened one visible below. But remember, that when I use this notation, I will always mean the partial derivative of the cost function.

![Back Propogation Equation](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/BackProp_1.gif)

Our task is to calculate dW[l] and db[l] - which are derivatives associated with parameters of current layer, as well as the value of dA[ l -1] - which will be passed to the previous layer. As shown in Figure 10, we receive the dA[l] as the input. Of course, the dimensions of tensors dW and W, db and b as well as dA and A respectively are the same. The first step is to obtain the intermediate value dZ[l] by applying a derivative of our activation function to our input tensor. According to the chain rule, the result of this operation will be used later.


Now, we need to deal with backward propagation of the convolution itself, and in order to achieve this goal we will utilise a matrix operation called full convolution — which is visualised below. Note that during this process we use the kernel, which we previously rotated by 180 degrees. This operation can be described by the following formula, where the filter is denoted by W, and dZ[m,n] is a scalar that belongs to a partial derivative obtained from the previous layer.

  ![Back Prop](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/BackProp.gif)


### Pooling Layers
   Besides convolution layers, CNNs very often use so-called pooling layers. They are used primarily to reduce the size of the tensor and speed up calculations. This layers are simple - we need to divide our image into different regions, and then perform some operation for each of those parts. For example, for the Max Pool Layer, we select a maximum value from each region and put it in the corresponding place in the output. As in the case of the convolution layer, we have two hyperparameters available — filter size and stride. Last but not least, if you are performing pooling for a multi-channel image, the pooling for each channel should be done separately.

   ![](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/MaxPooling.gif)

### Pooling Layers Backpropagation
   In this article we will discuss only max pooling backpropagation, but the rules that we will learn — with minor adjustments — are applicable to all types of pooling layers. Since in layers of this type, we don’t have any parameters that we would have to update, our task is only to distribute gradiwents appropriately. As we remember, in the forward propagation for max pooling, we select the maximum value from each region and transfer them to the next layer. It is therefore clear that during back propagation, the gradient should not affect elements of the matrix that were not included in the forward pass. In practice, this is achieved by creating a mask that remembers the position of the values used in the first phase, which we can later utilize to transfer the gradients.

   ![](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/PoolingBack.gif)
