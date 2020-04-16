.. _Data:

Public Data Sources
==============================

The following data is used in this project: 

.. content-tabs::

    .. tab-container:: tab1
        :title: NHS/UK Government

        - `NHS England <https://www.england.nhs.uk/statistics/statistical-work-areas/covid-19-daily-deaths/>`_ reports daily deaths with age group in 20-years bands.
        - `UK Government website <https://coronavirus.data.gov.uk/>`_ reports daily overall number positive and deaths, with no age information but with geographical location. Presently, we neglected the location information, but we plan to use that in a metapopulation model.
        
    .. tab-container:: tab2
        :title: Contact matrix
        
        `Prem et al. (2017) <https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005697>`_ estimated contact matrices describing the frequency of contact between people of different age groups. Essentially, for a person in a given age group, they give the average number of contacts that person has with people from all possible age groups. They consider 5-year bands, and split the type of contacts into 4 categories (see the image below).

            .. image:: img/C_UK.png
               :width: 13000

        As the NHS governement dataset consider 20-year bands, we aggregated the contact matrices provided by Prem et al. (2017) in order to match that.

    .. tab-container:: tab3
        :title: Google mobility data

        In order to understand the impact of the restrictive measures implemented in the UK (whose timeline is reported `here <https://bfpg.co.uk/2020/04/covid-19-timeline/>`_), we combined declarations from government officials (e.g. schools closure) and        `Google mobility data <https://www.google.com/covid19/mobility/>`_, which was transformed to a machine readable format using the code available at `this github repository <https://github.com/pastelsky/covid-19-mobility-tracker>`_


