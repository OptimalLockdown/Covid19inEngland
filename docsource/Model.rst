.. _Model:

Epidemic Model
==============================

age-structured :math:`SEI^4RD`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Presently, we are using a compartmental model, which splits whole of the UK population into  compartments representing different possible states (Susceptible (:math:`S`), Exposed (:math:`E`) but not infectious, asymptomatic and symptomatic Infected subclinical (:math:`I^{SC}`, split in :math:`I^{SC1}` and :math:`I^{SC2}`) not needing medical attention, Infected clinical needing medical attention (:math:`I^{C}`, split in :math:`I^{C1}` and :math:`I^{C2}`), Recovered (:math:`R`) and Deceased (:math:`D`)). Further each of the states are structured along 5 age groups: :math:`0-19, 20-39, 40-59, 60-79, 80+`, hence :math:`E_i` stands for the exposed population at the :math:`i`-th age group, and similarly for the other states.


.. content-tabs::

    .. tab-container:: tab1
        :title: Description
        

        Starting with the whole population being in the :math:`S` state (except for some individuals, who are seeding the infection), any susceptible individual becomes exposed (:math:`E`) with probability :math:`\beta` for each contact with an infected one. Next our model considers what is happening in the UK, where the patients are tested only when they have come to the hospital with symptoms. Afterwards, they are isolated and hence are not able to spread the infection. To reflect this scenario, we assume that from the exposed state and after some incubation period, all patients will become sub-clinical :math:`I^{SC}` in which they are infectious. After that some of them will recover (go to :math:`R`) and others will need clinical help (go to :math:`I^C`), reflected in a split of two categories: the ones directly recovering (:math:`I^{SC2}`) and the ones needing clinical help (:math:`I^{SC1}`). The split happens with an age-dependent probability :math:`\rho_i`. People in :math:`I^{SC1}` will go to hospital, therefore moving to the :math:`I^{C}` state and will be counted as COVID positive; similary as before, this state is split in two categories according to the final outcome: the ones in :math:`I^{C1}` will decease (:math:`D`) after some time, while the ones in :math:`I^{SC2}` will recover (:math:`R`). The split is again described by an age-dependent probability, which we denote as :math:`\rho'_i`. The dynamics can be visualized ad follows:

        .. image:: img/SEI3RD.png

        and is defined by the following ordinary differential equations (ODEs):
        
        :math:`\frac{dS_i}{dt} = - \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}, \ I_j^{SC} = I_j^{SC1} + I_j^{SC2}`

        :math:`\frac{dE_i}{dt} = \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}  - \kappa  E_i`

        :math:`\frac{dI^{SC1}_i}{dt} = \rho_i \kappa E_i - \gamma_{C}   I_i^{SC1}`

        :math:`\frac{dI^{SC2}_i}{dt} = (1-\rho_i) \kappa E_i - \gamma_{R}   I_i^{SC2}`

        :math:`\frac{dI^{C1}_i}{dt} =  \rho'_i \gamma_{C} I_i^{SC1}  -\nu I_i^{C1}`

        :math:`\frac{dI^{C2}_i}{dt} =  (1-\rho'_i) \gamma_{C} I_i^{SC1}  -\gamma_R I_i^{C2}`

        :math:`\frac{dR_i}{dt}  = \gamma_{R}   I_i^{C2} + \gamma_R I_i^{SC2}`

        :math:`\frac{dD_i}{dt}  =  \nu I_i^{C1}`.


        where :math:`C` is the contact matrix representing the frequency of contacts between different age groups as in `Prem et al. (2017) <https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005697>`_. Further we will consider the contact matrix to be composed of four different contributions, corresponding to contacts happening respectively in home, workplace, school and other locations:
        
        .. centered:: :math:`C=\alpha_{home}C_{home}+\alpha_{work}C_{work}+\alpha_{school}C_{school}+\alpha_{other}C_{other}`
        
        We reflect effects of lockdown strategies through the values of :math:`\alpha` (:math:`\alpha_{school}=0` means all schools are closed). Presently, we choose the values of different :math:`\alpha` on different days based on `Google mobility data <https://www.google.com/covid19/mobility/>`_ , except for :math:`\alpha_{school}`, which we fix to 0.1 after the start of the lockdown (as in the UK children of essential workers can still access school).

    .. tab-container:: tab2
        :title: Parameters
        
        The parameters of the considered model are following:
                - :math:`\beta` probability of an :math:`S`-:math:`I^{SC}` contact to result in the S individual catching the infection
                - :math:`\kappa = 1- \exp(-1/d_L)` transition rate of exposed individual becoming infectious, with :math:`d_L` the average number of days in this latent state
                - :math:`\gamma_{C} = 1- \exp(-1/d_C)` transition rate of going from from :math:`I^{SC1}` to :math:`I^C`, with :math:`d_C` the average number of days it takes to undergo this transition
                - :math:`\gamma_{R} = 1- \exp(-1/d_R)` recovery rate (from both :math:`I^{C2}` and :math:`I^{SC2}`), with :math:`d_C` the average number of days it takes to recover (from these two states)
                - :math:`\nu = 1- \exp(-1/d_D)` death rate from :math:`I^{C1}`, with :math:`d_D` the average number of days before death occurs after being diagnosed (which mostly corresponds to reaching the hospital)
                - :math:`\rho_i`'s: age dependent probabilities of going to :math:`I^C` instead of directly recovering from the :math:`I^{SC}` state; in order to reduce number of parameters, it is parametrized by a logistic transformation with parameters :math:`x_0` and :math:`\phi`, as explained in the following.
                - :math:`\rho'_i`'s: age dependent probabilities of death after becoming clinical; a logistic transformation with parameters :math:`x_0'` and :math:`\phi'` is used.

                Moreover, initial conditions for the dynamics are needed; :math:`E_{in}`: the initial number of exposed people; we distribute this number of initially exposed people over the age groups in order to approximately reflect the age distribution of incoming flight passengers to the UK (check for instance `here <https://www.statista.com/statistics/304641/age-distribution-of-air-passengers-by-airport-uk/>`_) as we are assuming the disease was brought to the UK from abroad; this results therefore in using the following rates in the age groups (from youngest to oldest): 0.1, 0.4, 0.35, 0.1, 0.05.

        **Logistic transformation for age-specific transition probabilities:**
        In order to reduce the number of parameters needed to describe :math:`\rho_i` for the five age groups to two, we use a logistic transformation:

        :math:`\rho_i = (1 + \exp(-\omega(x_i-x_0))^{-1}, \quad \omega = 4 \tan(\phi)`,

        where :math:`x_i` is the index of the age group (from 0 to 4), :math:`x_0` indicates where the midpoint of the curve is reached, and :math:`\phi \in [0, \pi/2]` represents the slope of the tangent line in the midpoint of the curve.

        The same transformation is also done for :math:`\rho'_i`; note that this assumes that both probabilities increase for older age groups, but this is motivated by the reality.

        **Inference**

        The values of these parameters for our model is not known, hence we learn them based on :ref:`publicly available dataset <Data>` using :ref:`approximate Bayesian computation <Inference>`.


        