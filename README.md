# COVID19-epidemics-forecast-England


We will publish here a work-in-progress version of an SEIRD model, fitted on data from England. 


The website is available at:  https://lorypack.github.io/COVID19-epidemics-forecast-England/


# How to update this folder: 

Source files for the documentation are in the `docsource` folder.

In order to preview changes locally, if you have Sphinx installed, run `make html` from the root directory. Then it will build in the `build/html` directory. There is no need to push that folder to github.

When ready to publish online, do `make github`; this will build the website and put it in the `docs` folder, which is the one served by Github pages. 
