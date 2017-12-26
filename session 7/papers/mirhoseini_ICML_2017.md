## Device Placement Optimization with Reinforcement Learning

> Title: Device Placement Optimization with Reinforcement Learning 

> Conference/Journal: ICML

> Year: 2017

> Authors: 
Azalia Mirhoseini, Hieu Pham, Quoc V. Le, Benoit Steiner, Rasmus Larsen,
Yuefeng Zhou, Naveen Kumar, Mohammad Norouzi, Samy Bengio, Jeff Dean 

### Summary

Decision of placing parts of the neural models on devices is often made by human experts based on simple heuristics and intuitions. In this paper, the authors use 
a sequence-to-sequence model to predict which operations in TF graph should run on which devices. 

### Cool Ideas

Deep Reinforcement Learning:

**States:** Computational Graph: Operators

**Actions:** Which operator should be placed on which device

**Rewards:** The execution time 

Method: Policy gradient


1. Use a sequence-to-sequence model to read input information about the operations as well as the dependencies between them, and then propose a placement for each operation.

2. On computational graphs with large memory footprints, some placements can fail to execute, simply set reward to a large constant, which we call the failing signal.

3. **The input to the encoder RNN is the sequence of operations of the input graph.**, the embedding of each operation is the concatenation of its type, its output shape, and its one-hot encoded adjacency information.

### Questions

I like this paper!

I think the most interesting part of this paper is using sequence-to-sequence model to read operator information directly. Before that, many research paper, like resource management using deep reinforcement learning via generated images as input (heavily preprocessing work, also doesn't make sense), RNN can encoder and decoder words directly, just use and tune it, that's much better.

