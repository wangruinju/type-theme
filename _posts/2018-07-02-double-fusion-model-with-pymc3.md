---
layout: post
title: Bayesian Modeling Using PyMC3
tags: [statistical-modeling, neuroscience]
---

Thanks to the fantastic course ([BIOS 8366: advanced statistical computing](https://github.com/fonnesbeck/Bios8366)) taught by Dr. Fonnesbeck Christopher, I have completed the biostatistics M.S. thesis under the instructions of Dr. Hakmook Kang. You can read the [Readme](https://htmlpreview.github.io/?https://github.com/wangruinju/Double-Fusion/blob/master/README.html) in HTML and [slides](https://github.com/wangruinju/Double-Fusion/blob/master/slides.pdf). 

# [Double-Fusion](https://github.com/wangruinju/Double-Fusion)

The thesis work is mainly focused on the modeling part, which is used to explain the model in the papar by Kang, Hakmook, et al. "[A bayesian double fusion model for resting-state brain connectivity using joint functional and structural data](https://www.liebertpub.com/doi/abs/10.1089/brain.2016.0447)." Brain connectivity 7.4 (2017): 219-227.

# Introduction

Our brain network, as a complex integrative system, consists of many different regions that have each own task and function and simultaneously share structural and functional information. With the developed imaging techniques such as functional magnetic resonance imaging (fMRI) and diffusion tensor imaging (DTI), researchers can investigate the underlying brain functions related to human behaviors and some diseases or disorders in the nervous system such as major depressive disorder (MDD).

We developed a Bayesian hierarchical spatiotemporal model that combined fMRI and DTI data jointly to enhance the estimation of resting-state functional connectivity. Structural connectivity from DTI data was utilized to construct an informative prior for functional connectivity based on resting-state fMRI data through the Cholesky decomposition in a mixture model. The analysis took the advantages of probabilistic programming package as [PyMC3](https://github.com/pymc-devs/pymc3) and next-generation Markov Chain Monte Carlo (MCMC) sampling algorithm as No-U-Turn Sampler ([NUTS](https://arxiv.org/abs/1111.4246)). PyMC3 is new, open-source framework with a readable but powerful syntax close to the natural syntax statisticians will use to describe models. NUTS avoids the random walk behavior and sensitivity to correlated parameters by taking a series of steps informed by first-order gradient information. In other words, the NUTS method is a self-tuning variant of Hamiltonian Monte Carlo (HMC).

# Installation

To install the Python packages for the project, clone the repository and run:

```
conda env create -f environment.yml
```

from inside the cloned directory. This assumes that [Anaconda Python](https://www.continuum.io/downloads) is installed. And `theanorc` file can follows as:

```
# cpu
[global]
floatX = float 32
config.compile.timeout = 1000

# gpu
[global]
floatX = float32
config.compile.timeout = 1000
device = cuda0
```

For Windows users, environmental variables need to be added in the system setting to use `conda` command in the terminal and `theano` package in Python environment. C++ compiler such as Cygwin needs to be installed before running `pymc3` and `theano` in Windows if it does not exist.

To run the model:

```
# activate the environment
source activate double-fusion
# run the model
python model.py
```

We also add some examples using CPU/GPU on Vanderbilt Advanced Computing Center for Research and Education (ACCRE).



