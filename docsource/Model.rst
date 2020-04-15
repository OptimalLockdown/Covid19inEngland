.. _Model:

Epidemic Models
==============================


SEIRD Model
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

        We are using a compartmental model, which splits the population into different _compartments_, representing different possible states (Susceptible, Exposed, Infected, Recovered and Deceased). The evolution over time is represented by some equations which assume the population is well mixed. 


.. content-tabs::

    .. tab-container:: tab1
        :title: Description
        
        The model we consider is inspired by what is happening in UK: in the first phase of the emergency, the majority of diagnosed people 
        are admitted into hospital. We assume that thereafter, they are 
         isolated, meaning that they are not able to spread the infection anymore. Therefore, we assume that after the exposed state, all patients 
        spend some time in the :math:`I^{SC}` one, and after that some of them will go directly to :math:`R`, and some to :math:`I^C`. From :math:`I^C`, 
        they can either decease (going into the :math:`D` state) or recover (to :math:`R`). Essentially, this means that the subclinical state is splitted in two.
        
        We consider 5 different age groups, and 7 different states; the transition pattern can be seen in the following image: 
        
        .. image:: img/SEIRD.png

    .. tab-container:: tab2
        :title: Parameters
        
        The parameters are therefore the following: 
        
        - :math:`\beta` transmission rate
        - :math:`\kappa` daily probability of exposed individual becoming infectious
        - :math:`\gamma_{C}` rate of going from from :math:`I_{SC1}` tp :math:`I_C`
        - :math:`\gamma_{R}` recovery rate (from both :math:`I_C` and :math:`I_{SC2}`)
        - :math:`\nu` death rate from :math:`I_{C}`
        - :math:`\rho_i`'s: age dependent probabilities of becoming clinical; in order to reduce number of parameters, it is 
        parametrized by a logistic transformation with parameters :math:`x_0` and :math:`\phi`.
        
        Finally, :math:`C` represents the contact matrix between age groups, with :math:`N_j` representing instead the number of people in each age group. 

    .. tab-container:: tab3
        :title: Equations
        
        Therefore, the equations defining the model are the following: 


        .. image:: img/equations.png
        
        
Metapopulation SEIRD Models
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. content-tabs::

    .. tab-container:: tab1
        :title: Description

        aaaaa


    .. tab-container:: tab2
        :title: Parameters

        bbbb

    .. tab-container:: tab3
        :title: Equations
        
        ccccc
