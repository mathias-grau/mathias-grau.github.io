---
layout: page
title: Cross-diffusion in population dynamics
description: with background image
img: assets/img/pyspecies.gif
importance: 1
category: work
related_publications: true
---

This project was conducted under the supervision of Vincent Bansaye and Maxime Breden (CMAP).

In population dynamics, cross-diffusion reveals local interactions that lead to spatial segregation between two species. To describe these repulsive effects, we first develop a probabilistic model that also considers birth and death events, simulated using the Gillespie algorithm. This approach naturally leads, in the limit, to a deterministic behavior described by a system of partial differential equations. Due to the presence of a nonlinear cross-diffusion term in the initial system, solving it numerically is challenging, especially over long time periods.

To reach and observe the system's stationary states, we subsequently implement an efficient integration algorithm for the continuous model. We then formulate some conjectures on conditions that may promote segregation at equilibrium and demonstrate initial results in this regard.

Finally, we explain and illustrate how, and to what extent, the continuous model can indeed be understood as the natural limit of the stochastic Markov process.

## Stochastic implementation

In this section, we simulate this deterministic evolution using a probabilistic approach and will later demonstrate how these two models are connected. We work within a space containing an integer number of individuals of each species distributed across MM discrete sites. Three types of events can occur: an individual moving from one site to an adjacent site, the birth of an individual, or the death of an individual. The probability of each event occurring within a given time interval depends on the concentration of each species and their coexistence, following a scheme similar to the SKT model equation, which we will detail in the final section. These events influence the overall population distribution and occur after a certain reaction time.

Each individual remains at a site for a random period, determined by an exponential distribution with an average inversely proportional to the number of individuals at that site. If an individual moves, the destination site is chosen uniformly from adjacent sites. The model then evolves after the reaction time of the individual that reacts first, resetting the reaction times for all other individuals according to the new distribution. This initial reaction time can thus be regarded as the general jump time of the given distribution.


## Deterministic implementation

To recap, the SKT model we study consists of the following system of equations:

\[
\begin{cases}
\partial_t u - \Delta (d_1 u + d_{11} u^2 + d_{12} uv) = u (r_1 - a_1 u - b_1 v) \\
\partial_t v - \Delta (d_2 v + d_{21} uv + d_{22} v^2) = v (r_2 - b_2 u - a_2 v)
\end{cases}
\]

where \( u(x, t) \) and \( v(x, t) \) are the concentrations of the two species. The coefficients are grouped in the diffusion matrix \( D \) and the reaction matrix \( R \):

\[
D = \begin{pmatrix} d_1 & d_{11} & d_{12} \\ d_2 & d_{21} & d_{22} \end{pmatrix}, \quad R = \begin{pmatrix} r_1 & a_1 & b_1 \\ r_2 & b_2 & a_2 \end{pmatrix}.
\]

We operate under periodic boundary conditions, but the results we present can also be extended to homogeneous Neumann boundary conditions.

**Note:** The SKT model generalizes many classic models in population dynamics. For example, let \( a \), \( b \), \( c \), and \( d \) be positive constants. The Lotka-Volterra predator-prey model corresponds to:

\[
D = \begin{pmatrix} 0 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}, \quad R = \begin{pmatrix} a & 0 & b \\ -d & -c & 0 \end{pmatrix}.
\]

It can be shown, under certain conditions, that the semi-continuous model is the deterministic limit of the stochastic framework previously described. We quickly developed a library to solve this class of systems to:

1. Experimentally understand the roles of various parameters;
2. Quantify the difference between the two models, and even the rate of convergence.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/pyspecies.gif" title="gif pyspecies" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Annimation of the cross diffusion using the deterministic approach.
</div>

The library is available at [PySpecies](https://pypi.org/project/PySpecies/)