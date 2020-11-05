.. _e2xgrader-configuration:

*****************************************
E2xgrader Configuration
*****************************************

To make sure all E2xgrader features are working as expected,
you need to edit your *nbgrader_config.py*.

Information about where this file is located can be found 
in the `Nbgrader docs`_.

Basic Configuration
===================

.. code-block:: python

   # nbgrader_config.py

   from e2xgrader.config import configure_base

   c = get_config()

   # Register custom preprocessors for autograding and generating assignments
   configure_base(c)

Configuring the Exchange
========================

For configuring the exchange look at the section :ref:`e2xgrader-exchange-config`.

A complete example of the *nbgrader_config.py* can be found in the `e2xgrader repository`_.

.. _Nbgrader docs: https://nbgrader.readthedocs.io/en/stable/configuration/nbgrader_config.html
.. _e2xgrader repository: https://github.com/DigiKlausur/e2xgrader/blob/master/nbgrader_config.py