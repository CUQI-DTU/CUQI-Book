---
authors:
  - name: Jasper Everink
---

(implicit-paper-summary)=
# 3. A Computational Framework and Implementation of Implicit Priors in Bayesian Inverse Problems

## 3.1. Summary

Bayesian modeling can be done using many families of prior distributions, each with their own behaviors. Most of the time, these priors are defined by explicitly writing down their probability density function (pdf), and we can call these explicit priors. In this work, {cite}`everink2025computational`, we study the opposite, priors for which the pdf cannot be written explicitly or is expensive or impossible to compute.

Although some structure is lost by not having access to a pdf, we can still construct intricate priors that allow for efficient posterior samples. Examples of methods we have in CUQIpy, see {ref}`implicit-prior-chapter`, include:
- Generative models allow for describing a parameter space concentrates on a complicated low-dimensional manifold using a simpler latent space.
- Plug-and-Play (PnP) priors allow for turning deep-learning based denoising methods into prior distributions.
- Regularized Gaussian Distributions allow for turning the deterministic effect of constraints and sparsity-promoting regularization into priors.

Whilst all implicit, these three families of priors are all rooted in different techniques, so implementing them all in a single computational framework such as CUQIpy requires additional care. Therefore, we developed a general framework for studying these implicit priors from a computational perspective, with a focus on their relation to more well-understood explicit priors. 

Improving our understanding of their implicit nature helped us make decisions in their implementation. For example, in their relation to samplers as described in the figure below.

<figure>
<img src="figures/fig_implicit.png" alt="Implicit framework" width="600"/>
<figcaption>Diagrams of two interpretations of implicit priors as part of a Bayesian modeling pipeline.

On the left, the implicit prior is considered separate from the sampler. For example, the `cuqi.implicitprior.RestorationPrior` can contain an arbitrary restorator, e.g., a denoiser, and can be used with any sampling algorithm that accepts restorators, such as `cuqi.sampler.ULA`.

On the right, the implicit prior is strongly linked to a specific sampling method. Each implicit prior forces the use of a specific sampler, such that once a posterior is formed, the summary statistics are fixed in the limit. For example, the `cuqi.implicitprior.RegularizedGaussian` requires the use of `cuqi.sampler.RegularizedLinearRTO`.
</figcaption>
</figure>

In all, the paper presents this computational framework and its impact on the implementation of implicit priors. It provides a large number of code snippets to explain the working and design of these priors in CUQIpy. Furthermore, it demonstrates the application of these implicit priors to a large range of inverse problems, including: deconvolution, conductivity estimation of the Poisson equation, and image inpainting. The link to the code for all examples in the paper is provided in the resources section below.

## 3.2. Resources
- Paper: {cite}`everink2025computational`
- Paper code GitHub repository: https://github.com/CUQI-DTU/Paper-Implicit
- Book chapter on implicit priors: {ref}`implicit-prior-chapter`
