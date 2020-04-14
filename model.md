---
layout: default
title: SEIRD model and inference scheme
usemathjax: true
---

[BACK](./)


# SEIRD model:


The model we consider is inspired by what is happening in UK: in the first phase of the emergency, the majority of diagnosed people 
are admitted into hospital. We assume that thereafter, they are 
 isolated, meaning that they are not able to spread the infection anymore. Therefore, we assume that after the exposed state, all patients 
spend some time in the $I^{SC}$ one, and after that some of them will go directly to $R$, and some to $I^C$. From $I^C$, 
they can either decease (going into the $D$ state) or recover (to $R$). Essentially, this means that the subclinical state is splitted in two.

We consider 5 different age groups, and 7 different states; the transition pattern can be seen in the following image: 

![SEIRD model](https://raw.githubusercontent.com/LoryPack/COVID19-epidemics-forecast-England/master/img/SEIRD.png?token=AIT3WHE77BMEFWECRDZO36K6T33XW)

The parameters are therefore the following: 

- $\beta$ transmission rate
- $\kappa$ daily probability of exposed individual becoming infectious
- $\gamma_{C}$ rate of going from from $I_{SC1}$ tp $I_C$
- $\gamma_{R}$ recovery rate (from both $I_C$ and $I_{SC2}$)
- $\nu$ death rate from $I_{C}$
- $\rho_i$'s: age dependent probabilities of becoming clinical; in order to reduce number of parameters, it is 
parametrized by a logistic transformation with parameters $x_0$ and $\phi$.

Finally, $C$ represents the contact matrix between age groups, with $N_j$ representing instead the number of people in each age group. 

Therefore, the equations defining the model are the following: 

![Equations](https://raw.githubusercontent.com/LoryPack/COVID19-epidemics-forecast-England/master/img/equations.png?token=AIT3WHHFZTPWTUS6IILOEXC6T4MOS)


# Inference scheme

We use Approximate Bayesian Computation as an inference scheme to fit the parameter values. This allows us to fix a prior 
range for the parameters, and to obtain an uncertainty range in the prediction. 

This inference scheme essentially works by looking for a value of the parameters which best approximates the observations.  


