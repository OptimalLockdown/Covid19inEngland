.. _FAQ:

Questions and Answers (for the public and media)
=================================================

.. TODO: add discussion on data-driven fitting wrt parameters determined by clinician knowledge, and fact that parameters that better fit a model are not the ones that are actually the true physical parameters with that physical meaning. However, possibilitiy of leveraging experts adive (through priors) and data-driven procedures.

*******************************
General Questions
*******************************

1. What is this project?
~~~~~~~~~~~~~~~~~~~~~~~~
“Optimal Lockdown” is a project conducted by researchers at the universities of Warwick, Oxford and Nottingham. It has three phases.

In the first phase - visible as of 20th April 2020 on this website - we have developed an **epidemic model to understand the spread of COVID-19 in England**. This model is tailored to the English situation and calibrated with approximate Bayesian computation (ABC). The model has been developed by Lorenzo Pacchiardi (Dept. of Statistics, University of Oxford) and `Dr. Ritabrata Dutta <https://warwick.ac.uk/fac/sci/statistics/staff/academic-research/dutta/>`_ (Dept. of Statistics, University of Warwick).

In the second phase, this model will be improved by integrating data about commuting patterns in England. 

In the third phase of the project, `Dr. Susana Gomes <https://warwick.ac.uk/fac/sci/maths/people/staff/gomes/>`_ (Dept. of Mathematics, University of Warwick) and `Dr. Dante Kalise <https://sites.google.com/view/dkalise>`_ (School of Mathematical Sciences, University of Nottingham) will use these models to **design an optimal lockdown for England** (e.g., what commuting routes to allow, what retail to close, etc.) and **how to exit lockdown** (what and when to reopen). The exit strategy will be updated daily based on the latest data available. 

We use data on the spread of COVID-19 in England provided by Public Health England (PHE), the National Health Service (NHS) and the Office for National Statistics (ONS). We also integrate `Google mobility data <https://www.google.com/covid19/mobility/>`_ in our model to reflect the effect of the current lockdown on the English population. We will also add data about commuting patterns in England based on the 2011 census data. Check our page on our data sources in more detail here. 

2. How can I get in touch with the researchers behind this study?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
To know more about this research project, please contact Dr. Ritabrata Dutta at Ritabrata.Dutta@warwick.ac.uk.


**************************************************************
Questions about the first phase of the project
**************************************************************
.. 
    1. What are the most important conclusions based on your model?
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    
    - According to our model, we are currently (April 20) crossing the peak of the number of COVID-19 deaths per day in hospitals in England. However, sadly, a large number of people will still die in the next seven weeks. 
    - According to our model (as of April 20), assuming the current lockdown measures are extended until early June and the population continues to comply with them, the number of daily COVID-19 deaths in hospitals in England will reduce to nil by the first week of June. 
    - As has been concluded by other studies, we also found that older people had a significantly higher probability of needing hospitalization and of dying compared to younger people.
    
    Note: these conclusions have last been updated on 20 April 2020. 
    
1. How does our model differ from others that predict the spread of COVID-19?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The greatest difference with other models we are aware of is that they use global estimates on how the epidemic spreads (eg. how many days it takes for a person to start showing symptoms once infected, or how many days between being diagnosed and death) whereas we have used data on the spread of COVID-19 in England to **learn the values of these parameters as they apply specifically to England**. Using :ref:`our method <Inference>`, these parameters can be learnt from local data anywhere, and used to create accurate local predictions. To compute these estimates, we have used a software called `ABCpy <https://github.com/eth-cscs/abcpy>`_.
 
Second, as the prediction is based on **real local data, it can and will be updated regularly**, and it thus reflects the current situation in England as accurately as possible. 

Our model is an extension of recent models by `Adam Kucharski et al. <https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=2ahUKEwiqhJnvyvXoAhVBUhUIHb5PDGcQFjABegQIAhAB&url=https%3A%2F%2Fwww.thelancet.com%2Fjournals%2Flaninf%2Farticle%2FPIIS1473-3099(20)30144-4%2Ffulltext&usg=AOvVaw2nzzqBRFeMEQpqx_OTabGq>`_ and `Kiesha Prem et al. <https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwiUq9e2y_XoAhWCUBUIHSw3CXsQFjAAegQIAhAB&url=https%3A%2F%2Fwww.thelancet.com%2Fjournals%2Flanpub%2Farticle%2FPIIS2468-2667(20)30073-6%2Ffulltext&usg=AOvVaw1UoR7nKMrtDnnvddKggVt4>`_, with the use of `Google mobility data <https://www.google.com/covid19/mobility/>`_ to reflect the effect of the current lockdown on the English population. The model we have created is a **compartmental model**, meaning one where the population (of England, in our case) is divided into compartments with different features (eg. susceptible, infected). The population is assumed to be well-mixed, i.e. each person has the same probability to meet with any other person; see here for further discussion on what this assumption means.

