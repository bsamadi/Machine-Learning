---
title: "Segmentation"
linkTitle: "Segmentation"
weight: 4
description: >
  What does your user need to understand about your project in order to use it - or potentially contribute to it? 
---

[Accurate and robust deep learning-based segmentation of the prostate clinical target volume in ultrasound images](https://www.sciencedirect.com/science/article/pii/S1361841519300623)

[Panoptic Segmentation: Unifying Semantic and Instance Segmentation](http://presentations.cocodataset.org/COCO17-Invited-PanopticAlexKirillov.pdf)

[Segmenter: Transformer for Semantic Segmentation](https://arxiv.org/pdf/2105.05633.pdf)
[code](https://github.com/rstrudel/segmenter)

In contrast to convolution-based methods, our approach
allows to model global context already at the first layer
and throughout the network. We build on the recent Vision
Transformer (ViT) and extend it to semantic segmentation.

However, the modeling of global interactions comes at a quadratic cost which makes such methods prohibitively expensive when applied to raw image pixels [11].


<img src="Segmenter.PNG"
   alt="Network"
   style="float: left; margin-right: 10px;" />

Transformer Encoder
L layers, multi-headed self-attention (MSA), ponit-wise MLP, Layer Norm (LN)

<img src="https://latex.codecogs.com/svg.image?a_{i-1}&space;=&space;MSA(LN(z_{i-1}))&plus;z_{i-1}" title="a_{i-1} = MSA(LN(z_{i-1}))+z_{i-1}" />
<img src="https://latex.codecogs.com/svg.image?z_{i}&space;=&space;MLP(LN(a_{i-1}))&plus;a_{i-1}" title="z_{i} = MLP(LN(a_{i-1}))+a_{i-1}" />
