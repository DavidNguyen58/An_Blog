---
date: '2026-02-02T22:13:40Z'
draft: false
title: 'Universal Approximation Theorem'
tags: ["Generalisation Theory"]
ShowToc: true
TocOpen: false # or true to expand by default
#categories: ["tech"]
---

When I first learnt about Deep Learning, I was always wondering how can these neural networks can perform a wide range of complex tasks. The idea of defining an objective function and then train the neural networks to minimise that seems intuitive to understand about the mechanism but does not justify why it would work. It turns out that when I came across the Universal Approximation Theorem, things get clearer. 
## Theorem

The Universal Approximation Theorem, in lose terms, tells us that a feedforward network with a linear output layer and at least one hidden layer with any "squashing" activation function can approximate any continuous function to any desired degree of accuracy. [1]

This has given mathematical justifications that large and deep neural networks can model complex non-linear data found in the real world.

However, it should be noted that the existence of such neural networks does not guarantee the learning algorithm would be able to learn that function.
## Experiment

Let's experiment with a toy example. We will try to construct a simple feedforward neural network to approximate the function:

$$
f(x)=e^{-x^2}
$$

**Model architecture**

Linear → Sigmoid → Hidden (hidden=16) → Linear

**Training configuration**

| Setting | Value |
| --- | --- |
| BATCH_SIZE | 32 |
| EPOCHS | 200 |
| OPTIMISER | ADAM |
| LR | 1e-3 |

The source code could be found in [here](URL_PLACEHOLDER)
## Evaluation

After the training, here is the graph to compare between our model approximation and the target function. As we can see, they're very close to each other!

![Model approximation vs. target function](/uat_img1.png)

The loss over time could be seen below

The training and testing loss to a MSE value of 0.000004, which show similarity between two models

![Training and testing loss over epochs](/uat_img2.png)

## Conclusion

The experiment shows that even a very simple neural network can approximate a "complex" continuous function quite well. I hope this post gives you an intuitive sense of the theorem and why neural networks are so powerful. I do not cover the proof here, but there are several interesting proofs available online. I may write about them in a future post. Happy reading!

## References

[1] Ian Goodfellow, Yoshua Bengio, and Aaron Courville. *Deep Learning*. MIT Press, 2016. Chapter 6: Deep Feedforward Networks.
