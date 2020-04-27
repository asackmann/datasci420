---
marp: true
theme: gaia
paginate: true
backgroundColor: white
---

<!-- #4C2E84 -->
<!-- ![bg right w:600](images/uw_pce_logo.jpg) -->

<!-- _backgroundColor: #0473cf; -->
<!-- _color: white -->

# ___________________
# DataSci 420
# lesson 7: support vector machines
## Seth Mottaghinejad
# ___________________

[DataSci 420]: https://www.pce.uw.edu/certificates/data-science
[break time]: https://www.google.com/search?q=online+timer
[lab time]: https://www.google.com/search?q=online+timer

----------------------------------------------------------------

## today's agenda

- SVM **pros and cons**
- linear separability and **wide-margin classifiers**
- non-linear separability
- the **kernel trick**
- **soft-margin classifiers**
- **multi-class classification** with SVMs
- **cross validation** for **hyper-parameter tuning**

----------------------------------------------------------------

## SVMs in a nutshell

SVMs give us models that capture very **complex relationships** without running the risk of over-fitting:
- world-class until the advent of deep learning
- they can run through **a lot of compute**, although the **kernel trick** makes the computation much more efficient
- less affected by outliers (because the separation boundary only depends on the **support vectors**)
- not great for **multi-class** classfication: **one-vs-one**, **one-vs-all**

----------------------------------------------------------------

## SVM classifier

- there are many lines that offer **linear separability**
- the one that maximizes the **margin** is the best one
- SVM are called **wide-margin classifires**
- the model is explained by its **support vectors**

image source: [wikipedia.org]

![bg right w:500](./images/svm-wide-margin.jpg)

[Wikipedia]: https://en.wikipedia.org/wiki/Support-vector_machine

----------------------------------------------------------------

<!-- _class: lead -->

![center w:1000](./images/svm-linear-separability.jpg)

image source: [wikipedia.org]

[Wikipedia]: https://en.wikipedia.org/wiki/Support-vector_machine

----------------------------------------------------------------

<!-- _class: lead -->

![center w:1000](./images/svm-mapping.jpg)

image source: [wikipedia.org]

[Wikipedia]: https://en.wikipedia.org/wiki/Support-vector_machine

----------------------------------------------------------------

## SVM motivation

- if data is **linearly separable** (by a hyper-plane), then a **wide-margin classifier** is a better classifier
- when data is not linearly separable, project it to a **higher dimension** ($\phi: X \rightarrow Z$) in which the labels are linearly separable
- in $Z$ space, **decision boundary** is linear, pinned down only by a few data points called **support vectors**
- the **pre-image** of decision boundary in $X$ space can look complex, but it's the pre-image of a hyper-plane in $Z$ space

----------------------------------------------------------------

<!-- _class: lead -->
## [break time]

----------------------------------------------------------------

## the kernel trick

- the math for SVMs can be challenging: linear algebra including some abstract concepts
- the prediction equation is $g(\bold{x}) = \text{sign}(\bold{w}^T\bold{z} + b)$
- we need to calculate $\bold{z}_n^T \bold{z}_m$ to find a solution
- with the kernel trick we can do it **without explicitly finding the mappings** $\bold{x}_i \mapsto \bold{z}_i$
- instead we use the kernel $K$: $\bold{z}_n^T \bold{z}_m = K(\bold{x}_n, \bold{x}_m)$

----------------------------------------------------------------

## types of kernels

depending on the choice, kernels introduce new hyper-parameters (such as $\gamma$ and $d$)

- **linear** $K(\bold{x}_n, \bold{x}_m) = \bold{x}_n^T \bold{x}_m$
- **polynomial** $K(\bold{x}_n, \bold{x}_m) = (\gamma\bold{x}_n^T \bold{x}_m + r)^d$ where $\gamma > 0$
- **radial basis function** $K(\bold{x}_n, \bold{x}_m) = \exp(-\gamma||\bold{x}_n - \bold{x}_m||^2)$ where $\gamma > 0$ (which corresponds to an infinite dimensional $Z$ space if we look at its Taylor series expansion)

----------------------------------------------------------------

## soft-margin classifiers

- **hard-margin classifiers** expect perfect separability, but we can add a **slack variable** and get a **soft-margin classifier**
- when the data is not linearly separable, we can adjust the trade-off between margin width and the classification error using the $C$ **hyper-parameter**
- $C$ is the penalty on data points that are on the wrong side of the decision boundary:
  - higer $C$ means more **tolerance** for misclassification

----------------------------------------------------------------

## multi-class classification

- let $k$ be the number of classes
- SVMs can only give us binary classifiers but we can still use them to do multi-class classification:
  - **one vs one:** builds $k\choose 2$ classifiers
  - **one vs rest:** (also called. **one vs all**), builds $k$ classifers
- unlike SVMs, neural networks can train multi-class classifiers with a single instance of training
  - logistic regression is like a NN too and can do the same

----------------------------------------------------------------

<!-- _class: lead -->
## [break time]

----------------------------------------------------------------

## hyper-parameter tuning

- we can do a **three-way split**:
  - **training data** is for **learning**, **validation data** is for **model selection**, **test data** is for **evaluating final model**
- we can do a **two-way split** and **cross validation**:
  - training data is divided into $k$ folds:
    - $k-1$ folds are for learning, and the $k$th fold for validation
    - we repeat this $k$ times, one for each fold
  - test data is for **evaluating final model**

----------------------------------------------------------------

<!-- _class: lead -->

![center w:800](./images/grid-search-cross-validation.jpg)

image source: [scikit-learn.org]

[scikit-learn.org]: https://scikit-learn.org/stable/modules/cross_validation.html#cross-validation

----------------------------------------------------------------

<!-- _class: lead -->
## the end

