## SEIRD model: 

We consider 5 different age groups, and 7 different states; the transition pattern can be seen in the following image: 

![SEIRD model](img/SEIRD.pdf)


The model we use is the following: 
{% raw %}  
$$\frac{dS_i}{dt} = - \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}, \quad I_j^{SC} = I_j^{SC1} + I_j^{SC2}$$
{% endraw %}

{% raw %}  
\begin{align*}
\frac{dS_i}{dt} & = - \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}, \quad I_j^{SC} = I_j^{SC1} + I_j^{SC2}\\[8pt]
\frac{dE_i}{dt} & = \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}  - \kappa  E_i \\[8pt]
\frac{dI^{SC1}_i}{dt} & = \rho_i \kappa E_i - \gamma_{C}   I_i^{SC1} \\[8pt]
\frac{dI^{SC2}_i}{dt} & = (1-\rho_i) \kappa E_i - \gamma_{R}   I_i^{SC2} \\[8pt]
\frac{dI^C_i}{dt} & =  \gamma_{C} I_i^{SC1} - \gamma_R   I_i^C -\nu I_i^C\\[8pt]
\frac{dR_i}{dt} & = \gamma_{R}   I_i^{SC} + \gamma_R I_i^{SC2}  \\[8pt]
\frac{dD_i}{dt} & =  \nu I_i^C.
\end{align*}
{% endraw %}