---
layout: default
title: SEIRD model and inference scheme
usemathjax: true
---

## SEIRD model: 

We consider 5 different age groups, and 7 different states; the transition pattern can be seen in the following image: 

![SEIRD model](https://raw.githubusercontent.com/LoryPack/COVID19-epidemics-forecast-England/master/img/SEIRD.png?token=AIT3WHE77BMEFWECRDZO36K6T33XW)

The model we use is the following: 

$$
\begin{align*}
\frac{dS_i}{dt} &= - \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}, \quad I_j^{SC} = I_j^{SC1} + I_j^{SC2} \\
\frac{dE_i}{dt} &= \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}  - \kappa  E_i \\   
\frac{dI^{SC1}_i}{dt} &= \rho_i \kappa E_i - \gamma_{C}   I_i^{SC1} \\
\frac{dI^{SC2}_i}{dt} &= (1-\rho_i) \kappa E_i - \gamma_{R}   I_i^{SC2} \\
\frac{dI^C_i}{dt} &=  \gamma_{C} I_i^{SC1} - \gamma_R   I_i^C -\nu I_i^C\\
\frac{dR_i}{dt} &= \gamma_{R}   I_i^{SC} + \gamma_R I_i^{SC2}  \\
\frac{dD_i}{dt} &=  \nu I_i^C.
\end{align*}
$$
