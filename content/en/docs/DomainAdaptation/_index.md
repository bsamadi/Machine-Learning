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

The deep neural networks pre-trained on
existing datasets cannot generalize well on the new data with
different appearance characteristics. Essentially, the difference in data distribution between domains makes it difficult
to transfer knowledge from the source to target domains.
This transferring problem is known as domain shift (Torralba
and Efros 2011).
Unsupervised domain adaptation (UDA) tackles the
above domain shift problem while transferring the model
from a labeled source domain to an unlabeled target domain.
The common idea of UDA is to make features extracted by
neural networks similar between domains (Long et al. 2015;
Ganin et al. 2016). In particular, the domain-adversarial
learning methods (Ganin et al. 2016; Tzeng et al. 2017)
train a domain discriminator to distinguish whether the feature is from the source domain or target domain. To fool
the discriminator, the feature generator has to output similar source and target feature distributions. However, it is
challenging for this type of UDA methods to learn discriminative features on the target domain (Saito et al. 2018;
Xie et al. 2018). That is because they overlook whether the
aligned target features can be discriminated by the classifier.

self training - > psuedo label -> . However, the alignment between the source and target feature
distributions is implicit and has no theoretical guarantee.
With unmatched target features, self-training based methods
can lead to a drop of performance in the case of shallow networks (Zou et al. 2018; Saito et al. 2019).

Previous works in domain adaptation are majorly based on two techniques: 

* domain-adversarial learning

it aligns feature distributions between domains but does not consider whether the
target features are discriminative.
domain-adversarial
learning cannot match the multi-modal distributions due to practical issues,
e.g., mode collapse (Che et al. 2017)

* self-training.

It utilizes the model predictions to enhance the discrimination of target features, but it is unable to explicitly
align domain distributions.
Recently, many works apply the above self-training based
methods to unsupervised domain adaptation (Zou et al.
2018; Chen, Xue, and Cai 2019; French, Mackiewicz, and
Fisher 2018). These UDA methods implicitly encourage the
class-wise feature alignment between domains and achieve
surprisingly good results on multiple UDA tasks.


## [Adversarial-Learned Loss for Domain Adaptation (ALDA)](https://arxiv.org/pdf/2001.01046.pdf)
Note: Most of the text here have been copied from [here](https://arxiv.org/pdf/2001.01046.pdf).

* Idea: integrate domain-adversarial
learning and self-training method.

To achieve this goal, we first analyze
the loss function of self-training with pseudo-labels (Zou et
al. 2018) on the unlabeled target domain. Previous works
in learning from noisy labels (Sukhbaatar and Fergus 2014;
Zhang and Sabuncu 2018) proposed accounting for noisy
labels with a confusion matrix. Following their analyzing
approach, we reveal that the loss function using pseudolabels (Zou et al. 2018) differs from the loss function learned
with the ground truth by a confusion matrix.

## Why do I want it?

Help your user know if your project will help them. Useful information can include: 

* **What is it good for?**: What types of problems does your project solve? What are the benefits of using it?

* **What is it not good for?**: For example, point out situations that might intuitively seem suited for your project, but aren't for some reason. Also mention known limitations, scaling issues, or anything else that might let your users know if the project is not for them.

* **What is it *not yet* good for?**: Highlight any useful features that are coming soon.

## Where should I go next?

Give your users next steps from the Overview. For example:

* [Getting Started](/getting-started/): Get started with $project
* [Examples](/examples/): Check out some example code!

