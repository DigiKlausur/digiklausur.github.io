.. _e2xgrader-installation:

*****************************************
E2xgrader Installation
*****************************************

The e2xgrader package needs some nbgrader functionality,
that has not been merged yet. For now you can use the 
branch *clean_up* of our `nbgrader fork`_.
It needs the custom exchange and configurable converters.

Install nbgrader
----------------

.. code-block:: bash

   git clone -b clean_up https://github.com/DigiKlausur/nbgrader.git
   cd nbgrader
   pip install .

Install e2xgrader
-----------------

.. code-block:: bash

   git clone https://github.com/DigiKlausur/e2xgrader
   cd e2xgrader
   pip install .

.. _e2xgrader-modes:

Enable e2xgrader extensions
---------------------------

E2xgrader comes with three modes:
    * teacher
    * student
    * student_exam

In teacher mode all grading extensions are activated.
In student mode only the *assignment_list* extension and a toolbar is enabled.
In student_exam mode, you get a restricted notebook interface

You can easily switch between modes via:

.. code-block:: bash

   python -m e2xgrader activate <mode> --sys-prefix


Enable teacher mode:

.. code-block:: bash

   python -m e2xgrader activate teacher --sys-prefix

Finally we need to edit our *nbgrader_config.py* to register our changes.
See the :ref:`e2xgrader-configuration` section for details.

.. _nbgrader fork: https://github.com/DigiKlausur/nbgrader/tree/clean_up
