# MNIST Reconstruction using an encoder-decoder framework

A simple encoder-decoder network has various advanced versions and 2 of the most famous of them are **Autoencoders** and **GANs**. In this, I have implemented different types of autoencoders and GANs to reconstruct synthetic MNIST digits. 

![Baisc Generative model](https://user-images.githubusercontent.com/47540320/115956529-eaaef780-a51a-11eb-90a3-e87d3e3cc144.png) ![Baisc Generative model](https://user-images.githubusercontent.com/47540320/115956575-2cd83900-a51b-11eb-96a5-4219b4059cb3.png)


I have used Tensorflow-Keras for this repository.

---

## Models implemented and a brief description

1. **Autoencoders (AE)** 
```
These are neural networks that aim to copy their inputs to their outputs. They work by compressing the input 
into a latent-space representation and then reconstructing the output from this representation. Different 
types of autoencoders used are : 
```

  * **Vanilla autoencoder** - In its simplest form, the autoencoder is a three layers net, i.e. a neural net with one hidden layer. The input and output are the same, and we learn how to reconstruct the input, for example using the adam optimizer and the mean squared error loss function.

  * **Multilayer autoencoder** - If one hidden layer is not enough, we can obviously extend the autoencoder to more hidden layers.

  * **Convolutional autoencoder** - Using autoencoders with Convolutions instead of Fully-connected layers using images (3D vectors) instead of flattened 1D vectors. The input image is downsampled to give a latent representation of smaller dimensions and force the autoencoder to learn a compressed version of the images.

2. **Regularized Autoencoders (RA)**
```
There are other ways we can constraint the reconstruction of an autoencoder than to impose a hidden layer of 
smaller dimension than the input. Rather than limiting the model capacity by keeping the encoder and decoder 
shallow and the code size small, RA use a loss function that encourages the model to have other properties 
besides the ability to copy its input to its output
```
  * **Sparse autoencoder** - Sparse autoencoders are typically used to learn features for another task such as classification. An autoencoder that has been regularized to be sparse must respond to unique statistical features of the dataset it has been trained on, rather than simply acting as an identity function. In this way, training to perform the copying task with a sparsity penalty can yield a model that has learned useful features as a byproduct.

  * **Denoising autoencoder** - Rather than adding a penalty to the loss function, we can obtain an autoencoder that learns something useful by changing the reconstruction error term of the loss function. This can be done by adding some noise to the input image and make the autoencoder learn to remove it. By this means, the encoder will extract the most important features and learn a more robust representation of the data.

3. **Variational Autoencoders (VAE)**
```
Standard autoencoders learn to generate compact representations and reconstruct their inputs well, but asides 
from a few applications like denoising autoencoders, they are fairly limited. The fundamental problem with
autoencoders, for generation, is that the latent space they convert their inputs to and where their encoded 
vectors lie, may not be continuous, or allow easy interpolation.

Variational Autoencoders (VAEs) have one fundamentally unique property that separates them from vanilla 
autoencoders, and it is this property that makes them so useful for generative modelling: their latent spaces
are, by design, continuous, allowing easy random sampling and interpolation. It achieves this by doing these 
2,rather surprising stuffs. At first: making its encoder not output an encoding vector of size n, rather, 
outputting two vectors of size n: a vector of means, μ, and another vector of standard deviations, σ.
```

4. **Generative Adversarial Networks (GANs)**
```
Generative Adversarial Networks or GANs are a deep-learning-based generative model that is used for
Unsupervised Learning. It is basically a system where two competing Neural Networks compete with each
other to create or generate variations in the data. In GANs, there is a Generator network that takes a
sample and generates a sample of data, and after this, the Discriminator network decides whether the 
data is generated or taken from the real sample using a binary Classification problem with the help of 
a sigmoid function that gives the output in the range 0 to 1.
```

---

## Generated outputs of each network

* Image Generation 

![download](https://user-images.githubusercontent.com/47540320/115105406-4823d100-9f7c-11eb-89e7-04a8f5385908.png)

* Image Denoising

![Denoise](https://user-images.githubusercontent.com/47540320/115971741-d6451c00-a567-11eb-9ccf-883839bf9405.JPG)