We are happy to hear suggestions to improve our model; please see :ref:`here <2. How can I get in touch with the researchers behind this study?>` for contact information.

2. What assumptions have been made in this model?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Five main assumptions we have used to develop our epidemic model are:

- The **people who have been tested are mostly those who needed clinical care in hospitals**. This assumption is backed up by `government data on testing <https://www.gov.uk/guidance/coronavirus-covid-19-information-for-the-public>`_: as of the 15th of April, 390,731 out of 417,649 tests were done mostly on people with a medical need in hospital and the most essential NHS workers and their families, a further detailed `here <https://www.gov.uk/government/publications/coronavirus-covid-19-scaling-up-testing-programmes/coronavirus-covid-19-scaling-up-our-testing-programmes#scaling-up-our-testing-programmes>`_.
- The **restrictive measures that are in effect as of 11 April will be kept in place** for the prediction horizon, i.e. until the end date of the prediction. 
- Once people are **tested positive and admitted into hospital, they are isolated** and no longer able to transmit the infection. 
- **Conditions about hospital use remain more or less constant**; specifically, we do not explicitly model the occupation of hospital beds and ICUs, which, if saturated, can have a large impact on the death rate of the disease.
- Finally, we assume that **a person cannot catch the disease twice**. This is still a matter of debate; however, even if this were the case, we expect it not to change too much the dynamics of the epidemics in a first phase, in which a great part of the population is still susceptible anyway. It would naturally make a great difference in the long time dynamics.

Other assumptions are explained in the :ref:`Epidemic model <Model>`.

3. Are we sure our prediction is correct? Are there any caveats?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Of course we are **not** sure it is correct; nobody can predict the future and, moreover, every model is a simplification of reality. However, models may be useful to have a better understanding of possible outcomes of some phenomena, given some conditions. Therefore, you need to take into account that:

- The predictions of this model are based on a number of assumptions, and if in reality these assumptions are not satisfied (e.g. that restrictive measures will be kept in place for the prediction horizon), the forecast will most likely be invalidated.
- Our predictions contain an uncertainty range, but what that uncertainty means is hard to understand (as discussed :ref:`here <4. What do we mean by uncertainty in this model?>`).
- The predictions eventually rely on the accuracy of the data the model was provided with; in emergency settings like this, data is a partial observation of reality. Our model tries to take that into account to an extent (for instance we explicitly assume that all confirmed cases were diagnosed in hospitalised people, which has been mostly true until testing of NHS workers was started), but of course it cannot do so perfectly.
- As said above, every model is a simplification of reality, and this is clearly an extreme simplification, as it describes the whole population in England as if it was a well-mixed fluid, so that every person can interact with anyone else with the same probability. This is of course not the case, but models which describe reality in more detail are harder to handle and fit to the data. Moreover, this kind of well-mixed models are quite commonly applied in epidemics settings, and they have shown to have a fair amount of predictive power, when the considered populations are large. We hope that this is the case for the present setting as well.

4. What do we mean by uncertainty in this model?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The uncertainty of our prediction is the orange shaded area in each graph, which means that the actual value (e.g. of daily deaths) will be within the orange range with 95 percent probability. 
The uncertainty is due to the fact that in this model we do not estimate the exact values of the parameters of the model (e.g. how many days it takes for a person to start showing symptoms once infected, or how many days between being diagnosed and death). Instead we estimate the probabilities of different possible values being the correct one. This is a central element of the Bayesian paradigm of statistics. 

This uncertainty can be thought of as arising due to our inability to describe the reality perfectly by our (deterministic) model, for any choice of the values of the parameters; this is called a misspecified model. Therefore, there could be several choices of the values of the parameters which approximate the truth in a similar way.

.. - Moreover, the :ref:`inference scheme <Inference>` we use is approximate: it gives us a blur of the true parameter distribution. As discussed in `Wilkinson (2008) <https://www.degruyter.com/view/journals/sagmb/12/2/article-p129.xml>`_, this corresponds to assuming some noise structure on the observation on which the model is fit; it is probably the case that the data is not perfect, but understanding the quantity of noise present in it is a hard issue as well.

Overall, it is hard to be sure that this uncertainty is calibrated, namely that it actually describes the underlying probability of the parameters.