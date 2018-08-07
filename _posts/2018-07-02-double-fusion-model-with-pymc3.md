---
layout: post
title: Bayesian Modeling Using PyMC3
tags: [statistical-modeling, neuroscience]
---

Recently, I have completed the biostatistics M.S. thesis under the instructions of Dr. Hakmook Kang. The thesis work is mainly focused on the modeling part, which is used to explain the model in the papar by [Kang, Hakmook, et al. "A bayesian double fusion model for resting-state brain connectivity using joint functional and structural data." Brain connectivity 7.4 (2017): 219-227](https://www.liebertpub.com/doi/abs/10.1089/brain.2016.0447). You can read the [Readme](https://htmlpreview.github.io/?https://github.com/wangruinju/Double-Fusion/blob/master/README.html), [slides](https://github.com/wangruinju/Double-Fusion/blob/master/slides.pdf) or code in [Double-Fusion](https://github.com/wangruinju/Double-Fusion) from GitHub. Also, I want to express thanks to the fantastic course ([BIOS 8366: advanced statistical computing](https://github.com/fonnesbeck/Bios8366)) taught by Dr. Fonnesbeck Christopher, which allows me to learn PyMC3 from scratch.

![model]({{ "/assets/img/spatial_temporal_model.png"}})

Abstract about this work:

Our brain network, as a complex integrative system, consists of many different regions that have each own task and function and simultaneously share structural and functional information. With the developed imaging techniques such as functional magnetic resonance imaging (fMRI) and diffusion tensor imaging (DTI), researchers can investigate the underlying brain functions related to human behaviors and some diseases or disorders in the nervous system such as major depressive disorder (MDD).

We developed a Bayesian hierarchical spatiotemporal model that combined fMRI and DTI data jointly to enhance the estimation of resting-state functional connectivity. Structural connectivity from DTI data was utilized to construct an informative prior for functional connectivity based on resting-state fMRI data through the Cholesky decomposition in a mixture model. The analysis took the advantages of probabilistic programming package as [PyMC3](https://github.com/pymc-devs/pymc3) and next-generation Markov Chain Monte Carlo (MCMC) sampling algorithm as No-U-Turn Sampler ([NUTS](https://arxiv.org/abs/1111.4246)). PyMC3 is new, open-source framework with a readable but powerful syntax close to the natural syntax statisticians will use to describe models. NUTS avoids the random walk behavior and sensitivity to correlated parameters by taking a series of steps informed by first-order gradient information. In other words, the NUTS method is a self-tuning variant of Hamiltonian Monte Carlo (HMC).

