
# Neural Network 


### Loss Functions

<details>
  
  [](https://gombru.github.io/2018/05/23/cross_entropy_loss/)

</details>


### Optimizers 

<details>
  
  
 </details>

### Overfitting [[Here](https://towardsdatascience.com/https-medium-com-piotr-skalski92-deep-dive-into-deep-networks-math-17660bc376ba)]

<details>
  
- **Preventing Overfitting**[[Here](https://towardsdatascience.com/https-medium-com-piotr-skalski92-deep-dive-into-deep-networks-math-17660bc376ba)]
)]
  - **L1 and L2 Regularizations**

    One of the first methods we should try when we need to reduce overfitting is regularisation. It involves adding an extra element to the loss function, which punishes our model for being too complex or, in simple words, for using too high values in the weight matrix. This way we try to limit its flexibility, but also encourage it to build solutions based on multiple features. Two popular versions of this method are L1 - Least Absolute Deviations (LAD) and L2 - Least Square Errors (LS). Equations describing these regularisations are given below.

    In most cases the use of L1 is preferable, because it reduces the weight values of less important features to zero, very often eliminating them completely from the calculations. In a way, it is a built-in mechanism for automatic featur selection. Moreover, L2 does not perform very well on datasets with a large number of outliers. The use of value squares results in the model minimizing the impact of outliers at the expense of more popular examples.

       ![](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/L1_L2_Regularisation.gif)

  - **Lambda factor and its effect**
 
    In the previously mentioned formulas for regularisation in both versions of L1 and L2, I introduced hyperparameter λ — also called regularization rate. When choosing its value we try to hit the sweet spot between simplicity of our model and fitting it to the training data. Increasing the λ value also increases the regularisation effects.
    n Figure 4. we can immediately notice that the planes obtained for the model without regulation, and models with a very low λ coefficient value are very “turbulent”. There are many peaks with significant values. After applying L2 regularization with higher hyperparameter value, the graph is flattening. Finally, we can see that setting the lambda value around 0.1 or 1 causes a drastic decrease in the value of weights in our model. I encourage you to check the source code used to create these visualizations.
    
    ![](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/Regularisation.gif)
    
  - **Drop Out**
    
    Another very popular method of regularization of neural networks is dropout. This idea is actually very simple - every unit of our neural network (except those belonging to the output layer) is given the probability p of being temporarily ignored in calculations. Hyper parameter p is called dropout rate and very often its default value is set to 0.5. Then, in each iteration, we randomly select the neurons that we drop according to the assigned probability. As a result, each time we work with a smaller neural network. The visualization below shows an example of a neural network subjected to a dropout. We can see how in each iteration random neurons from second and fourth layer are deactivated.
    
    ![](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/DropOut.gif)
    
    The effectiveness of this method is quite surprising and counterintuitive. After all, in the real world, the productivity of the factory will not increase if its manager, every day, randomly selects employees and sends them home. Let us look at this problem from the perspective of a single neuron. Since in each iteration, any input value can be randomly eliminated, the neuron tries to balance the risk and not to favour any of the features. As a result, the values in the weight matrix become more evenly distributed. The model wants to avoid a situation in which the solution it proposes, will no longer make sense, because it no longer has information flowing from an inactive feature.
    
 - **Early Stopping**
 
    The graph below shows the change in accuracy values calculated on the test and cross-validation sets during subsequent iterations of learning process. We see right away that the model we get at the end is not the best we could have possibly create. To be honest, it is much worse than what we have had after 150 epochs. Why not interrupt the learning process before the model starts overfitting? This observation inspired one of the popular overfitting reduction method, namely early stopping.
    
    ![](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/Images/EarlyStopping.gif)
  
    In practice, it is very convenient to sample our model every few iterations and check how well it works with our validation set. Every model that performs better than all the previous models is saved. We also set a limit, i.e. the maximum number of iterations during which no progress will be recorded. When this value is exceeded, the learning is stopped. Although early stopping allows for a significant improvement in the performance of our model, in practice, its application greatly complicates the process of optimization of our model. It is simply difficult to combine with other regular techniques.

</details>

- **Useful Links**
  - [what does the bias do in a neural network](https://stats.stackexchange.com/questions/185911/why-are-bias-nodes-used-in-neural-networks)
  - [how bias error related to bias node](https://stats.stackexchange.com/questions/130158/backpropagation-bias-nodes-and-error)
  - [How to Avoid Overfitting in Deep Learning Neural Networks](https://machinelearningmastery.com/introduction-to-regularization-to-reduce-overfitting-and-improve-generalization-error/)
  - [Gentle Introduction to the Bias-Variance Trade-Off in Machine Learning](https://machinelearningmastery.com/gentle-introduction-to-the-bias-variance-trade-off-in-machine-learning/)
  - [How to Normalize, Center, and Standardize Images With the ImageDataGenerator in Keras](https://machinelearningmastery.com/how-to-normalize-center-and-standardize-images-with-the-imagedatagenerator-in-keras/)


- **[BATCH NORMALISATION]**
    
    [How does Batch Normalization Help Optimization?](http://gradientscience.org/batchnorm/)
    
    [Batch Normalization and Internal Covariate Shift](https://medium.com/@SeoJaeDuk/archive-post-batch-normalization-and-internal-covariate-shift-1d47661d236f)
