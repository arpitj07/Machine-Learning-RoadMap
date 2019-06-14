# Machine-Learning-Algorithms

## Machine Learning

Machine learning (ML) is the scientific study of algorithms and statistical models that computer systems use in order to perform a specific task effectively without using explicit instructions, relying on patterns and inference instead. [Here](https://en.wikipedia.org/wiki/Machine_learning)
 
 <details> 
 <summary> 
 <a class="btnfire small stroke"><em class="fas fa-chevron-circle-down"></em>&nbsp;&nbsp;Types of Machine Learning Algorithms</a> 
 </summary>
  
  - [**Supervised learning**](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/README.md#supervised-learning)
    - Nearest Neighbor
    - Naive Bayes
    - Decision Trees
    - Linear Regression
    - Support Vector Machines (SVM)
    - Neural Networks
    
    
  - [**Unsupervised Learning**](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/README.md#unsupervised-learning)
    - Clustering
     - hierarchical clustering
     - k-means
     - mixture models
     - DBSCAN
     - OPTICS algorithm
    - Anomaly detection
     - Local Outlier Factor
    - Neural Networks
     - Autoencoders
     - Deep Belief Nets
     - Hebbian Learning
     - Generative Adversarial Networks
     - Self-organizing map
   Approaches for learning latent variable models such as
     - Expectation–maximization algorithm (EM)
     - Method of moments
    - Blind signal separation techniques
      - Principal component analysis
      - Independent component analysis
      - Non-negative matrix factorization
      - Singular value decomposition
      
      
  - [**Semi-supervised Learning**](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/README.md#semi-supervised-learning)
  - [**Reinforcement Learning**](https://github.com/arpitj07/Machine-Learning-Journey/blob/master/README.md#reinforcement-learning)
    - Q-Learning
    - Temporal Difference (TD)
    - Deep Adversarial Networks
 </details>
 

### Supervised Learning [[here](https://towardsdatascience.com/types-of-machine-learning-algorithms-you-should-know-953a08248861)]

Supervised learning algorithms try to **_model relationships and dependencies between the target prediction output and the input features_** such that we can predict the output values for new data based on those relationships which it learned from the previous data sets.

Most of the time we are not able to figure out the true function that always make the correct predictions and other reason is that the algorithm rely upon an assumption made by humans about how the computer should learn and **this assumptions introduce a bias**.

 - **Types** [[Here](https://www.geeksforgeeks.org/supervised-unsupervised-learning/)]
    
    Supervised learning classified into two categories of algorithms:
   - **Classification:** A classification problem is when the output variable is a category, such as “Red” or “blue” or “disease” and         “no disease”.
   -  **Regression:** A regression problem is when the output variable is a real value, such as “dollars” or “weight”.
 
 
### Unsupervised Learning [[Here](https://www.geeksforgeeks.org/supervised-unsupervised-learning/)]

Unsupervised learning is the training of machine using information that is neither classified nor labeled and allowing the algorithm to act on that information without guidance. Here the task of machine is to group unsorted information according to similarities, patterns and differences without any prior training of data.

Unlike supervised learning, no teacher is provided that means no training will be given to the machine. Therefore machine is restricted to find the hidden structure in unlabeled data by our-self.

- **Types** [[Here](https://www.geeksforgeeks.org/supervised-unsupervised-learning/)]
  
  Unsupervised learning classified into two categories of algorithms:

  - **Clustering:** A clustering problem is where you want to discover the inherent groupings in the data, such as grouping customers by      purchasing behavior.
  - **Association:** An association rule learning problem is where you want to discover rules that describe large portions of your data,      such as people that buy X also tend to buy Y.

### Semi Supervised Learning


### Reinforcement Learning [here](https://towardsdatascience.com/types-of-machine-learning-algorithms-you-should-know-953a08248861)

method aims at using observations gathered from the interaction with the environment to take actions that would maximize the reward or minimize the risk. Reinforcement learning algorithm (**called the agent**) continuously learns from the environment in an iterative fashion. In the process, the agent learns from its experiences of the environment until it explores the full range of possible states.

In order to produce intelligent programs (also called agents), reinforcement learning goes through the following steps:

- Input state is observed by the agent.
- Decision making function is used to make the agent perform an action.
- After the action is performed, the agent receives reward or reinforcement from the environment.
- The state-action pair information about the reward is stored.


