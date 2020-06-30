---
title: "Domain Adaptation"
linkTitle: "Domain Adaptation"
weight: 1
description: >
  Here's where you can find some domain adaptation techniques.
---

{{% pageinfo %}}
Note: This page is a mixed up of different references. Networks and algorithms and some texts are taken from the references.
{{% /pageinfo %}}


Previous works in domain adaptation are majorly based on two techniques: 

* domain-adversarial learning

it aligns feature distributions between domains but does not consider whether the
target features are discriminative.

* self-training.

It utilizes the model predictions to enhance the discrimination of target features, but it is unable to explicitly
align domain distributions.

## [Adversarial-Learned Loss for Domain Adaptation](https://arxiv.org/pdf/2001.01046.pdf)
Note: Most of the text here have bben copied from [here](https://arxiv.org/pdf/2001.01046.pdf).

Introduce your project, including what it does or lets you do, why you would use it, and its primary goal (and how it achieves it). This should be similar to your README description, though you can go into a little more detail here if you want.

## Why do I want it?

Help your user know if your project will help them. Useful information can include: 

* **What is it good for?**: What types of problems does your project solve? What are the benefits of using it?

* **What is it not good for?**: For example, point out situations that might intuitively seem suited for your project, but aren't for some reason. Also mention known limitations, scaling issues, or anything else that might let your users know if the project is not for them.

* **What is it *not yet* good for?**: Highlight any useful features that are coming soon.

## Where should I go next?

Give your users next steps from the Overview. For example:

* [Getting Started](/getting-started/): Get started with $project
* [Examples](/examples/): Check out some example code!

