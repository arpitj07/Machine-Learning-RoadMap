
# Unsupervised Learning Algortihms:


### Cluster Analysis:

   Clustering is a Machine Learning technique that involves the grouping of data points. Given a set of data points, we can use a clustering algorithm to classify each data point into a specific group. In theory, data points that are in the same group should have similar properties and/or features, while data points in different groups should have highly dissimilar properties and/or features. Clustering is a method of unsupervised learning and is a common technique for statistical data analysis used in many fields.

   - **K-Means Clustering**:
   
     -<details><summary> :star: Steps involved </summary>
      
        - To begin, we first select a number of classes/groups to use and randomly initialize their respective center points. To figure               out the number of classes to use, it’s good to take a quick look at the data and try to identify any distinct groupings.**The               center points are vectors of the same length as each data point vector and are the “X’s” in the graph.**
        - Each data point is classified by computing the distance between that point and each group center, and then classifying the                 point to be in the group whose center is closest to it.
        - Based on these classified points, we recompute the group center by taking the mean of all the vectors in the group.
        - Repeat these steps for a set number of iterations or until the group centers don’t change much between iterations. You can                 also opt to randomly initialize the group centers a few times, and then select the run that looks like it provided the best                 results. 
        </details>
   
     - <details><summary> :star:Advantages </summary>
      
      -  it’s pretty fast
      -  we’re really doing is computing the distances between points and group centers; very few computations! It thus has a linear             complexity O(n)
      
      </details><summary> :star: Disadvantages </summary>
      
      - you have to select how many groups/classes there are. This isn’t always trivial and ideally with a clustering algorithm we’d want           it to figure those out for us because the point of it is to gain some insight from the data. 
      - K-means also starts with a random choice of cluster centers and therefore it may yield different clustering results on different           runs of the algorithm. Thus, the results may not be repeatable and lack consistency.
        
       </details>
