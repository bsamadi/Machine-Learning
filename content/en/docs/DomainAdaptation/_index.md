---
katex: true
markup: "mmark"
title: "Domain Adaptation"
linkTitle: "Domain Adaptation"
weight: 1
description: >
  Here's where you can find some domain adaptation techniques.
---

* Note: This page is a mixed up of different references. Networks and algorithms and some texts are taken from the references.

The deep neural networks trained on
training datasets (source domain) cannot generalize well on the application datasets (target domain) because there is a discrepancy between assumptions on the source domain and the target domain. For example, in medical imaging data may be collected in different medical centers, the radiolosoists may use different machine settings or their behaviour sometimes may affect the data characterization. Essentially, the difference in data distribution between domains makes it difficult
to transfer knowledge from the source to target domains. This transferring problem is known as domain shift (Torralba
and Efros 2011).[11]
Domain adaptation tackles the domain shift problem concerning two different datasets. Specifically 
Unsupervised domain adaptation (UDA) concerns
the domain shift problem while transferring the model
from a labeled source domain to an unlabeled target domain.[11]
The common idea of UDA is to make to transfer the both datasets ot a feature space which has the same information for both domains (long et al. 2015;
Ganin et al. 2016). 

22
applications such as natural language processing [12, 27] and computer vision [24, 65, 67].

Instead of decreasing the distance betweem the two domains in training and testing time, we can use their moments.
Moment-based algorithms perform particularly well in many practical tasks [21, 4, 53, 65,
67, 66, 30, 34, 68, 42, 45, 28, 63, 64, 46, 44].

similarity measure:
Wasserstein distance [15], the Maximum Mean Discrepancy [37] or the f-divergences [69]
Appropriate distance function for domain adaptation [8, 15, 36, 37, 69, 24]

11
Previous works in domain adaptation are majorly based on two techniques: 

* domain-adversarial learning
In particular, the domain-adversarial
learning methods (Ganin et al. 2016; Tzeng et al. 2017)
train a domain discriminator to distinguish whether the feature is from the source domain or target domain. To fool
the discriminator, the feature generator has to output similar source and target feature distributions. However, it is
challenging for this type of UDA methods to learn discriminative features on the target domain (Saito et al. 2018;
Xie et al. 2018). That is because they overlook whether the
aligned target features can be discriminated by the classifier.
it aligns feature distributions between domains but does not consider whether the
target features are discriminative.
domain-adversarial
learning cannot match the multi-modal distributions due to practical issues,
e.g., mode collapse (Che et al. 2017)

* self-training.
self training - > psuedo label -> . However, the alignment between the source and target feature
distributions is implicit and has no theoretical guarantee.
With unmatched target features, self-training based methods
can lead to a drop of performance in the case of shallow networks (Zou et al. 2018; Saito et al. 2019).

It utilizes the model predictions to enhance the discrimination of target features, but it is unable to explicitly
align domain distributions.
Recently, many works apply the above self-training based
methods to unsupervised domain adaptation (Zou et al.
2018; Chen, Xue, and Cai 2019; French, Mackiewicz, and
Fisher 2018). These UDA methods implicitly encourage the
class-wise feature alignment between domains and achieve
surprisingly good results on multiple UDA tasks.


33
The performance of computer vision models has been
improved significantly by deep neural networks that take
advantage of large quantities of labeled data. However,
the models trained on one dataset typically perform
poorly on another different but related dataset [1], [2].

Existing UDA algorithms attempt to mitigate domain shifts by only considering the classifier-induced discrepancy between the two
domains, which can reduce the domain divergence [3].

 Advances in adversarial DA
can always be found in recently reported works. Long
et al. propose to measure the domain divergence by
considering the distribution correlations for each class of
objects [16], [17], [18]. Domain separation network [6] is
also proposed to better preserve the component that is
private to each domain before aligning the latent feature
distributions.

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

## [Learning Bounds for Moment-Based Domain Adaptation](https://arxiv.org/pdf/2002.08260.pdf)
Note: Most of the text here have been copied from [here](https://arxiv.org/pdf/2002.08260.pdf).

* Question: which further conditions can we expect a discriminative model to perform
well on a future test sample given that only finitely many moments are aligned with those of a prior training sample

Ben-David et al. [8, 11, 7, 9] propose bounds on the misclassification
probability of discriminative models for domain adaptation. 

## [discriminative feature alignment (DFA)](https://arxiv.org/pdf/2006.12770.pdf)
Note: Most of the text here have been copied from [here](https://arxiv.org/pdf/2006.12770.pdf).
[Code:](https://github.com/JingWang18/Discriminative-Feature-Alignment)

* idea

  * construct a common feature space under the guidance of the Gaussian prior.

![Gaussian Prior](DAL_idea.JPG)

  * instead of the discriminator error, it minimizes the direct L1-distance between the decoded samples.

$$L_1(\bold{x}_s,\hat{\bold{x}}_t) \propto -\log_p(\bold{x}_s | \bold{z}_t)$$

* Distribution alignment

![Distribution Alignment](DAL_arch.JPG)

* Network

![Network](DAL_net.JPG)

* Algorithm

  * Adversarial Domain Adaptation

![Algorithm 1](DAL_Alg1.JPG)

  * Non-adversarial Domain Adaptation

![Algorithm 2](DAL_Alg2.JPG)

* Decoder 

The proposed regularization has two functionalities in
our model: 1) distribution alignment; 2) discriminative
feature extraction. The distribution alignment mechanism
alone cannot guarantee the produced latent distribution
p(zt) is adequately discriminative for F to generalize well
to the target domain. To further enforce G to focus on the
cross-domain classification discriminative characteristics
of the target samples, we let the weight matrices of G
and D be symmetric. The choice of weight tying for the
proposed encoder-decoder is motivated by the denoising
autoencoder (DAE) [26]. DAE shows that the tying weight
makes it more difficult for an encoder to stay in the linear
regime of its nonlinearity.

## [Maximum Classifier Discrepancy for Unsupervised Domain Adaptation](https://arxiv.org/pdf/1712.02560.pdf)
* Idea: to align source and target features by utilizing the task-specific classifiers as a discriminator in order to consider the relationship between class
boundaries and target samples.

![idea](DA_Classification.JPG)

* Network and algorithm

  * Step A: train both classifiers and generator to
classify the source samples correctly. In order to make classifiers and generator obtain task-specific discriminative features, this step is crucial. We train the networks to minimize
softmax cross entropy. The objective is as follows:

$$ min_{G,F1,F2}L(\bold{X}_s, \bold{Y}_s)$$

[Step B]

![Step B](DA_StepB.JPG)

[Step C]

![Step C](DA_StepC.JPG)

* **What is it good for?**: What types of problems does your project solve? What are the benefits of using it?

* **What is it not good for?**: For example, point out situations that might intuitively seem suited for your project, but aren't for some reason. Also mention known limitations, scaling issues, or anything else that might let your users know if the project is not for them.

* **What is it *not yet* good for?**: Highlight any useful features that are coming soon.

## Where should I go next?

Give your users next steps from the Overview. For example:

* [Getting Started](/getting-started/): Get started with $project
* [Examples](/examples/): Check out some example code!
