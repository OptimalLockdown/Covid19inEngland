.. _Prediction:

Predictions for the UK (Updated on 11th April)
================================================



Number of infected
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Prediction of the total number of infected people who needed hospitalization and the number of hospital beds needed for COVID-19 patients per day. 

.. content-tabs::

    .. tab-container:: tab1
        :title: Infected & Hospitalized

        .. image:: img/cumulative_confirmed.png
        True data matches the median prediction very well.

    .. tab-container:: tab2
        :title: Hospital beds needed per day

        .. image:: img/cumulative_confirmed.png
        True data matches the median prediction very well.

Number of deaths in hospital
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Prediction of the number of deaths in hospital per day and total number of deaths.

.. content-tabs::

    .. tab-container:: tab1
        :title: Deaths per day 

        .. image:: img/total_deaths_per_day.png

        DPD_image (Add image and a line about, true number, projected number and uncertainty)

    .. tab-container:: tab2
        :title: Total deaths

        .. image:: img/total_deaths.png

        TD_image (Add image and a line about, true number, projected number and uncertainty)


Deaths in hospital in each age group
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Prediction of total number of deaths in the 5 age groups: :math:`<20, 20-39, 40-59, 60-79, 80+`.

.. content-tabs::

    .. tab-container:: tab1
        :title:  <20
        
        .. image:: img/total_deaths_per_day.png

    .. tab-container:: tab2
        :title:  20-39
        
        .. image:: img/total_deaths_per_day.png


    .. tab-container:: tab3
        :title:  40-59
        
        .. image:: img/total_deaths_per_day.png


    .. tab-container:: tab4
        :title:  60-79
        
        .. image:: img/total_deaths_per_day.png


    .. tab-container:: tab5
        :title:  80+
        
        .. image:: img/total_deaths_per_day.png
        

Age-specific probabilities
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From our model, we estimate two age-dependent probabilities of (a) needing hospitalization when infected and (b) death.

.. content-tabs::

    .. tab-container:: tab1
        :title: Need of hospitalization 

        .. image:: img/prob_hospitalisation.png
        DPD_image (Add image and a line about, true number, projected number and uncertainty)

    .. tab-container:: tab2
        :title: Death

        .. image:: img/prob_deceasing.png

        TD_image (Add image and a line about, true number, projected number and uncertainty)

.. Evolution of :math:`R_0` during the pandemic
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    From our estimate of the parameters, we can estimate :math:`R_0`, ie the basic reproduction number, for this pandemic.


**Assumptions**: Our predictions are done under the assumption that the conditions in the UK remain the following, ie:
 - Tested people are composed mostly of the ones which are admitted into hospital, or at least they will isolate themselves when tested positive; this is reasonable according to what said on `this government webpage <https://www.gov.uk/guidance/coronavirus-covid-19-information-for-the-public>`_ which reports that, as of the 15th of April, 390,731 out of 417,649 tests were done on people with a medical need and the most essential workers and their families.
 - Restrictive measures as of the 11th April will be kept in place for the prediction horizon; the government announced that such restrictive measures will be kept in place until the DATE, PUT LINK!
 - Once people are tested positive and admitted into hospital, they are isolated, not being able anymore of transmitting the infection.

For more details please check :ref:`Epidemic model <Model>`, :ref:`approximate Bayesian computation <Inference>` and :ref:`Data sources <Data>`.