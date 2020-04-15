.. _Data:

Details of Data
==============================

The following data is used in this project: 

.. content-tabs::

    .. tab-container:: tab1
        :title: NHS England/UK Government

        - `NHS England <https://www.england.nhs.uk/statistics/statistical-work-areas/covid-19-daily-deaths/>`_ reports daily deaths with age group in 20-years bands.
        - `UK Government website <https://www.gov.uk/government/publications/covid-19-track-coronavirus-cases>`_ reports daily overall number positive and deaths, with no age information but with geographical location. Presently, we neglected the location information, but we plan to use that in a metapopulation model.
        
    .. tab-container:: tab2
        :title: Contact Matrix
        
        `Prem et al. (2017) <https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005697>`_ estimated contact matrices describing the frequency of contact between people of different age groups. As the NHS and UK governement dataset consider 5-year bands, we aggregated the contact matrix in order to match the data provided by NHS England. The contact matrices used for our work is as following:
        
        .. image:: img/C_UK.png
           :width: 10000


    .. tab-container:: tab3
        :title: Restrictions

        In order to understand the impact of the restrictive measures implemented in the UK (whose timeline is reported `here <https://bfpg.co.uk/2020/04/covid-19-timeline/>`_), we combined declarations from government officials (e.g. self-isolation of eldelry or schools closure) and        `Google mobility data <https://www.google.com/covid19/mobility/>`_, which was transformed to a machine readable format using `this github repository <https://github.com/pastelsky/covid-19-mobility-tracker>`_
