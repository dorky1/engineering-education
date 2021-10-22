### Introduction
SVMs are a type of vector machine which supports vectors. Support vector machines, popularly called support vector classifications and support vector regression, are methods for dealing with classification and regression problems (SVR). The time required to evaluate a big dataset using this technique makes it unfeasible even for smaller datasets. 

### Table of Contents
- [Overview on Support Vector Machines](#overview-on-support-vector-machines)
- [The Role of Margin in Support Vector Machines](#the-role-of-margin-in-support-vector-machines)
- [Support Vector Machines with a Hard Margin](#support-vector-machines-with-a-hard-margin)
- [Support Vector Machines with a Soft Margin](#support-vector-machines-with-a-soft-margin)
- [Hard Margin and Soft Margin comparisons.](#hard-margin-and-soft-margin-comparisons)

### Overview on Support Vector Machines
It is possible to utilize Vector Machines for both classification and regression. Vector Machines are a powerful machine learning method. Because it has such a significant impact, the kind of margin we employ to solve a problem must be carefully considered. When doing SVM calculations, this section of the course will discuss the distinctions between the use of a hard margin and the use of a soft margin.

These are the benefits of using this technique:
- SVM works effectively whenever we have a clear difference between classes.
- SVM outperforms other techniques in high-dimensional spaces.
- It works well when the number of parameters exceeds the number of samples.
- Statistical Learning Machines (SVM) need less memory.

### The Role of Margin in Support Vector Machines
Consider first a set of data that we want to categorize. Based on this knowledge, they may be differentiable or the splitting of hyperplanes may be non-linear. We utilize SVM with a large margin to prevent misclassifications for linearly separable. Soft margins are used when a linear border is not usable, or when we desire to tolerate some misclassifications to increase the generality of the classification system.

### Support Vector Machines with a Hard Margin
If the hyperplane separating  then our two classes will be `wTx + b = 0`, then the following will be true:

![Classes separation in hyperplane](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/margin.jpg)

SVMs are represented by the green and purple lines in the above picture, respectively. It is our goal to narrow the distance between these two hyperplanes to the greatest extent feasible while preventing misclassifications in the hard margin. SVM This equation is used to determine how far away the point and plane appear to be from one another seen from different perspectives. In other words, the distances from  the blue and red dots, including the ranges between them, are:

![Distance of blue and red points from black line](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/distance.jpg) 

We must utilize our available area to realize this potential. We can look at `alpha = b + 1` and `beta = b - 1` without sacrificing generality. The problem must be solved in terms of maximizing or minimization. To compute gradients, we will use the term in its squared form:

![Squared for formula](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/gradient.jpg)

This optimization has several drawbacks. Suppose our classes are -1 and +1 for argument's sake. `wx+b>=1`, while `wx=b=-1` classifies the data as positive. These two requirements may be linked to a single one. As a solution, our optimization issue would be as shown below:

![Optimization problem](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/formula.jpg)

This kind of optimization problem is referred to as a primal problem since it always results in the production of a globally minimal value. The dual issue may be solved by using `alpha i` Lagrange multipliers in the equation.

![Primal problem](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/primal.jpg)

`Lagrangian function` is the name used to describe this kind of function, which is distinct in terms of (omega) and b and which is generated from the SVM's Lagrangian function.

![Lagrangian function](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/function.jpg)

By switching the Lagrangian functions, two SVM problems may be solved. The first is SVM's two-fold problem.

![Dual problem of svm](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/dual.jpg)

As a result, the dual issue is simpler to solve. It can be utilized for non-linear boundaries since it does not need to divide the data for training into dual issues and inner products.

### Support Vector Machines with a Soft Margin
The soft margin SVM optimization method has undergone a few minor tweaks to make it more effective. To begin, unchecking this scenario invites mistakes. Reduce the quantity of wrongly categorized data, which means we already have one more barrier to clear. Second, a loss function should indeed be created to reduce error. The `hinge loss` is a soft margin loss function that is often seen.

![Common loss's function (hinge loss)](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/hinge.jpg)

Slack variables, or misclassified features, are lost when using hard margin SVM. So, a major issue for something such as  the soft margin is as illustrated below:

![Primal problem for the soft margin](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/marg.jpg)

To control the trade-off between margin expansion and loss reduction, the regularization parameter C may be used. Loose factors have been added to both the fundamental and hard margin problems, as shown in the image. Because it contains slack variables, the model is more lenient when misclassifications occur. This is illustrated below:

![Addtion of slack variables](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/slack.jpg)

Finally, we may make the following comparison between the two issues:

![Primal problem for the soft margin](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/max.jpg)

### Hard Margin and Soft Margin comparisons.
#### Hard Margin
Assume there are three hyperplanes denoted by the letters `(π, π+, π+)`, so that on the positive side of each of them, `π+` is parallel to the support vectors, and on the negative side of each of them, `π-` is parallel to the support vectors. On the other hand, `π` is parallel to the support vectors on both of its positive sides.

![Hyperplanes (π, π+, π−)](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/negative.jpg)

Each hyperplane's equations may well be summarized as follows:
(for the sake of point X1)

![Equations for hyperplane](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/hyper.jpg)

**Explanation**
Our actual output multiplied by the hyperplane equation will be equal to 1, indicating that X1 has been classified as a positive.

> For point X3 is shown below

![For the point at X3](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/three.jpg)

**Explanation**
X3 is beyond the hyperplane's domain when it is further away from it. This indicates the point is positive.

As stated above, if `Yi(WT*Xi +b) > 1`, then Xi is properly categorized; otherwise, Xi is wrongly classified.

If we add an outlier, our hyperplane becomes worthless since it cannot differentiate linearly separable points. As a result, we must use `hard margin SVMs` to classify each piece of data.

#### Soft Margin
We presume data can be split linearly, although this might not be the case. This technique eliminates outliers, enabling us to categorize locations almost linearly. Thus, the Slack variable  `ξ` Xi is generated. If we add  `ξ` to our previous equation, we get:

![Introducing ξ](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/xi.jpg)

*If `ξi= 0`, then the points are properly classified. If that's not the case, we receive`ξi> 0` which is miscategorized.*

If `ξi> 0` then the variables will be in the wrong dimension (variable). How to compute the error of  standard deviation is shown below:

![Average error](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/error.jpg)

As a result, we can express our goal mathematically as;

![Mathematical description of the formula](engineering-education/using-a-hard-margin-vs-soft-margin-in-support-vector-machines/min.jpg)

As long as all points are correctly classified, we can find the vector w and b whereby the hyperplane given by w and b maximizes the margin length while minimizing the loss term.

> The soft margin method is the name given to this kind of formulation.

Hard margins are more exact than soft margins in SVMs because the data is more separable. When our dataset can also be split linearly, we strive for a small margin of error. As a result, unless certain criteria are met, it will just be impossible to carry out the necessary activity. Obtaining a linear classifier is difficult in this instance because of the many variables at play. SVMs with slender margins perform well in this situation.

> Because the error margin is so small in certain instances, overfitting or excessive sensitivity to outliers is a possibility. We may also employ a softer margin SVM with a larger margin to improve the generalization of the model.

### Conclusion
In this tutorial, we have looked at the concept of a hard margin and a soft margin SVM, along with how to use each one of them. Support vector machines margin requirements were also discussed.

Happy Learning!