---
layout: page
title: Extractive Summarization with Discourse Graphs
description: A Kaggle Project of INF554 Machine Learning and Deep Learning course at Ecole Polytechnique
img: assets/img/kaggle_discourse_graph/graph.png
importance: 1
category: work
giscus_comments: true
---

### Description
This project, led by Samuel Gaudin, Alexandre Ver Hulst and I at École Polytechnique part of INF554 course, focuses on identifying key messages in business dialogues using machine learning. By analyzing 137 labeled business dialogues, we explored various features—such as message size, speaker type, sentence embeddings, and sentiment scores—to determine message importance.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/kaggle_discourse_graph/description.png" title="IS note" class="img-fluid rounded z-depth-1" style="width: 50%;" %}
    </div>
</div>
<div class="caption">
    Description of the project.
</div>

### Approach and Models
We implemented a range of machine learning and deep learning models, including logistic regression, support vector machines (SVM), XGBoost, and advanced neural networks. Graph Neural Networks (GNN) and LSTM-based models were particularly effective, with LSTM proving best at capturing dialogue nuances.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/kaggle_discourse_graph/graph.png" title="pyspecies stochastic" class="img-fluid rounded z-depth-1 fixed-aspect-ratio" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/kaggle_discourse_graph/model.png" title="pyspecies stochastic 2" class="img-fluid rounded z-depth-1 fixed-aspect-ratio" %}
    </div>
</div>
<div class="caption">
    Graph of a conversation and final model
</div>

### Results
The LSTM neural network model demonstrated superior performance in understanding professional dialogue, thanks to its ability to process sequential text.