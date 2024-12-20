---
layout: page
title: Reinforcement Learning on financial data
description: A Project of INF581 Advanced Machine Learning and Autonomous Agents course at Ecole Polytechnique
img: assets/img/RL4Trading/trading.png
importance: 6
category: work
---

In this project, we implemented a Reinforcement Learning algorithm for financial data analysis.

Acces to report : 
- [Report](https://drive.google.com/file/d/1mU4c1jeIt4Psimh49YUeQnJWM70Czpcg/view?usp=sharing)
- [Repo](https://github.com/mathias-grau/RL4Trading)

## Data Structure

* We sourced our data from Yahoo Finance via their API, specifically focusing on the closing prices for our modeling purposes.

## Model Architecture

### Environment

* Our environment:
  - A dataframe containing stock price data,
  - A specified time range for action consideration,
  - A balance representing investable funds,
  - A record of the number of shares held at each time step.

### Actions

* Our action space encompassed three distinct types:
  1. Buying a certain proportion of stocks based on the model's confidence in a buy strategy.
  2. Selling a certain proportion of stocks based on the model's confidence in a sell strategy.
  3. Taking no action.


### Deep Q-Network (DQN)

* Our DQN architecture was a blend of various layers, notably incorporating LSTM due to the sequential nature of trading data. Additionally, it considered other relevant factors such as the number of stocks held and the current account balance.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RL4Trading/model1.png" title="LSTM" class="img-fluid rounded z-depth-1 fixed-aspect-ratio" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RL4Trading/model2.png" title="Transformer" class="img-fluid rounded z-depth-1 fixed-aspect-ratio" %}
    </div>
</div>
<div class="caption">
    Two models using combination of RNN and Transformers to predict the next price value.
</div>

### Results

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RL4Trading/triangles.png" title="triangle" class="img-fluid rounded z-depth-1 fixed-aspect-ratio" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RL4Trading/wealth.png" title="wealth" class="img-fluid rounded z-depth-1 fixed-aspect-ratio" %}
    </div>
</div>
<div class="caption">
    Action taken over time and evolution of the value of the account.
</div>