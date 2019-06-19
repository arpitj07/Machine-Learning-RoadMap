
# Convolutional Neural Network


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

![Strided Convolution](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/Strided%20Convolution.gif)

![Stride Equation](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/Stride%20Equation.gif)


### Convolutional Over Volume

onvolution over volume is a very important concept, which will allow us not only to work with color images, but even more importantly to apply multiple filters within a single layer. The first important rule is that the filter and the image you want to apply it to, must have the same number of channels. Basically, we proceed very much like in the example from Figure 3, nevertheless this time we multiply the pairs of values from the three-dimensional space. If we want use multiple filters on the same image, we carry out the convolution for each of them separately, stack the results one on top of the other and combine them into a whole. The dimensions of the received tensor (as our 3D matrix can be called) meet the following equation, in which: n — image size, f — filter size, nc — number of channels in the image, p —used padding, s — used stride, nf — number of filters.

![Convolutional Over Volume](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/VolumeEquation.gif)

![Convolutional Over Volume](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/OverVolume.png)
