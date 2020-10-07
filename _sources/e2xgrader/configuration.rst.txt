.. _e2xgrader-configuration:

*****************************************
E2xgrader Configuration
*****************************************

To use the custom exchange, autograder and fetch assignment,
we need to add it to our *nbgrader_config.py*.

Information about where this file is located can be found 
in the `Nbgrader docs`_.

1. Register the custom exchange

.. code-block:: python

   # nbgrader_config.py

   c = get_config()

   c.ExchangeFactory.submit = 'e2xgrader.exchange.E2xExchangeSubmit'
   c.ExchangeFactory.fetch_assignment = 'e2xgrader.exchange.E2xExchangeFetchAssignment'

2. Register custom preprocessors for autograding and generating assignments

.. code-block:: python

   c.Autograde.sanitize_preprocessors = [
       'nbgrader.preprocessors.ClearOutput',
       'nbgrader.preprocessors.DeduplicateIds',
       'nbgrader.preprocessors.OverwriteKernelspec',
       'e2xgrader.preprocessors.OverwriteCells',
       'nbgrader.preprocessors.CheckCellMetadata',
       'e2xgrader.preprocessors.Unscramble',
   ]

   c.Autograde.autograde_preprocessors = [
       'nbgrader.preprocessors.Execute',
       'nbgrader.preprocessors.LimitOutput',
       'e2xgrader.preprocessors.SaveAutoGrades',
       'nbgrader.preprocessors.AssignLatePenalties',
       'nbgrader.preprocessors.CheckCellMetadata',
   ]

   c.GenerateAssignment.preprocessors = [
       'nbgrader.preprocessors.IncludeHeaderFooter',
       'nbgrader.preprocessors.LockCells',
       'e2xgrader.preprocessors.ClearSolutions',
       'nbgrader.preprocessors.ClearOutput',
       'nbgrader.preprocessors.CheckCellMetadata',
       'nbgrader.preprocessors.ComputeChecksums',
       'e2xgrader.preprocessors.SaveCells',
       'e2xgrader.preprocessors.ClearHiddenTests',
       'nbgrader.preprocessors.ClearMarkScheme',
       'nbgrader.preprocessors.ComputeChecksums',
       'nbgrader.preprocessors.CheckCellMetadata',
       'e2xgrader.preprocessors.ValidateExtraCells'
   ]

A complete example of the *nbgrader_config.py* can be found in the `e2xgrader repository`_.

.. _Nbgrader docs: https://nbgrader.readthedocs.io/en/stable/configuration/nbgrader_config.html
.. _e2xgrader repository: https://github.com/DigiKlausur/e2xgrader/blob/master/nbgrader_config.py