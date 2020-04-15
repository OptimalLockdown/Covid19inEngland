.. _Inference:

Likelihood-free inference
=========================================

.. content-tabs::

    .. tab-container:: tab1
        :title: Approximate Bayesian computation

        We use Approximate Bayesian Computation as an inference scheme to fit the parameter values. This allows us to fix a prior range for the parameters, and to obtain an uncertainty range in the prediction.  This inference scheme essentially works by looking for a value of the parameters which best approximates the observations. The fundamental ABC rejection sampling scheme iterates the following steps: 
        
        - Draw :math:`\theta` from the prior :math:`\pi(\theta)`.
        - Simulate a synthetic dataset :math:`\mathbf{x}_{sim}` from the simulator-based model :math:`\mathbb{M}(\theta)`.
        -  Accept the parameter value :math:`\theta` if :math:`\mathbf{d}(\mathbf{x}_{sim},\mathbf{x}_{obs}) < \epsilon`. Otherwise, reject :math:`\theta`.
        
        :download: ABC_rejection.pdf
        
        Here, the metric on the dataspace :math:`\mathbf{d}(\mathbf{x}_{sim},\mathbf{x}_{obs})` measures the closeness between :math:`\mathbf{x}_{sim}` and :math:`\mathbf{x}_{obs}`. The accepted :math:`(\theta,\mathbf{x}_{sim})` pairs are thus jointly sampled from a distribution proportional to :math:`\pi(\theta)p_{\mathbf{d},\epsilon}(\mathbf{x}_{obs}|\theta)`, where :math:`p_{\mathbf{d},\epsilon}(\mathbf{x}_{obs}|\theta)` is an approximation to the likelihood function :math:`p(\mathbf{x}_{obs}|\theta)`
        
        :math:`p_{\mathbf{d}, \epsilon}(\mathbf{x}_{obs}|\theta) = \int p(\mathbf{x}_{sim}|\theta) \mathbb{K}_{\epsilon}(\mathbf{d}(\mathbf{x}_{sim},\mathbf{x}_{obs}))  d\mathbf{x}_{sim}`, 
        
        where :math:`\mathbb{K}_{\epsilon}(\mathbf{d}(\mathbf{x}_{sim},\mathbf{x}_{obs}))` is in this case a probability density function proportional to :math:`\mathbb{1}{(\mathbf{d}(\mathbf{x}_{sim},\mathbf{x}_{obs})<\epsilon)}`. Besides this choice for :math:`\mathbb{K}_{\epsilon}(\mathbf{d}(\mathbf{x}_{sim},\mathbf{x}_{obs}))`, that has been exploited in several ABC algorithms (for instance \cite{beaumont:2010, drovandi2011estimation, del:2012, lenormand2013adaptive}), ABC algorithms relying on different choices exist, for instance being proportional to :math:`\exp(-\mathbf{d}(\mathbf{x}_{sim},\mathbf{x}_{obs})/\epsilon)` in simulated-annealing ABC (SABC) \citep{Albert_2015}. In general, :math:`\mathbb{K}_{\epsilon}(\cdot)` needs to be a probability density function with a large concentration of mass near 0, in which the parameter :math:`\epsilon` denotes the amount of concentration (the smaller :math:`\epsilon`, the more concentrated the density is). This guarantees that, in principle, the above approximate likelihood converges to the true one when :math:`\epsilon \to 0`. Of course, decreasing the threshold increases the computational cost, as less simulations will be accepted.
        

    .. tab-container:: tab2
        :title: ABCpy

        For this work we use `ABCpy <https://github.com/eth-cscs/abcpy/tree/master/abcpy>`_ scientific library written in Python for Bayesian uncertainty quantification in absence of likelihood function, which parallelizes existing approximate Bayesian computation (ABC) algorithms and other likelihood-free inference schemes efficiently using High performance computing.
        

