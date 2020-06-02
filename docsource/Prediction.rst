.. _Prediction:

Inference results for England (Updated on 23rd May)
===================================================


Hospitalized people
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Predicted number of hospitalized people vs. actual number.

        .. image:: img/daily_Ic_total.png
        .. centered:: (Orange shaded area indicates :ref:`uncertainty <4. What do we mean by uncertainty in this model?>`)

The dotted vertical line denotes the observation horizon, the day up to which the observed data was used for fitting the model (23rd May).

Number of deaths in hospital
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Prediction of the number of deaths in hospital per day and total number of deaths. 

.. content-tabs::

    .. tab-container:: tab1
        :title: Deaths per day 

        .. image:: img/daily_deceased_total.png
        .. centered:: (Orange shaded area indicates :ref:`uncertainty <4. What do we mean by uncertainty in this model?>`)


    .. tab-container:: tab2
        :title: Total deaths

        .. image:: img/cumulative_deceased_total.png
        .. centered:: (Orange shaded area indicates :ref:`uncertainty <4. What do we mean by uncertainty in this model?>`)

The dotted vertical line denotes the observation horizon, the day up to which the observed data was used for fitting the model (23rd May). Note that deaths are considered by the date they actually happened, not by reporting date.

Deaths in hospital in each age group
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Prediction of total number of deaths in the 5 age groups: :math:`0-19,   20-39, 40-59, 60-79, 80+`, versus the day the deaths actually happened.

.. content-tabs::

    .. tab-container:: tab1
        :title:  0-19
        
        .. image:: img/daily_deaths_age_group_1.png
        .. centered:: (Orange shaded area indicates :ref:`uncertainty <4. What do we mean by uncertainty in this model?>`)

    .. tab-container:: tab2
        :title:  20-39
        
        .. image:: img/daily_deaths_age_group_2.png
        .. centered:: (Orange shaded area indicates :ref:`uncertainty <4. What do we mean by uncertainty in this model?>`)

    .. tab-container:: tab3
        :title:  40-59
        
        .. image:: img/daily_deaths_age_group_3.png


    .. tab-container:: tab4
        :title:  60-79
        
        .. image:: img/daily_deaths_age_group_4.png
        .. centered:: (Orange shaded area indicates :ref:`uncertainty <4. What do we mean by uncertainty in this model?>`)

    .. tab-container:: tab5
        :title:  80+
        
        .. image:: img/daily_deaths_age_group_5.png
        .. centered:: (Orange shaded area indicates :ref:`uncertainty <4. What do we mean by uncertainty in this model?>`)

Age-specific probabilities
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From our model, we estimate two age-dependent probabilities of (a) needing hospitalization when infected and (b) death when hospitalized.

.. content-tabs::

    .. tab-container:: tab1
        :title: Hospitalization

        .. image:: img/violinplot_rho.png

        The horizontal line is the median prediction, while the bands width indicates the probability distribution for each value.


    .. tab-container:: tab2
        :title: Death

        .. image:: img/violinplot_rho_prime.png

        The horizontal line is the median prediction, while the bands width indicates the probability distribution for each value.

.. Evolution of :math:`R_0` during the pandemic
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    From our estimate of the parameters, we can estimate :math:`R_0`, ie the basic reproduction number, for this pandemic.

.. 
    **Main Conclusions**: (Last updated on 20 April 2020.)
    - According to our model, we are currently (April 20) crossing the peak of the number of COVID-19 deaths per day in hospitals in England. However, sadly, a large number of people will still die in the next seven weeks. 
    - According to our model (as of April 20), assuming the current lockdown measures are extended until early June and the population continues to comply with them, the number of daily COVID-19 deaths in hospitals in England will reduce to nil by the first week of June. 
    - As has been concluded by other studies, we also found that older people had a significantly higher probability of needing hospitalization and of dying compared to younger people. 
    
**Assumptions**: Our predictions are done under the assumption that the conditions in the UK remain the following, ie:

..
    - Tested people are composed mostly of the ones which are admitted into hospital, or at least they will isolate themselves when tested positive; this is reasonable according to what said on `this government webpage <https://www.gov.uk/guidance/coronavirus-covid-19-information-for-the-public>`_ which reports that, as of the 15th of April, 390,731 out of 417,649 tests were done in the "pillar 1" category, which includes mostly people with a medical need in hospitals and, whenever lab capacity allows that, the most critical NHS workers, as further detailed `here <https://www.gov.uk/government/publications/coronavirus-covid-19-scaling-up-testing-programmes/coronavirus-covid-19-scaling-up-our-testing-programmes#scaling-up-our-testing-programmes>`_


- Restrictive measures as of the 23rd May will be kept in place for the prediction horizon.

- Once people are tested positive and admitted into hospital, they are isolated, not being able anymore of transmitting the infection.

- Conditions about hospital use remain more or less constants; specifically, we do not explicitly model the occupation of hospital beds and ICUs, which, if saturated, can have a large impact on the death rate of the disease.

- Moreover, a key assumption of this model is that a person cannot catch the disease twice; this is still matter of debate; however, even if this were the case, we expect it not to change too much the dynamics of the epidemics in a first phase, in which a great part of the population is still susceptible anyway. It would of course matter a lot in the long time dynamics.

For more details please check :ref:`Epidemic model <Model>`, :ref:`approximate Bayesian computation <Inference>` and :ref:`Data sources <Data>`.