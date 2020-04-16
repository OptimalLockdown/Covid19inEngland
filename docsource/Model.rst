.. _Model:

Epidemic Model
==============================

age-structured :math:`SEI^3RD`
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Presently, we are using a compartmental model, which splits whole of the UK population into 7 compartments representing different possible states (Susceptible (:math:`S`), Exposed (:math:`E`), asymptomatic and symptomatic Infected subclinical (:math:`I_{SC1}` and :math:`I_{SC2}`) not needing medical attention, Infected clinical needing medical attention (:math:`I_{C}`), Recovered (:math:`R`) and Deceased (:math:`D`)). Further each of the states are structured along 5 age groups: :math:`<20, 20-40, 40-60, 60-80, 80>`, hence :math:`E_i` stands for the exposed population at the :math:`i`-th age group.


.. content-tabs::

    .. tab-container:: tab1
        :title: Description
        
        The model we consider is inspired by what is happening in UK, where the patients are tested only when they have come to the hospital with symptoms. Afterwards, they are isolated and hence are not able to spread the infection. To reflect this scenario, we assume that after the exposed state, all patients will be sub-clinical :math:`I^{SC}` for a while, and after that some of them will recover (go to :math:`R`) and others will need clinical help (go to :math:`I^C`). Essentially, this means that the subclinical state is splitted into two compartments :math:`I_{SC1}` and :math:`I_{SC2}`. From :math:`I^C`, they can either decease (going into the :math:`D` state) or recover (to :math:`R`). The transmission dynamics can be visualized in the following image, 
        
        .. image:: img/SEIRD.png

        and is defined by the following ordinary differential equations (ODEs) where :math:`C` is the contact matrix representing the frequency of contacts between different age groups as in `Prem et al. (2017) <https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005697>`_: 
        
        :math:`\frac{dS_i}{dt} = - \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}, \ I_j^{SC} = I_j^{SC1} + I_j^{SC2}`

        :math:`\frac{dE_i}{dt} = \beta {S_i} \sum_j C_{i,j} \frac{I^{SC}_j}{N_j}  - \kappa  E_i`

        :math:`\frac{dI^{SC1}_i}{dt} = \rho_i \kappa E_i - \gamma_{C}   I_i^{SC1}`

        :math:`\frac{dI^{SC2}_i}{dt} = (1-\rho_i) \kappa E_i - \gamma_{R}   I_i^{SC2}`

        :math:`\frac{dI^C_i}{dt} =  \gamma_{C} I_i^{SC1} - \gamma_R   I_i^C -\nu I_i^C`

        :math:`\frac{dR_i}{dt} = \gamma_{R}   I_i^{SC} + \gamma_R I_i^{SC2}`

        :math:`\frac{dD_i}{dt} =  \nu I_i^C`

        
        Further we will consider: 
        
        .. centered:: :math:`C=\alpha_{home}C_{home}+\alpha_{work}C_{work}+\alpha_{school}C_{school}+\alpha_{other}C_{other}`
        
        where :math:`C_{work}` is the contact matrix at the workplace and the values of :math:`0 \leq \alpha \leq 1`. We can reflect effects of lockdown strategies through the values of :math:`\alpha` (:math:`\alpha_{school}=0` means schools are closed). Presently, we choose the values of different :math:`\alpha` on different days based on `Google mobility data <https://www.google.com/covid19/mobility/>`_ .

    .. tab-container:: tab2
        :title: Parameters
        
        The parameters of the considered model are following: 
        
        - :math:`\beta` transmission rate
        - :math:`\kappa` daily probability of exposed individual becoming infectious
        - :math:`\gamma_{C}` rate of going from from :math:`I_{SC1}` tp :math:`I_C`
        - :math:`\gamma_{R}` recovery rate (from both :math:`I_C` and :math:`I_{SC2}`)
        - :math:`\nu` death rate from :math:`I_{C}`
        - :math:`\rho_i`'s: age dependent probabilities of becoming clinical; in order to reduce number of parameters, it is parametrized by a logistic transformation with parameters :math:`x_0` and :math:`\phi`.
        