## Accelerating Deep Convolutional Networks using low-precision and sparsity

> Title: Accelerating Deep Convolutional Networks using low-precision and sparsity 

> Conference/Journal: ICASSP

> Year: 2017

> Authors: Ganesh Venkatesh, Eriko Nurvitadhi, Debbie Marr

### Summary

To full expoloit the benefits of their very low-precision (2-bit) weight networks (accelerate the execution time), 
they build a deep learning accelerator core, `DLAC` which can achieve up to 1 TFLOP/mm^2 quivalent for single-precision floating-point operations (~2 TFLOPS/mm^2 for half precision).

### Cool Ideas

Using the approach from [Ternary Weight Networks](https://arxiv.org/abs/1605.04711) Lin et al. that lowers the network weights to a ternary value with the options being [-1, 0, 1].

#### Training Low-precision Networks

1. Pre-initialization from full-precision network

> train the network in full-precision for the first few iterations

2. Skipping lowering of precision for parts of network

> do not lower the precision of the first layer in the network to minimize the information loss

3. Aggressive lowering of learning rate

> maintain a history of the train error and lower the learning rate when the train error does not go down for few iterations.

4. Regularization

> regularize activations to reduce noise and induce more sparsity.

5. ReLU threshold

> vary the thresholds on our rectifier units to induce higher sparsity and reduce noise, reduce the compute requirements of these networks by skipping over operations on zero values (zero-skipping).

#### Deep Learning Accelerator

DLAC is a two-dimensional grid of processing elements with buffers for network weights and input feature map. The `processing elements` have `arithmetic units`, `buffers for output feature map` and `control logic for skipping over operations on zero values` to leverage the sparsity in low-precision networks.

### Questions

Overall, the paper is very clear to present a new deep learning accelerator. I think the advantage of that is low-precision (2-bit) and sparsity to extremely accelerator the execution time for both training an inference.

But, I still think the training process of low-precision network is too trick. For instance, how many iterations you need to do full-precision training for Resnet20, Resenet50, Resnet152? Do you also benchmark on other networks like AlexNet, GoogleNet and VGG ? Any adaptive method can help users ?

I think it's a very good paper, I like the idea of zero-skipping and its logic control implementation in hardware. Accelerator provides greater speed-up as we go deeper in the network because the layers get more and more sparse.