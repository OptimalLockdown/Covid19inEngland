.. _Prediction:

Predictions for the UK (updated daily)
================================================

Number of infected
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Prediction of the total number of infected people and the total number of infected people who needed hospitalization. 

.. content-tabs::

    .. tab-container:: tab1
        :title: Total infected
        
        DPD_image (Add image and a line about, true number, projected number and uncertainty)

    .. tab-container:: tab2
        :title: Infected & Hospitalized
        
        TD_image (Add image and a line about, true number, projected number and uncertainty)


Number of deaths
~~~~~~~~~~~~~~~~
Prediction of the number of death per day, total number of deaths and deaths in the 5 age groups: :math:`<20, 20-40, 40-60, 60-80, 80>`.

.. content-tabs::

    .. tab-container:: tab1
        :title: Deaths per day 
        
        DPD_image (Add image and a line about, true number, projected number and uncertainty)

    .. tab-container:: tab2
        :title: Total deaths
        
        TD_image (Add image and a line about, true number, projected number and uncertainty)

    .. tab-container:: tab3
        :title: Deaths per age-groups
        
        DPAG_image (Add image and a line about, true number, projected number and uncertainty)


Age-specific probabilities
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From our model, we estimate two age-dependent probabilities of (a) needing hospitalization when infected and (b) death.

.. content-tabs::

    .. tab-container:: tab1
        :title: Need of hospitalization 
        
        DPD_image (Add image and a line about, true number, projected number and uncertainty)

    .. tab-container:: tab2
        :title: Death
        
        TD_image (Add image and a line about, true number, projected number and uncertainty)


Evolution of :math:`R_0` during the pandemic
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From our estimate of the parameters, we can estimate :math:`R_0`, ie the basic reproduction number, for this pandemic.


**Assumptions**: Our predictions are done under the assumption that the conditions in the UK remain the following, ie:
 - Tested people are composed mostly of the ones which are admitted into hospital
 - Restrictive measures as of the 9th April will be kept in place for the prediction horizon
 - Once people are tested positive and admitted into hospital, they are isolated, not being able anymore of transmitting the infection.

For more details please check :ref:`Epidemic model <Model>`, :ref:`approximate Bayesian computation <Inference>` and :ref:`Data sources <Data>`.