### DataMix: Efficient Privacy-Preserving Edge-Cloud Inference

#### Abstract

Deep neural network can be run either:
- locally (e.g. mobile phone)
- remotely (send to cloud)

However, either way has constraints.
- local - hardware restrictions
- cloud - privacy problems

This paper introduces DataMix (privacy-preserving edge-cloud inference framework).

- complete the majority of computation on cloud.
- do mixing and de-mixing operations for data updated to cloud in order to protect privacy.

#### 1. Introduction

Focus on the following performance:
- efficiency
- accuracy
- privacy

#### 2. Related Work

##### Efficient Inference

Efforts have been made by other previous researchers:
- create new efficient models (e.g. SqueezeNets)
- compress & accelerate existing models

##### Privacy-Preserving Inference
Privacy-Preserving: perform the inference on the cloud without leaking any private information

##### Hybrid Edge-Cloud Inference
- Some people send the data from very deep layers of neural network to cloud in order to protect privacy. But this means doing a lot of computation on local platforms.
- Not only the input privacy is important. The ouput privacy is also very important. We want to hide the output data under some situation.

#### 3. A Motivating Example

For example, we take two pictures $A$ and $B$, where $A$ is a dog picture and $B$ is a cat picture.

Here we can mix these two pictures with coefficients 
$\textbf{c}=[0.7,0.3]^T$, $\textbf{c'}=[0.6,0.4]^T$

$$\textbf{m(c)} = [A,B] \cdot \textbf{c} = 0.7A+0.3B$$

$$\textbf{m(c')} = [A,B] \cdot \textbf{c'} = 0.6A+0.4B$$

$$[\tilde{y_A},\tilde{y_B}] = [\tilde{y}_{m(c)},\tilde{y}_{m(c')}] \cdot C^{-1}$$

where $C^{-1} = [c,c']$

Here we only send the mixup to the cloud, and transmit only mixed inputs and outputs for model inference. Attackers on the network and cloud cannot access the coefficients, therefore they cannot recover the original private data from the mixed inputs and outputs. So this method can preserve private information. 

Also, the method is not locally-computational.

However, though it can protect original data from being recovered, some private information can still be recognized. In the paper, here is an example where from the mixed pictures we can still identify the color of the cat.

So the following part extend the method to DataMix for a general privacy-preserving framework.


#### 4. Method

Following the order:
- describe problem setting
- extend mixing & de-mixing for DataMix with
    - larger group size
    - intermediate features processing
- analyze the design choice & provide techniques for practice

##### Problem Setting
