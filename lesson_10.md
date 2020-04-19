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
# lesson 10: deep learning (part 2)
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

Docker
- like a VM, but better (more lightweight), scale different parts of your applications independently
- Dockerfiles -> Docker images -> Docker container (ANALOGY - conda environment file -> conda environment -> launch a Jupyter notebooks on the environment)- 

- online learning - NNs can learn one example at a time (this is very noisy, but you need little memory)

- batch learning - NNs learning on the whole training data at once (this is not noisy, but almost always impossible because we don't have enough memory)

- between the two - mini-batches

- Google's word2Vec (wordvectors, word embeddings)

- the h layer can be thought of as an "embedding" ("encodings")
- Word embeddings - One-hot-encoded word -> Dense embedding
- Word embeddings - Google's "Word2Vec"
- Transfer learning - take pre-trained model and "fine-tune" it
- "Attention" is all you need! -> Transformer architecture (feed-forward only)

- LSTMs explained: https://colah.github.io/posts/2015-08-Understanding-LSTMs/
- For learning about neural networks (with math): http://neuralnetworksanddeeplearning.com/
- If you want to learn more about model interpretation: https://christophm.github.io/interpretable-ml-book/
- Great blog to learn more about topics in deep learning: https://distill.pub/
- Jay Alammar has a great blog explaining deep learning topics: https://jalammar.github.io/
- Stanford's online machine learning course: https://lagunita.stanford.edu/courses/HumanitiesSciences/StatLearning/Winter2016/about
- Caltech's ML course on Youtbe: https://www.youtube.com/watch?v=mbyG85GZ0PI&list=PLD63A284B7615313A
- Stanford's online class on CNNs: http://cs231n.stanford.edu/
- Stanford's online class on deep learning NLP: http://web.stanford.edu/class/cs224n/


- the h layer can be thought of as an "embedding" ("encodings")
- Word embeddings - One-hot-encoded word -> Dense embedding
- Word embeddings - Google's "Word2Vec"
- Transfer learning - take pre-trained model and "fine-tune" it
- "Attention" is all you need! -> Transformer architecture (feed-forward only)

- LSTMs explained: https://colah.github.io/posts/2015-08-Understanding-LSTMs/
- For learning about neural networks (with math): http://neuralnetworksanddeeplearning.com/
- If you want to learn more about model interpretation: https://christophm.github.io/interpretable-ml-book/
- Great blog to learn more about topics in deep learning: https://distill.pub/
- Jay Alammar has a great blog explaining deep learning topics: https://jalammar.github.io/
- Stanford's online machine learning course: https://lagunita.stanford.edu/courses/HumanitiesSciences/StatLearning/Winter2016/about
- Caltech's ML course on Youtbe: https://www.youtube.com/watch?v=mbyG85GZ0PI&list=PLD63A284B7615313A
- Stanford's online class on CNNs: http://cs231n.stanford.edu/
- Stanford's online class on deep learning NLP: http://web.stanford.edu/class/cs224n/


