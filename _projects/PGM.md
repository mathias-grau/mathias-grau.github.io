---
layout: page
title: Denoising Diffusion Probabilistic Models (DDPM)
description: Introduction to Probabilistic Graphical Models and Deep Generative Models Course as part of M2 MVA
img: assets/img/PGM/bg.png
importance: 2
category: work
---

* Course: [Introduction to Probabilistic Graphical Models and Deep Generative Models](https://lmbp.uca.fr/~latouche/mva/IntroductiontoProbabilisticGraphicalModelsMVA.html), led by Profs. Jean [Pierre Latouche](https://lmbp.uca.fr/~latouche) - [Pierre-Alexandre Mattei](https://pamattei.github.io) 

## Project Overview

This project focuses on the implementation of **Denoising Diffusion Probabilistic Models (DDPM)** as described in *Ho et al.* (2020). The goal was to implement the training and sampling processes of the DDPM model, optimizing it using **Hugging Face's Diffusers** library, and apply it to a new dataset of **impressionist paintings**. 

We successfully implemented the DDPM model as outlined in *Ho et al. (2020)*, which is one of the seminal works in the field of diffusion models. This paper laid the groundwork for many advancements, including improvements in sampling efficiency, conditioning, multi-task learning, and reducing the computational costs associated with diffusion models.

### Training Data

The dataset used for training consists of 2287 paintings from the **WikiArt** collection, specifically focusing on impressionist artworks from renowned artists.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/PGM/trainimages.png" title="Description" class="img-fluid rounded z-depth-1" style="width: 50%;" %}
    </div>
</div>
<div class="caption">
    Training Samples
</div>

The dataset used here focuses on impressionist paintings by the following artists:

- Claude Monet
- Pierre-Auguste Renoir
- Edgar Degas
- Camille Pissarro
- Alfred Sisley
- Paul Cezanne
- Berthe Morisot
- Mary Cassatt
- Gustave Caillebot

### Implementation

The implementation follows the parameters from the article, with optimizations using **Hugging Face's Diffusers** library, which significantly simplified the process of training and inference for diffusion-based models.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/PGM/output.png" title="Outputs" class="img-fluid rounded z-depth-1" style="width: 50%;" %}
    </div>
</div>
<div class="caption">
    Outputs generated
</div>

We also implemented new functions and classes that extend Hugging Face diffusion library to visualize the denoising process : 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/PGM/denoisingsmall.png" title="Denoising" class="img-fluid rounded z-depth-1" style="width: 50%;" %}
    </div>
</div>
<div class="caption">
    Outputs generated
</div>

### Conclusion

By addressing some of the fundamental challenges faced by other generative modeling techniques, diffusion models have emerged as a robust alternative. Their deterministic and iterative structure lends itself to interpretability, and their performance rivals state-of-the-art methods, especially in tasks requiring high-fidelity image synthesis.

This project explores the theoretical underpinnings, practical advancements, and broader implications of the DDPM framework. By delving into the foundational aspects of this paper, we aim to understand its role in reshaping the landscape of generative modeling and its potential to inspire future innovations.

### References

```bibtex
@misc{ho2020denoisingdiffusionprobabilisticmodels,
      title={Denoising Diffusion Probabilistic Models}, 
      author={Jonathan Ho and Ajay Jain and Pieter Abbeel},
      year={2020},
      eprint={2006.11239},
      archivePrefix={arXiv},
      primaryClass={cs.LG},
      url={https://arxiv.org/abs/2006.11239}, 
}

@misc{huggingfacecourse,
  author = {Hugging Face},
  title = {The Hugging Face Diffusion Models Course, 2022},
  howpublished = "\url{https://huggingface.co/course}",
  year = {2022},
}

@misc{wikiart_dataset,
  author       = {WikiArt},
  title        = {WikiArt Dataset},
  year         = {2024},
  url          = {https://www.wikiart.org/},
  note         = {Accessed: 2024-11-25},
}
```

