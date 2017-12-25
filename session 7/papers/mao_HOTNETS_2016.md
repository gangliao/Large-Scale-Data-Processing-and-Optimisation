## Resource Management with Deep Reinforcement Learning

> Title: Resource Management with Deep Reinforcement Learning 

> Conference/Journal: HotNet

> Year: 2016

> Authors: Hongzi Mao, Mohammad Alizadeh, Ishai Menache, Srikanth Kandula

### Summary

Inspired by recent advances in deep reinforcement learning, the author build systems [DeepRM: a simple multi-resource cluster scheduler] that learn to manage resources directly from experience. It employs a standard `policy gradient` reinforcement learning algorithm.

Traditional solution for these problems are solved using meticulously designed heuristics. It's too specific and not a general purpose solution, which often must be
repeated if some metric changes. i.e., the workload. RL does not require any prior knowledge of the system's behavior to learn these strategies, it can support a variety of objectives just by using `different reinforcement rewards`.

### Cool Ideas

Mapping Resource Management in Cluster into a learning problem.

Assumption:

1. The resource demand of each job is known upon arrival.
2. No preemption and a fixed allocation profile.

**State Space**:
the current allocation of cluster resources and the resource profiles of jobs waiting to
be scheduled as distinct images

**Action Space**:
At each timestamp, the scheduler may want to admit any subset of the M jobs. The authors keep the action space small by allowing the agent to execute more than one 
action in each timestamp.

**Rewards**:

Crafting the reward signal to guide the agent towards good solutions for our objective: `minimizing average
slowdown`.

### Questions

Very Cool Paper! The authors were trying to use deep reinforcement learning to manage 
cluster resource. The novel contribution is that they formulate the problem and describe how to represent it as an RL task. That's amazing! It could be widely in other problems in system area. **But, I am still curious, how to generate the input image?**
Also, there are some assumption may not work in real world.

Resource management problem are ubiquitous in computer systems and networks. There are many research directions such as job scheduling in clusters, bitrate adaptation in video streaming, relay selection in Internet telephony, virtual machine placement in cloud computing, congestion control can take the advantage of deep reinforcement learning to translate problem into a learning problem.

> To minimize average completion time, we can use −|J| (negative the number of unfinished jobs in the system) for the reward at each timestep. 

> To maximize resource utilization, we could reward the agent for the sum of the resource utilizations at each timestep.

> The makespan for a set of jobs can also be minimized by penalizing the agent one unit for each timestep for which unfinished jobs exist.
