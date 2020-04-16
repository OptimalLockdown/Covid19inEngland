.. _Model:

Epidemic Model
==============================

age-structured :math:`SEI^3RD`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Presently, we are using a compartmental model, which splits whole of the UK population into 7 compartments representing different possible states (Susceptible (:math:`S`), Exposed (:math:`E`), asymptomatic and symptomatic Infected subclinical (:math:`I_{SC1}` and :math:`I_{SC2}`) not needing medical attention, Infected clinical needing medical attention (:math:`I_{C}`), Recovered (:math:`R`) and Deceased (:math:`D`)). Further each of the states are structured along 5 age groups: :math:`<20, 20-40, 40-60, 60-80, 80>`, hence :math:`E_i` stands for the exposed population at the :math:`i`-th age group.


.. content-tabs::

    .. tab-container:: tab1
        :title: Description
        
        The model we consider is inspired by what is happening in UK, where the patients are tested only when they have come to the hospital with symptoms. Afterwards, they are isolated and hence are not able to spread the infection. To reflect this scenario, we assume that after the exposed state, all patients will be sub-clinical :math:`I^{SC}` for a while, and after that some of them will recover (go to :math:`R`) and others will need clinical help (go to :math:`I^C`).

        More in detail, the model works as follows: the population starts in the :math:`S` state (except for some individuals, who are seeding the infection). Then, once an individual in :math:`S` gets in contact with an infected one, it will go to the exposed state :math:`E`; this step happens with probability :math:`\beta` for each contact; note that in this state individuals are not yet infectious. After some incubation time, the individuals become Infected subclinical (:math:`I^{SC}`), in which they are capable of infecting other people; even if all people in this compartment act equally, we split the population in two categories: the ones which will directly recover (:math:`I_{SC2}`) and the ones that instead will need clinical help (:math:`I_{SC1}`). The split happens with an age-dependent probability :math:`\rho_i`.
        Once in the :math:`I_{SC2}` state, people will recover after some time, and their infection is not recorder by the authorities. Instead, people in :math:`I_{SC1}` will go to hospital, therefore moving to the :math:`I_{C}` state, and they are registered. From this state, they will either recover :math:`R` or decease :math:`D`; we model this transition with two independent processes with a certain rate.

        The transmission dynamics can be visualized ad follows:

        .. image:: img/SEIRD.png

        and is defined by the following ordinary differential equations (ODEs):
        
        :math:`\frac{dS_i}{dt} = - \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}, \ I_j^{SC} = I_j^{SC1} + I_j^{SC2}`

        :math:`\frac{dE_i}{dt} = \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}  - \kappa  E_i`

        :math:`\frac{dI^{SC1}_i}{dt} = \rho_i \kappa E_i - \gamma_{C}   I_i^{SC1}`

        :math:`\frac{dI^{SC2}_i}{dt} = (1-\rho_i) \kappa E_i - \gamma_{R}   I_i^{SC2}`

        :math:`\frac{dI^C_i}{dt} =  \gamma_{C} I_i^{SC1} - \gamma_R   I_i^C -\nu I_i^C`

        :math:`\frac{dR_i}{dt} = \gamma_{R}   I_i^{C} + \gamma_R I_i^{SC2}`

        :math:`\frac{dD_i}{dt} =  \nu I_i^C`


    where :math:`C` is the contact matrix representing the frequency of contacts between different age groups as in `Prem et al. (2017) <https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005697>`_.

        Further we will consider the contact matrix to be composed of four different contributions, corresponding to contact happening respectively in home, workplace, school and other locations:
        
        .. centered:: :math:`C=\alpha_{home}C_{home}+\alpha_{work}C_{work}+\alpha_{school}C_{school}+\alpha_{other}C_{other}`
        
        We reflect effects of lockdown strategies through the values of :math:`\alpha` (:math:`\alpha_{school}=0` means schools are closed). Presently, we choose the values of different :math:`\alpha` on different days based on `Google mobility data <https://www.google.com/covid19/mobility/>`_ , except for :math:`\alpha_{school}`, which we fix to 0.1 after the start of the lockdown (as in the UK children of essential workers can still access school).

    .. tab-container:: tab2
        :title: Parameters
        
        The parameters of the considered model are following:
                - :math:`\beta` transmission rate
                - :math:`\kappa = 1- \exp(-1/d_L)` daily probability of exposed individual becoming infectious, with :math:`d_L` the average number of days in this latent state
                - :math:`\gamma_{C} = 1- \exp(-1/d_C)` rate of going from from :math:`I_{SC1}` tp :math:`I_C`, with :math:`d_C` the average number of days it takes to undergo this transition
                - :math:`\gamma_{R} = 1- \exp(-1/d_R)` recovery rate (from both :math:`I_C` and :math:`I_{SC2}`), with :math:`d_C` the average number of days it takes to recover (from these two states)
                - :math:`\nu = 1- \exp(-1/d_D)` death rate from :math:`I_{C}`, with :math:`d_L` the average number of days before death occurs after reaching the hospital (being diagnosed)
                - :math:`\rho_i`'s: age dependent probabilities of becoming clinical; in order to reduce number of parameters, it is parametrized by a logistic transformation with parameters :math:`x_0` and :math:`\phi`, as explained in .....

                Moreover, initial conditions for the dynamics are needed; :math:`E_{in}`: the initial number of exposed people (which is....



        The values of these parameters for our model is not known, hence we learn them based on :ref:`publicly available dataset <Data>` using :ref:`approximate Bayesian computation <Inference>`.


        