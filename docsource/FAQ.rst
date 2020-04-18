.. _FAQ:

Questions and Answers (for the public and media)
=================================================

.. TODO: add discussion on data-driven fitting wrt parameters determined by clinician knowledge, and fact that parameters that better fit a model are not the ones that are actually the true physical parameters with that physical meaning. However, possibilitiy of leveraging experts adive (through priors) and data-driven procedures.


1. What is this project?
~~~~~~~~~~~~~~~~~~~~~~~~


This project presently focuses on developing cutting-edge epidemic models tailored to the UK population, calibrating them with approximate Bayesian computation (ABC) using data from the spread of COVID-19 in the UK provided by Public Health England (PHE), the National Health Service (NHS) and the Office for National Statistics (ONS) rather than using global estimates of parameters of transmission dynamics. We also integrate `Google mobility data <https://www.google.com/covid19/mobility/>`_ in our model to reflect the affects of the lockdown on the UK population. Lorenzo Pacchiardi of Department of statistics, University of Oxford  and `Dr. Ritabrata Dutta of Department of statistics, University of Warwick <https://warwick.ac.uk/fac/sci/statistics/staff/academic-research/dutta/>`_ are presently working on improving the epidemic model by integrating data about commuting patterns of UK citizens constructed from the 2011 census data.

Further, `Dr. Susana Gomes of Department of mathematics, University of Warwick <https://warwick.ac.uk/fac/sci/maths/people/staff/gomes/>`_ and `Dr. Dante Kalise of School of Mathematical Sciences, University of Nottingham <https://sites.google.com/view/dkalise>`_ are working on using these models with control theory-based techniques to design an optimal strategy of how to impose a lock-down (e.g., what commuting routes to allow, what retail to close, etc.) and exit this lock-down when the time comes (what and when to reopen), responding daily to the data from PHE, NHS and ONS. 

2. How does this model differ from others that predict the spread of Covid-19?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The model we considered is a *compartmental* model, meaning one where the population (of England, in our case) is divided in compartments with different features. The population is assumed to be well-mixed, ie each person has the same probability to meet with any other person; see :ref:`here <4. What assumptions have been made in this model?>` for further discussion on what does this assumption mean. The evolution of the number of people in each compartment over time is described by some :ref:`equations <Model>` (ODEs).

This approach is different from so-called *individual-based models*, which aim to describe the action of each distinct individual but is harder to handle and more computationally intensive, being therefore more suited for the study of smaller size populations; an example of such kind of models in action can be seen `here <https://korona.kausal.tech/sim/en>`_. Some other models, for instance `this one by the Institute for Health Metrics and Evaluation (IHME) <https://covid19.healthdata.org/united-kingdom>`_  use instead curve-fitting approaches, by fitting some complex nonlinear mixed-effects model to the available data.

Another main difference is the :ref:`fitting procedure which we used <Likelihood-free inference>`: based on Bayesian statistics, we are able to leverage expertise about the parameters (by defining prior probabilities on them) but at the same time choosing the final value of them based on data. Moreover, the use of `ABCpy <https://github.com/eth-cscs/abcpy>`_ library allows us to perform efficient inference exploiting High Performance Computing, even in the present case of a model in which no direct inference procedure is possible.

Of course, we are happy to hear any comments or suggestions about improvements to the model; please see :ref:`here <6. How can I get in touch with the researchers behind this study?>` for contact informations.

DON'T KNOW ABOUT UK MODEL!

..  Refer to and link e.g. IHME model and explain very shortly the difference. Refer to and link article about model used by UK government, that it is not public, etc.
..  Possibly mention that you are interested in other models, and people can get in touch with you if they know of some?


3. How should I interpret the uncertainty predicted by this model?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

What we get from the inference scheme applied to our model is not a pointwise estimate of the parameters, but a probability distribution of them (in a Bayesian way), which reflect some sort of uncertainty on the model parameters.

This uncertainty can be thought of as arising from two different things:

