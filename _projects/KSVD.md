---
layout: page
title: K-SVD: An Algorithm for Designing Overcomplete Dictionaries for Sparse Representation
description: PyKSVD is a Python implementation of the K-SVD algorithm based on paper K-SVD by Michal Aharon, Michael Elad, and Alfred Bruckstein.
img: assets/img/KSVD/bg.png
importance: 2
category: work
---

* Course: Machine Learning for Time Series led by Prof. Laurent Oudre 

- Code : [GitHub](https://github.com/mathias-grau/PyKSVD) 
- Report : [PDF](https://drive.google.com/file/d/15XPjozYf9K4HwfK86bSZjujyPpiYFQFZ/view?usp=sharing)
- Library : `pip install pyksvd` on [PyPi](https://pypi.org/project/pyksvd)

## Project Overview

PyKSVD is a Python implementation of the K-SVD algorithm based on paper *K-SVD: An Algorithm for Designing Overcomplete Dictionaries for Sparse Representation* (2006) by Michal Aharon, Michael Elad, and Alfred Bruckstein. 


## Examples

- Image processing : Denoise or complete a corrupted image with missing pixels with patches. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/KSVD/example_corrupted_image_70.png" title="Description" class="img-fluid rounded z-depth-1" style="width: 50%;" %}
    </div>
</div>
<div class="caption">
    Image Reconstruction with 70% missing pixels
</div>