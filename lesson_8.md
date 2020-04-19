---
marp: true
theme: gaia
paginate: true
---

<!-- #4C2E84 -->
<!-- ![bg right w:600](images/uw_pce_logo.jpg) -->

<!-- _backgroundColor: #0473cf; -->
<!-- _color: white -->

# ___________________
# DataSci 420
# lesson 8: neural networks
## Seth Mottaghinejad
# ___________________

[DataSci 420]: https://www.pce.uw.edu/certificates/data-science
[break time]: https://www.google.com/search?q=online+timer
[lab time]: https://www.google.com/search?q=online+timer

----------------------------------------------------------------

## today's agenda

----------------------------------------------------------------

<!-- _class: lead -->
## [break time]

----------------------------------------------------------------

## [lab time]

----------------------------------------------------------------

<!-- _class: lead -->
## the end





what are NNs? what is deep learning?

neural networks motivation:
- show training progress and stop training when it starts to overfit
- the math is basic calculus and LA
- GPUs instead of CPUs
- they do their own feature engineering, allowing for more abstract features in deeper layers

math behind NNs:
- optimization - SGD stochastic gradient descent
- calculus - chain rule applied to multivariate calculus
- linear algebra - basic matrix algebra and how to vectorize computations

terminology:
- inputs, outputs, weights, biases, activation functions, activations (output of applying activation functions to weighted sums)
- forward pass, backward pass
- gradient descent, stochastic gradient descent, back-propagation
- three ways to run each iteration of the optimization:
  - batch (update weights and biases based on average loss for the whole data)
  - mini-batch (update weights and biases based on average loss for a small sample of data)
  - online training (update weights and biases one row at a time)
- epoch

the perceptron model is the most basic neural network building block

different activation functions:
- sigmoid (between 0 and 1)
- tanh (between -1 and 1)
- softmax (at the last layer)
- ReLU

how a neural network trains:
- 1) initialize weights and biases
- 2) take the next mini-batch of data:
  - a) make a forward pass (which gives you a prediction) and calculate the "loss" (error)
  - b) make a backward pass (which gives you the derivative of loss w.r.t. weights and biases)
  - c) update weights and biases accordingly
- 3) repeat step 2 until you converge
- 4) OPTIONAL if we've reached an epoch (exhausted the mini-batches), then keep track of performance (loss or accuracy) so far

how training happens -> GD is the what, SGD is the whatish, BP is the how:
- the cost function (loss function, objective function) computes the error
- gradient descent finds weights and biases that minimize cost
  - we can minimize the cost over all training data, but this takes forever
  - stochastic gradient descent runs gradient descent on mini-batches of data, so we minimize the cost over a mini-batch of training data and use a different mini-batch for each iteration
  - SGD is more noisy, but much much faster
back-propagation (implementation of gradient descent for neural networks)
- implement the optimization using a matrix computation (single pass at each iteration -> you updates all weights and biases in one swoop of matrix computations)

prevent over-fitting:
  - early-stopping - if after a certain number of epochs performance (on validation data) starts to decline then stop training
  - drop-out - for each mini-batch of data (iteration), drop some random units, do the forward and backward pass, update weights and biases (that weren't dropped), then repeat
  - regularization
  - more training data
  - simplify the architecture (fewer HLs, fewer units within each HL) - hyper-parameter tuning

automated ML can be used to tune the hyper-parameters of a NN (and figure out the right architecture) -> bayesian optimization is the most popular method:
- trade-off between exploration (very different set of HPs) and exploitation (very similar HPs, just slight tweek)



neural networks motivation:
- computational power (GPU hardware such as Nvidia, CUDA software layer on top)
- big data (deep models need a lot of data to not overfit)
- training happens gradually and can be updated
- break-throughs
- neural networks do their own feature engineering

the perceptron model is the most basic neural network building block
- weighted sum (weights and bias)
- activations (apply an activation function to weighted sums)

how training happens -> GD is the what, SGD is the whatish, BP is the how:
- the cost function (loss function, objective function) computes the error
- gradient descent finds weights and biases that minimize cost
  - we can minimize the cost over all training data, but this takes forever
  - stochastic gradient descent runs gradient descent on mini-batches of data, so we minimize the cost over a mini-batch of training data and use a different mini-batch for each iteration
  - SGD is more noisy, but much much faster
back-propagation (implementation of gradient descent for neural networks)
- implement the optimization using a matrix computation (single pass at each iteration -> you updates all weights and biases in one swoop of matrix computations)

different activation functions:
- sigmoid
- tanh
- ReLU
- softmax (used in the last layer -> normalizes the outputs so they add up to 1 and become probabilities)

how a neural network trains:
- 1) initialize weights and bias
- 2) make forward pass (from inputs you get outputs) and calculate loss/cost
- 3) make a backward pass and calculate the "gradient" (derivative) of cost
- 4) update weights and biases accordingly
- 5) run steps 2-4 iteratively, use mini-batches of data for each iteration
for record-keeping (so you know when you're overfitting)
- 6) after we exhaust all mini-batches, we made one pass through all the data (called an "epoch"), we track the performance on the training and test data so far

prevent over-fitting:
  - early-stopping: stop training when performance on test data starts to decline
  - drop-out: for each iteration (mini-batch), drop out some hidden units at random and update remaining weights and biases, then repeat

automated ML can be used to tune the hyper-parameters of a NN (and figure out the right architecture) -> bayesian optimization is the most popular method:
- trade-off between exploration (very different set of HPs) and exploitation (very similar HPs, just slight tweek)




math behind NNs:
- optimization - SGD stochastic gradient descent
- calculus - chain rule applied to multivariate calculus
- linear algebra - basic matrix algebra and how to vectorize computations

terminology:
- inputs, outputs, weights, biases, activation functions, activations (output of applying activation functions to weighted sums)
- forward pass, backward pass
- gradient descent, stochastic gradient descent, back-propagation
- three ways to run each iteration of the optimization:
  - batch (update weights and biases based on average loss for the whole data)
  - mini-batch (update weights and biases based on average loss for a small sample of data)
  - online training (update weights and biases one row at a time)
- epoch

neural networks motivation:
- show training progress and stop training when it starts to overfit
- the math is basic calculus and LA
- GPUs instead of CPUs
- they do their own feature engineering, allowing for more abstract features in deeper layers

the perceptron model is the most basic neural network building block

how training happens -> GD is the what, SGD is the whatish, BP is the how

back-propagation (implementation of gradient descent for neural networks)

different activation functions:
- sigmoid (between 0 and 1)
- tanh (between -1 and 1)
- softmax (at the last layer)
- ReLU

how a neural network trains:
- 1) initialize weights and biases
- 2) take the next mini-batch of data:
  - a) make a forward pass (which gives you a prediction) and calculate the "loss" (error)
  - b) make a backward pass (which gives you the derivative of loss w.r.t. weights and biases)
  - c) update weights and biases accordingly
- 3) repeat step 2 until you converge
- 4) OPTIONAL if we've reached an epoch (exhausted the mini-batches), then keep track of performance so far


prevent over-fitting:
  - early-stopping - if after a certain epoch performance (on test data) starts to decline then stop training
  - drop-out - for each mini-batch of data (iteration), drop some random units, do the forward and backward pass, update weights and biases (that weren't dropped), then repeat
  - regularization
  - more training data
  - simplify the architecture (fewer HLs, fewer units within each HL) - hyper-parameter tuning
