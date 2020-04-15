.. _Data:

Details of Data
==============================

The following data is used in this project: 

.. content-tabs::

    .. tab-container:: tab1
        :title: NHS England

        - [NHS England](https://www.england.nhs.uk/statistics/statistical-work-areas/covid-19-daily-deaths/) reports daily deaths with age group in 20-years bands.
        - [UK Government website](https://www.gov.uk/government/publications/covid-19-track-coronavirus-cases) reports daily overall number positive and deaths, with no age information but with geographical location; in this first time, we neglected the location information, but we plan to use that in the future.
        
    .. tab-container:: tab2
        :title: Contact Matrix
        
        [Prem et al. (2017)](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005697) estimated contact matrices describing the frequency of contact between people of different age groups; they consider here 5-year bands, which we aggregated in order to match the data provided by NHS England.  

    .. tab-container:: tab3
        :title: Restrictions

        In order to understand the impact of the restrictive measures implemented in the UK (whose timeline is reported [here](https://bfpg.co.uk/2020/04/covid-19-timeline/)), we combined declarations from government officials (for instance regarding eldelry self-isolating, or schools closure) and        [Google data regarding mobility](https://www.google.com/covid19/mobility/), which was transformed to a machine readable format using [this github repository](https://github.com/pastelsky/covid-19-mobility-tracker)
