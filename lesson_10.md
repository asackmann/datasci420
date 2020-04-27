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
# lesson 10: deep learning (part 2)
## Seth Mottaghinejad
# ___________________

[DataSci 420]: https://www.pce.uw.edu/certificates/data-science
[break time]: https://www.google.com/search?q=online+timer
[lab time]: https://www.google.com/search?q=online+timer

----------------------------------------------------------------

## today's agenda

- **convolutional neural networks**
  - applications
  - motivations
  - basic architecture
- **recurrent neural networks**
  - applications
  - motivations
  - basic architecture

----------------------------------------------------------------

## image processing applications

- **facial** recognition
- **satellite image** analysis in farming or environmental studies
- optical character recognition
- sound analysis through **audiogram**
- **sentiment analysis** can rely on 1-d convolutions
- **image tagging**
- **anomaly detection** in video images

----------------------------------------------------------------

## why use CNNs

- **convolutional neural networks** (CNNs) have dethroned all other image segmentation benchmarks
- image **segmentation** = image **localization** + **classification**
- CNNs preserve **locality** of pixels in an image
- CNNs reduce the connections so we can go deeper: this is done though **shared weights** used by **filters** (aka **kernels**)
- using **transfer learning**, we can directly use features learned from a **pre-trained model**, or **fine-tune** them

----------------------------------------------------------------

<!-- _class: lead -->

![center w:1200](./images/convolutional-architecture.jpg)

image source: [wikipedia.org]

[wikipedia.org]: https://en.wikipedia.org/wiki/Convolutional_neural_network

----------------------------------------------------------------

<!-- _class: lead -->

![center w:1200](./images/cnn-deepr-abstraction.jpg)

image source: [Visualizing and Understanding Convolutional Neural Networks]

[Visualizing and Understanding Convolutional Neural Networks]: http://arxiv.org/pdf/1311.2901v3.pdf

----------------------------------------------------------------

## image processing with NNs

- we use **convolutional filters** to process images: blur, sharpen, invert, detect lines and edges, detect colors, etc.
- CNNs **learn** the convolutional filters that should be applied **layer by layer** in order to detect what's in an image
- deeper layers can detect more complex shapes, allowing for a deeper levels of **feature abstraction**
- new models architectures are tested against **benchmark datasets** such as [ImageNet] (~15 million labeled images from 22K categories)

[ImageNet]: http://www.image-net.org/

----------------------------------------------------------------

<!-- _class: lead -->

![center w:1200](./images/imagenet-competition.jpg)

image source: [paperswithcode.com]

[paperswithcode.com]: https://paperswithcode.com/sota/image-classification-on-imagenet

----------------------------------------------------------------

<!-- _class: lead -->
## [break time]

----------------------------------------------------------------

## natural language processing (NLP) applications

- machine **translation**
- **speech recognition** for virtual assistants
- question answering / conversation modeling
- **named entity** recognition and extraction
- generating image **caption**
- word or sentence completion (called **language modeling**): in this case the data labels itself: **word + context**

----------------------------------------------------------------

<!-- _class: lead -->

![center w:500](./images/nlp-squad.jpg)

image source: [The Stanford Question Answering Dataset]

[The Stanford Question Answering Dataset]: https://rajpurkar.github.io/SQuAD-explorer/

----------------------------------------------------------------

## why use RNNs

- recurrent neural networks (RNNs) can work well with **sequential data** where order matters
- we **unroll** it for $n$ steps and end up with regular a deep neural network, whose weights are shared across time steps
- we can teach them to learn long term information, solving the **vanishing gradient problem** (see LSTMs or GRUs)
- we can improve performance by using **dense representations** (like **word2vec**) instead of **sparse ones** (one-hot encoding)

----------------------------------------------------------------

<!-- _class: lead -->

![center w:1000](./images/unrolled-rnn.jpg)

image source: [Understanding LSTMs]

[Understanding LSTMs]: https://colah.github.io/posts/2015-08-Understanding-LSTMs/

----------------------------------------------------------------

## GRUs

- **gated recurrent units** can combine new information $x_t$ with internal state $h_{t-1}$ from the previous time step
- $z_t = \sigma(W_zx_t + U_zh_{t-1})$ is the **update gate**
- $r_t = \sigma(W_rx_i + U_rh_{t-1})$ is the **reset gate**
- **gates** use **sigmoid** activation $\sigma$ and **element-wise product** $\odot$
- $\tilde h = \tanh(Wx_t + r_t \odot Uh_{t-1})$ is the **current memory**
- $h_t = z_t \odot h_{t-1} + (1-z_t) \odot \tilde h_t$ is the **internal state** (output)

----------------------------------------------------------------

<!-- _class: lead -->

## GRU architecture

![right w:600](./images/gru-architecture.jpg)

image source: [Understanding LSTMs]

[Understanding LSTMs]: https://colah.github.io/posts/2015-08-Understanding-LSTMs/

----------------------------------------------------------------

<!-- _class: lead -->
## the end

<!-- 
- LSTMs explained: https://colah.github.io/posts/2015-08-Understanding-LSTMs/
- For learning about neural networks (with math): http://neuralnetworksanddeeplearning.com/
- If you want to learn more about model interpretation: https://christophm.github.io/interpretable-ml-book/
- Great blog to learn more about topics in deep learning: https://distill.pub/
- Jay Alammar has a great blog explaining deep learning topics: https://jalammar.github.io/
- Stanford's online machine learning course: https://lagunita.stanford.edu/courses/HumanitiesSciences/StatLearning/Winter2016/about
- Caltech's ML course on Youtbe: https://www.youtube.com/watch?v=mbyG85GZ0PI&list=PLD63A284B7615313A
- Stanford's online class on CNNs: http://cs231n.stanford.edu/
- Stanford's online class on deep learning NLP: http://web.stanford.edu/class/cs224n/
 -->

