.. _Data:

Public Data Sources
==============================

The following data is used in this project: 

.. content-tabs::

    .. tab-container:: tab1
        :title: NHS/UK Government

        - `NHS England <https://www.england.nhs.uk/statistics/statistical-work-areas/covid-19-daily-deaths/>`_ reports daily deaths with age group in 20-years bands.
        - `UK Government website <https://www.gov.uk/government/publications/covid-19-track-coronavirus-cases>`_ reports daily overall number positive and deaths, with no age information but with geographical location. Presently, we neglected the location information, but we plan to use that in a metapopulation model in future.
        
    .. tab-container:: tab2
        :title: Contact matrix
        
        `Prem et al. (2017) <https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005697>`_ estimated contact matrices describing the frequency of contact between people of different age groups. 

        .. image:: img/C_UK.png
           :width: 10000

        As the NHS and UK governement dataset consider 5-year bands, we aggregated the contact matrix in order to match the data provided by NHS England. For the details of how these contact matrices are used in our model, please check :ref:`Epidemic model <Model>`.     



    .. tab-container:: tab3
        :title: Google mobility data

        In order to understand the impact of the restrictive measures implemented in the UK (whose timeline is reported `here <https://bfpg.co.uk/2020/04/covid-19-timeline/>`_), we combined declarations from government officials (e.g. self-isolation of elderly or schools closure) and `the change in mobility of the UK population reported by their Android devices <https://www.google.com/covid19/mobility/>`_, which was transformed to a machine readable format using `this github repository <https://github.com/pastelsky/covid-19-mobility-tracker>`_. This restrictive measures and change in the mobility of population is reflected in the values of :math:`\alpha` in our :ref:`Epidemic model <Model>`.
