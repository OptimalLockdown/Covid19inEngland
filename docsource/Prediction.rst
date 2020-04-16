.. _Prediction:

Predictions for the UK (updated daily)
================================================

Add predictions, results and interpretation.



Multistage model, with which we predict the number of deceased and people who will tested clinical in England.

**Note**: the predictions assume that the conditions in England remain the following, ie:
 - Tested people are composed mostly of the ones which are admitted into hospital
 - Restrictive measures as of the 9th April will be kept in place for the prediction horizon
 - Once people are tested positive and admitted into hospital, they are isolated, not being able anymore of transmitting the infection.


Total number of confirmed cases
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We report here a prediction for the total number of confirmed cases in the next 30 days. This is the sum over all age groups

IMAGE







Deceased according to age group
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Next, we forecast the number of deceased for each of the 5 considered age groups.

IMAGES





Estimates of age-specific transition probabilities
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Two different age-specific probabilities are presenti in our model: first, the probability of needing clinical assistance, which we denote by :math:`\rho`, and then the probability of deceasing, conditioned on the fact that you need clinical assistance, which we denote as :math:`\rho'`.

We can estimate these age-dependent transition probabilities.




Parameter estimation: :math:`R_0` evolution during the epidemics
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

From our estimate of the parameters, we can estimate :math:`R_0`, ie the basic reproduction number, for this pandemic.














For more details please check :ref:`Epidemic model <Model>`, :ref:`approximate Bayesian computation <Inference>` and :ref:`Data sources <Data>`.