1. It may be the case that the reality cannot be described perfectly by a realization of our (deterministic) model, for any choice of parameters; this is the case of a *misspecified model*. Therefore, there could be several choice of the parameters that give slightly different realizations that approximate the truth in a similar way.
2. Moreover, the inference scheme we use is *approximate*: it gives us a blur of the true parameter distribution. As discussed in `Wilkinson (2008) <https://www.degruyter.com/view/journals/sagmb/12/2/article-p129.xml>`_, this corresponds to assuming some noise structure on the observation on which the model is fit; it is probably the case that the data is not perfect, but understanding the quantity of noise present in it is an hard issue as well.

Overall, it is hard to be sure that this uncertainty is *calibrated*, namely that it actually describes the underlying probability of the parameters.

.. As noticed in the discussion about the :ref:`likelihood-free inference method <Inference>`, the posterior distribution we get is an approximation (a sort of blurring) of the true posterior. We remark that, in this case, the model we use is deterministic, so that its likelihood (and hence posterior) is a singular value peaked in the parameters value corresponding to the truth. We instead get a wider, smoother posterior; so, how is that to be interpreted? Notice the following two thigs:

.. First, it probably is the case that the observation we get from reality is not a full realization of the model


4. What assumptions have been made in this model?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Three main assumptions we have used to develop our epidemic model are:

- Tested people are composed mostly of the ones who needed clinical care at the hospital; this is reasonable according to what said on `this government webpage <https://www.gov.uk/guidance/coronavirus-covid-19-information-for-the-public>`_ which reports that, as of the 15th of April, 390,731 out of 417,649 tests were done on people with a medical need and the most essential workers and their families.

- Restrictive measures as of the 11th April will be kept in place for the prediction horizon

- Once people are tested positive and admitted into hospital, they are isolated, not being able anymore of transmitting the infection.

- Conditions about hospital use remain more or less constants; specifically, we do not explicitly model the occupation of hospital beds and ICUs, which, if saturated, can have a large impact on the death rate of the disease.

- Finally, we are assuming that a person cannot catch the disease twice; this is still matter of debate; however, even if this were the case, we expect it not to change too much the dynamics of the epidemics in a first phase, in which a great part of the population is still susceptible anyway. It would of course matter a lot in the long time dynamics.

Other assumptions are explained in :ref:`Epidemic model <Model>`.

5. This prediction looks scary. Are you sure it is correct? Are there any caveats?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Of course we are **not** sure it is correct; nobody can predict the future and, moreover, every model is a simplification of reality. However, some models may be useful to have better understanding of possible outcomes of some phenomena, given some conditions. Therefore, you need to take into account that:

- the predictions of this model are based on some :ref:`assumptions <4. What assumptions have been made in this model?>`, and if in reality these assumptions will not be satisfied (as the fact that restrictive measures will be kept in place for the prediction horizon), the forecast will most likely be invalidated.

- Our predictions contain an uncertainty range, but what that uncertainty means is hard to be understood (as discussed :ref:`here <3. How should I interpret the uncertainty predicted by this model?>`).

- The predictions eventually rely on the accuracy of the data the model was provided with; in emergency settings like this, data is a partial observation of reality. Our model tries to take that into account for some part (for instance explicitly modelling the confirmed cases as the ones who come into hospital, which is mostly true in the first phase of the pandemics in the UK), but of course it cannot do that perfectly.

- As said above, every model is a simplification of reality, and this is clearly an extreme simplification, as it describes the whole population in England as if it was a well-mixed fluid, so that every person can interact with anyone else with the same probability. This is of course not the case, but models which describe in more detail are harder to handle and fit to the data. Moreover, this kind of *well-mixed* models are quite commonly applied in the epidemics settings, and they have shown to have a fair amount of predictive power, when the considered populations are large. We hope that this is the case for the present setting as well.

.. write:
    - A short explanation about how models are always a simplification of complex reality.
    - About error.
    - About variation - are the graphs you show the average of a range etc?
    - Caveats - regarding the accuracy of data used. Regarding the assumptions you have made in the model (like people over 70 no longer meet anyone etc.) that are overly simplified?

6. How can I get in touch with the researchers behind this study?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
To know more about this research project, please contact Dr. Ritabrata Dutta at Ritabrata.Dutta@warwick.ac.uk. 

