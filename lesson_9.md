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
# lesson 9: deep learning (part 1)
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




try to tune an NN on tensorflow playground

discuss differences between deep learning vs traditional ML

deep learning applications
- auto-encoders (unsupervised learning)
- convolutional networks for image classification
- recurrent neural networks
- deep reinforcement learning

restricted boltzmann machines
- larger family of models known as auto-encoders (unsupervised)
- extract features (encoder) and reconstruct inputs (decoder)
- generative (as opposed to discriminative)

auto-encoders example
- kind of like PCAs but with non-linearity (used for dimensionality reduction and data compression)
- denoising images (input is noisy, output is clean)
- remove watermarks and reconstruct image

deep belief networks
- an RBM at each layer
- learning happens layer by layer
- pre-train it so you only needs small labeled dataset

convolutional networks (image segmentation = image localization + classification)
- can we preserve locality of pixels in images?
- can we reduce the connections without simplifying the architecture too much?
  - anwer to both -> shared weights used by filters (aka kernels)
- series of convolutional + pooling layers with padding + extra channels and fully connected layer at the end
- we can retrain the fully-connected layer at the end on more specific data -> this is called "transfer learning"

NN frameworks:
- high-level language (library) for training NNs
  - I don't want to do linear algebra explicitly - call `forward` and `backward`
- specify the "architecture" (number of hidden layers, hidden units, activation functions, connections)
- specify some of the "math" - loss function, activation functions, "auto-differentiation"
- CPU vs GPU vs TPU (or FPGA) - I don't want my code to change if I switch the context

Tensorflow and Pytorch
- Tensorflow is "static" (symbolic) - kind of like compiled languages
  - Tensorflow 2.0 is dynamic by default
  - Tensorflow as of now is a little better at operationalization
  - support for the very popular, high-level Keras library
- Pytorch is "dynamic" (imperative)
  - Pytorch is more popular in academia (for research)

image -> apply 16 filters -> apply pooling -> apply 32 filters -> apply pooling -> apply 64 filters -> apply pooling
