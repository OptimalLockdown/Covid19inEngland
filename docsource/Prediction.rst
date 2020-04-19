.. _Prediction:

Predictions for England (Updated on 11th April)
================================================


Number of infected
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Prediction of the cumulative total number of infected people who are diagnosed (most of them needing hospitalisation), and the daily number of new diagnoses.
Shaded area indicates :ref:`uncertainty <3. How should I interpret the uncertainty predicted by this model?>`, specifically 95% High Posterior Density (HPD) region. Dotted vertical line denotes the day up to which the observed data was used for fitting the model (11th April); after we've done the fit, data until the 13th became available, so we plot those as well, in order to check how our predictions match reality.

.. content-tabs::

    .. tab-container:: tab1
        :title: Infected & Hospitalized

        .. image:: img/cumulative_confirmed.png
        Data is referred to the day the specimen was collected, not to the reporting date.

    .. tab-container:: tab2
        :title: Daily new diagnoses

        .. image:: img/daily_confirmed.png

    .. tab-container:: tab3
        :title: Active infected

        .. image:: img/total_number_infected.png

        We estimate the number of active infected people (ie people who are capable of spreading the infection, as they are in the :math:`I^{SC}` state) for each day of the model. Note that the uncertainty here is very large as we do not have real data on this; note also that the y axis here has to be multiplied by :math:`10^7`.

Number of deaths in hospital
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Prediction of the number of deaths in hospital per day and total number of deaths. Note that deaths are considered by the date they actually happened, not by reporting date; this is why we are not able to use data more recent than 5 days ago, as reporting takes some time.
Shaded area indicates :ref:`uncertainty <3. How should I interpret the uncertainty predicted by this model?>`, specifically 95% High Posterior Density (HPD) region.

.. content-tabs::

    .. tab-container:: tab1
        :title: Deaths per day 

        .. image:: img/total_deaths_per_day.png

        According to this model, we are right now close at the peak of number of deaths per day; note that these are considered by the date the death actually happened, not by reporting date; this is why we are not able to use data more recent than 5 days ago, as reporting takes some time.


    .. tab-container:: tab2
        :title: Total deaths

        .. image:: img/total_deaths.png


Deaths in hospital in each age group
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Prediction of total number of deaths in the 5 age groups: :math:`0-19,   20-39, 40-59, 60-79, 80+`, versus the day the deaths actually happened.
Shaded area indicates :ref:`uncertainty <3. How should I interpret the uncertainty predicted by this model?>`, specifically 95% High Posterior Density (HPD) region.

.. content-tabs::

    .. tab-container:: tab1
        :title:  0-19
        
        .. image:: img/total_deaths_age_group_0.png

    .. tab-container:: tab2
        :title:  20-39
        
        .. image:: img/total_deaths_age_group_1.png


    .. tab-container:: tab3
        :title:  40-59
        
        .. image:: img/total_deaths_age_group_2.png


    .. tab-container:: tab4
        :title:  60-79
        
        .. image:: img/total_deaths_age_group_3.png


    .. tab-container:: tab5
        :title:  80+
        
        .. image:: img/total_deaths_age_group_4.png
        

Age-specific probabilities
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From our model, we estimate two age-dependent probabilities of (a) needing hospitalization when infected and (b) death when confirmed positive; we remark again that diagnosis happen in most part when people need clinical care in hospital.

.. content-tabs::

    .. tab-container:: tab1
        :title: Need of hospitalization 

        .. image:: img/prob_hospitalisation.png
        The horizontal line is the median prediction, while the bands width indicates the probability distribution for each value.

    .. tab-container:: tab2
        :title: Death

        .. image:: img/prob_deceasing.png

        The horizontal line is the median prediction, while the bands width indicates the probability distribution for each value.

.. Evolution of :math:`R_0` during the pandemic
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    From our estimate of the parameters, we can estimate :math:`R_0`, ie the basic reproduction number, for this pandemic.


**Assumptions**: Our predictions are done under the assumption that the conditions in the UK remain the following, ie:
 - Tested people are composed mostly of the ones which are admitted into hospital, or at least they will isolate themselves when tested positive; this is reasonable according to what said on `this government webpage <https://www.gov.uk/guidance/coronavirus-covid-19-information-for-the-public>`_ which reports that, as of the 15th of April, 390,731 out of 417,649 tests were done on people with a medical need and the most essential workers and their families.
 - Restrictive measures as of the 11th April will be kept in place for the prediction horizon; the government `announced <https://www.bbc.com/news/uk-52313715>`_ that such restrictive measures will be kept in place for at least three weeks starting from the 16th of April.
 - Once people are tested positive and admitted into hospital, they are isolated, not being able anymore of transmitting the infection.
- Conditions about hospital use remain more or less constants; specifically, we do not explicitly model the occupation of hospital beds and ICUs, which, if saturated, can have a large impact on the death rate of the disease.

Moreover, a key assumption of this model is that a person cannot catch the disease twice; this is still matter of debate; however, even if this were the case, we expect it not to change too much the dynamics of the epidemics in a first phase, in which a great part of the population is still susceptible anyway. It would of course matter a lot in the long time dynamics.

For more details please check :ref:`Epidemic model <Model>`, :ref:`approximate Bayesian computation <Inference>` and :ref:`Data sources <Data>`.