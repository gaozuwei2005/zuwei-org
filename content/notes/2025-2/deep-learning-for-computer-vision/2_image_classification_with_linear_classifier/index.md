---
title: CV | Lecture 2 Image Classification with Linear Classifiers
date: 2026-04-10
summary: Data-driven approaches, Linear Classification
---

# Data-driven approaches

image classification: to assign a label to a image

challenges: illumination, background clutter, occlusion, raccoon, deformation, etc

process:
1. collect a dataset of images and labels
2. use ML algorithms to train a classifier (takes in images & labels, return model)
   training function: memorize all data & label
3. evaluate the classifier on new images (takes in model & test images, return outputs)
   predict function: predict the label of the test image

**original idea**: output the label of the "nearest" image from the test image.
- L1 distance (Manhattan distance): $\displaystyle d_1(I_1, I_2) = \sum_p |I_1^p - I_2^p|$
	- training time: $O(1)$ (no training)
	- prediction time: $O(samples · dim)$.
	- we want to accerlarate prediction.
- L2 distance (Euclidean distance): $d_2(I_1, I_2) = \sqrt{\sum_p (I_1^p - I_2^p)^2}$
- L1 is sensitive on feature values; L2 is not.
- want to preserve the feature $\rightarrow$ L1 distance; feature is arbitrary $\to$ L2 distance

**K-Nearest Neighbor**: take majority vote from nearest K neighbors.

![](attachments/Pasted%20image%2020260409233322.png)

that will create "white regions". We should collect more samples for these areas.

**Hyperparameter**: choices about the alg themselves.
- is often dataset-dependent or problem-dependent
- referred to hyperparameter tuning in ML alg
- idea #1: choose the hpp that work best on the training data.
- idea #2: choose the hpp that work best on the test data. (kind of cheating)
- idea #3: choose the part of training data, and regard the rest as evaluate test. (may not be the good representative.)
- idea #4: **cross-validation**. split data into folds. and iterarate them as evaluate test and calc the average score. (less practiced on large scale datasets)
- use intuition to set hpp

# Linear Classification

parametric approach:
- $f(x, W)$ (takes in image and parameters, give labels)
- linear classifier $f(x,W) = Wx + b$，where $W$ is $labels · pixels$，$x$ is $pixels · 1$，bias $b$ is $labels · 1$
- linear classifier is the most basic  component  in neuron networks.
- visual viewpoint: what template per class is like 
- geometric viewpoint: find the hyperplane that separate each class from others.
- problems for linear classifier: 
	- cannot regard separated areas as one label
	- cannot create curve boundaries.

process:
- define a loss func that quantifies the errors of the labels on the training data
- come up with a way of efficiently finding the param to minimize the loss func.

**softmax classifier:**
- interpret raw classifier scores as probability distribution (all are positive and the sum is $1$)
- if scores is $s = f(x_i;W)$, then $\displaystyle P(Y = k \mid X = x_i) = \frac{e^{s_k}}{\sum_je^{s_j}}$
- the same framework as logistic regression.
- it's not the only loss function used in classification.

SVM / hinge loss function: $\displaystyle L_i = \sum_{j \ne y_i} \max(0, s_j - s_{y_i} + 1)$


**objective function:**
- to maximize the probability of the correct label.
- loss function 1: $L = -\log(P(Y = k \mid X = x_i))$ whose range is $[0, +\infty)$
- loss function 2: KL divergence $D_{KL}(P||Q) = \sum_y P(y) \log\frac{P(y)}{Q(y)}$
- loss function 3: cross entropy $H(P,Q) = H(p) + D_{KL}(P||Q)$


# Glossary

- illumination
- background clutter
- occlusion
- raccoon
- deformation
- intraclass variation
- context
- paradigm
- agnostic
- finalize
- algebraic
- negate