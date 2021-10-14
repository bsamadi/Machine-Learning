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

The self-attention mechanism:

<img src="https://latex.codecogs.com/svg.image?\boldsymbol{Q}&space;\in&space;\mathbb{R}^{N\times&space;d},&space;\boldsymbol{K}&space;\in&space;\mathbb{R}^{N\times&space;d},&space;\boldsymbol{V}&space;\in&space;\mathbb{R}^{N\times&space;d}" title="\boldsymbol{Q} \in \mathbb{R}^{N\times d}, \boldsymbol{K} \in \mathbb{R}^{N\times d}, \boldsymbol{V} \in \mathbb{R}^{N\times d}" />

<img src="https://latex.codecogs.com/svg.image?MSA(\textbf{Q},\textbf{K},\textbf{V})=softmax(\frac{\mathbf{Q}\mathbf{K}^T}{\sqrt{d}})\textbf{V}" title="MSA(\textbf{Q},\textbf{K},\textbf{V})=softmax(\frac{\mathbf{Q}\mathbf{K}^T}{\sqrt{d}})\textbf{V}" />

Our model is
trained end-to-end with a per-pixel cross-entropy loss. At
inference time, argmax is applied after upsampling to obtain a single class per pixel.


<img src="Segmenter_compare_chart.PNG"
   alt="Network"
   style="float: left; margin-right: 10px;" />
   
 
<img src="Segmenter_compare_table.PNG"
   alt="Network"
   style="float: left; margin-right: 10px;" />
   
Inference. To handle varying image sizes during inference,
we use a sliding-window with a resolution matching the
training size. For multi-scale inference, following standard
practice [10] we use rescaled versions of the image with
scaling factors of (0.5, 0.75, 1.0, 1.25, 1.5, 1.75) and left-right flipping and average the result   
