COVID19-epidemics-forecast-England
==================================
Repository for the website describing the modeling effort and prediction for the COVID-19 epidemics in England, with the SEI4RD model.

This is fitted on data from England.

The website is available at:  https://OptimalLockdown.github.io/Covid19inEngland/


How to update this folder: 
==========================

Source files for the documentation are in the :code:`docsource` folder.

In order to preview changes locally, if you have Sphinx installed, run :code:`make html` from the root directory. Then it will build in the :code:`build/html` directory. There is no need to push that folder to github.

When ready to publish online, do :code:`make github`; this will build the website and put it in the :code:`docs` folder, which is the one served by Github pages.
