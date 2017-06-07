===================================================================================
Calling loops from HiChIP data
===================================================================================
.. image:: https://badge.fury.io/py/hichipper.svg
    :target: https://badge.fury.io/py/hichipper
 
.. image:: https://travis-ci.org/aryeelab/hichipper.svg?branch=master
    :target: https://travis-ci.org/aryeelab/hichipper
    
.. image:: https://img.shields.io/badge/License-MIT-blue.svg
    :target: https://opensource.org/licenses/MIT
 
.. image:: https://zenodo.org/badge/70860290.svg
    :target: https://zenodo.org/badge/latestdoi/70860290  

================
About
================

**hichipper** is an open-source command-line toolkit that performs restriction fragment bias-aware
preprocessing of `HiChIP data <https://www.nature.com/nmeth/journal/v13/n11/full/nmeth.3999.html>`_. 
This package takes output from a `HiC-Pro >https://github.com/nservant/HiC-Pro>`_ run and a sample manifest
file (``.yaml``) that coordinates optional high-quality peaks (identified through ChIP-Seq) and restriction
fragment locations as input and produces output that can be used to 1) determine library quality, 2) identify
and characterize DNA loops and 3) interactively visualize loops. Loops are assigned strength and confidence
metrics that can be used to evaluate samples individually or for differential analysis in
downstream tools.


.. image:: content/media/overview.png
   :width: 100%

================
Installation
================
.. toctree:: content/Installation

================
Dependencies
================
.. toctree:: content/Dependencies

================
Revisions
================
.. toctree:: content/revision-history
   
================
Author
================

The primary developer is `Caleb Lareau <https://caleblareau.github.io>`_ 
in the `Aryee Lab <https://aryee.mgh.harvard.edu/>`_.

================
Citation
================

If you use **proatac** in your research, please cite our tool at the following URL:
	
	``http://aryeelab.org/hichipper``
	
================
Bugs / Errors
================

Please let us know if you find any errors/inconsistencies in the documentation or code
by filing a new `Github Issue <https://github.com/aryeelab/hichipper/issues>`_.

