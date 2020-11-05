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

#### Introduction

Focus on the following performance:
- efficiency
- accuracy
- privacy

#### Related Work

##### Efficient Inference

Efforts have been made by other previous researchers:
- create new efficient models (e.g. SqueezeNets)
- compress & accelerate existing models

##### Privacy-Preserving Inference
Privacy-Preserving: perform the inference on the cloud without leaking any private information

##### Hybrid Edge-Cloud Inference
- Some people send the data from very deep layers of neural network to cloud in order to protect privacy. But this means doing a lot of computation on local platforms.
- Not only the input privacy is important. The ouput privacy is also very important. We want to hide the output data under some situation.

#### A Motivating Example