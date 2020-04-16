.. _Inference:

Likelihood-free inference
=========================================

.. content-tabs::

    .. tab-container:: tab1
        :title: Approximate Bayesian computation
                
        As the likelihood of parameters in the proposed epdiemic model is intractable, we use a likelihood-free inference scheme approximate Bayesian Computation (ABC) to calibrate the epidemic model based on daily number of confirmed infected individuals and deceased one in the UK. ABC allows us to fix a prior range for the parameters and uncertainty on them (defined by prior distribution :math:`\pi(\theta)`), and to obtain an uncertainty range in the prediction.  This inference scheme essentially works by looking for a value of the parameters which best approximates the observations. The fundamental ABC rejection sampling scheme iterates the following steps: 
        
        - Draw :math:`\theta` from the prior :math:`\pi(\theta)`.
        - Simulate a synthetic dataset :math:`\mathbf{x}^{sim}` from the simulator-based model :math:`\mathcal{M}(\theta)`.
        -  Accept the parameter value :math:`\theta` if :math:`\mathbf{d}(\mathbf{x}^{sim},\mathbf{x}^{obs}) < \epsilon`. Otherwise, reject :math:`\theta`.
        
        .. image:: img/ABC_rejection.png
        
        Here, the metric on the dataspace :math:`\mathbf{d}(\mathbf{x}^{sim},\mathbf{x}^{obs})` measures the closeness between :math:`\mathbf{x}^{sim}` and :math:`\mathbf{x}^{obs}`. The accepted :math:`(\theta,\mathbf{x}^{sim})` pairs are thus jointly sampled from a distribution proportional to :math:`\pi(\theta)p_{\mathbf{d},\epsilon}(\mathbf{x}^{obs}|\theta)`, where :math:`p_{\mathbf{d},\epsilon}(\mathbf{x}^{obs}|\theta)` is an approximation to the likelihood function :math:`p(\mathbf{x}^{obs}|\theta)`
        
        	

        .. centered:: :math:`p_{\mathbf{d}, \epsilon}(\mathbf{x}^{obs}|\theta) = \int p(\mathbf{x}^{sim}|\theta) \mathbb{K}_{\epsilon}(\mathbf{d}(\mathbf{x}^{sim},\mathbf{x}^{obs}))  d\mathbf{x}^{sim}` 
        
        proportional to :math:`P(\mathbf{d}(\mathbf{x}^{sim},\mathbf{x}^{obs})\leq\epsilon)`. In general, :math:`\mathbb{K}_{\epsilon}(\cdot)` needs to be a probability density function with a large concentration of mass near 0, in which the parameter :math:`\epsilon` denotes the amount of concentration (the smaller :math:`\epsilon`, the more concentrated the density is). This guarantees that, in principle, the above approximate likelihood converges to the true one when :math:`\epsilon \to 0`. Of course, decreasing the threshold increases the computational cost, as less simulations will be accepted. This is mitigated by efficient ABC algorithms in conjuction with High performance computing in `ABCpy <https://github.com/eth-cscs/abcpy>`_. 
        

    .. tab-container:: tab2
        :title: ABCpy

        For this work we use `ABCpy <https://github.com/eth-cscs/abcpy>`_ scientific library written in Python for Bayesian uncertainty quantification in absence of likelihood function, which parallelizes efficient approximate Bayesian computation (ABC) algorithms and other likelihood-free inference schemes efficiently using High performance computing.
        

