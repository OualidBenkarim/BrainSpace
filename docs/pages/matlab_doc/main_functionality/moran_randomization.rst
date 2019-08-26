.. _moran_randomization:

====================
moran_randomization
====================

------------------
Synopsis
------------------

Computes the moran eigenvectors required for Moran spectral randomization 
(`source code
<https://github.com/MICA-MNI/BrainSpace/blob/master/matlab/analysis_code/moran_randomization.m>`_).

------------------
Usage
------------------

::

    Y_rand = moran_randomization(Y,MEM,n_perm,procedure,joint);

- *Y*: An n-by-m data matrix to randomize where n is number of datapoints and m are different modalities. 
- *MEM*: Moran eigenvectors as returned by :ref:`compute_mem`.
- *n_perm*: Number of perutations
- *procedure*: Randomization procedure; either 'singleton' or 'pair'.
- *joint*: If true, randomizes different modalities identically. 
- *Y_rand*: Randomized data. 

------------------ 
Description 
------------------ 

Implementation of Moran spectral randomization as presented by  `(Wagner and
Dray, 2015)
<https://besjournals.onlinelibrary.wiley.com/doi/full/10.1111/2041-210X.12407>`_.
This function uses the eigenvectors computed by :ref:`compute_mem` to generate
null model data with similar spatial autocorrelation. The implemented procedures
are 'singleton' and 'pair'. Singleton matches the input data's autocorrelation
more closely at the cost of fewer possible randomizations (max: 2\ :sup:`n`). In
most use-cases this allows for ample randomizations. In cases where the maximum
number of randomizations becomes restrictive, we recommend using the pair
procedure instead. 

