---
numbering:
  equation:
    continue: false
---

(chapter9_Hybrid_Gibbs_sampling_in_CUQIpy)=
# Chapter 9: Hybrid Gibbs sampling in CUQIpy

In this chapter, we introduce the hybrid Gibbs sampling framework in CUQIpy. We focus mainly on two cases. The first case is using this framework to sample from a posterior distribution of a BIP with hyperparameters. The second case is using this framework to sample from a posterior distribution of a BIP in which the forward model has multiple, distinct input parameters, that may be of different nature and dimensionality, and require different priors.