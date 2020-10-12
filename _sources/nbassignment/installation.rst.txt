.. _nbassignment-installation:

*****************************************
Nbassignment Installation
*****************************************

The nbassignment package needs some e2xgrader functionality.
For information on how to install e2xgrader, see :ref:`e2xgrader-installation`.

Install nbassignment

.. code-block:: bash

   git clone https://github.com/DigiKlausur/nbassignment.git
   cd nbassignment
   pip install .

Enable nbassignment extensions

.. code-block:: bash

   jupyter serverextension enable nbassignment --py --sys-prefix
   jupyter nbextension install nbassignment --py --sys-prefix --overwrite
   jupyter nbextension enable nbassignment --py --sys-prefix