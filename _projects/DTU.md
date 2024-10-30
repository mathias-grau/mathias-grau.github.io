---
layout: page
title: Enhancing TCR-pMHC Binding Predictions
description: 3A Internship Project Overview (DTU)
img: assets/img/DTU/2.png
importance: 1
category: work
---

* Location: [Technical University of Denmark (DTU)](https://www.dtu.dk/english)
* Group: [Immunoinformatics and Machine Learning Group](https://orbit.dtu.dk/en/organisations/immunoinformatics-and-machine-learning), led by Prof. [Morten Nielsen](https://scholar.google.com/citations?user=ahkeJGgAAAAJ&hl=en)

### Description
This project is dedicated to advancing predictive models for binding interactions between T-cell receptors (TCRs) and peptides presented by Major Histocompatibility Complex (MHC) class I molecules, with applications in vaccine development, cancer immunotherapy, and autoimmune disease management.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/DTU/1.png" title="Description" class="img-fluid rounded z-depth-1" style="width: 50%;" %}
    </div>
</div>
<div class="caption">
    Description of the problem
</div>

### Research Goals and Innovations

The central objective of my research was to develop a more accurate machine learning model to predict how TCRs recognize peptides displayed by Major Histocompatibility Complex (MHC) class I molecules. By refining current methods, my work sought to bridge gaps in prediction accuracy for peptides with limited known TCR interactions, a significant challenge in immunoinformatics. Key steps included using the RSA-based Shrake-Rupley algorithm to identify and prioritize solvent-exposed amino acid residues on TCRs, which are most likely to interact with peptides. Additionally, I employed [ImmuneBuilder](https://www.nature.com/articles/s42003-023-04927-7) to rapidly and accurately predict TCR structures, allowing for efficient computational analysis.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/DTU/2.png" title="example image 1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/DTU/3.png" title="example image 2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/DTU/4.png" title="example image 3" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/DTU/5.png" title="RSA calculation" class="img-fluid rounded z-depth-1" style="width: 50%;" %}
    </div>
</div>
<div class="caption">
    Example of RSA computation for CDR1α: YSGSPE, CDR2α: HISR, CDR3α: ALVTFTGGGNKLT, CDR1β: SGHNT, CDR2β: YYREEE, CDR3β: ASSSTGGGEKDQPQH. Peptides with an RSA of more than 0.15 are shown in red and those with an RSA of less than 0.15 are shown in blue
</div>

To address predictive limitations, I developed a novel machine learning model based on a bidirectional Recurrent Neural Network (RNN) with Gated Recurrent Units (GRUs). This approach enabled the model to capture the dynamic sequence patterns and structural features unique to TCRs and peptides, resulting in an improvement in prediction accuracy, specifically for peptides with fewer positive TCR interactions. Through rigorous validation, including nested cross-validation with early stopping techniques, the model demonstrated a 2.7% increase in AUC0.1, confirming its effectiveness over previous models.

An unexpected finding during this project was that RSA-based removal of residues, though theoretically sound, eventually reduced predictive performance. Consequently, I pivoted to using RSA as an additional feature rather than a filter, but it did not improved the precision either. Thus I only kept the new architecture without intergrating structural features.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/DTU/6.png" title="result 1" class="img-fluid rounded z-depth-1 fixed-aspect-ratio" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/DTU/7.png" title="result 2" class="img-fluid rounded z-depth-1 fixed-aspect-ratio" %}
    </div>
</div>
<div class="caption">
    [1] AUC and AUC0.1 comparison to illustrate the improvement with the new GRU baseline compared to NetTCR2.2, with a pvalue = 1.2 × 10−10 for the Student’s t-test under the hypothesis ”both models have equal performance,” confirming this significant improvement. [2] AUC and AUC0.1 comparison peptide per peptide ranked by the number of positive binders
</div>

#### Key Findings

- Feature Integration: Shifted from RSA-based residue removal to incorporating RSA as an additional model feature, preserving essential structural information.
- New architecture based on GRU layers instead of only convolutions
- Performance Improvement: Achieved a 2.7% increase in AUC0.1, validated through statistical tests, confirming significant improvement over previous models.
- Model Robustness: Enhanced accuracy in identifying peptides with fewer positive binders, demonstrating reliability across diverse peptide data.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/DTU/8.png" title="Architecture" class="img-fluid rounded z-depth-1" style="width: 50%;" %}
    </div>
</div>
<div class="caption">
    New model architecture
</div>

### Conclusion

Initially, our RSA-based approach aimed to retain only accessible residues essential for interactions, but filtering residues by RSA thresholds unexpectedly lowered model performance, likely by excluding valuable structural information. Recognizing RSA's value, we adjusted our strategy to integrate it into the model without removing residues. Building on previous CNN models, we developed a GRU architecture tailored to capture sequential dependencies in TCR-peptide interactions, incorporating structural features like RSA and minimum distance values. Although these features enriched the model’s understanding, they did not yield the expected gains in accuracy, highlighting the complexity of integrating structural data. Rigorous testing showed the GRU model improved predictive performance, especially with challenging peptides, yet RSA and distance features did not consistently enhance results, indicating further exploration is needed for effective feature integration.
