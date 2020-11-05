.. _e2xgrader-student-mode:

Student Assignment Mode
=======================

In student assignment mode the assignment list is enabled.

Assignment View Toolbar
-----------------------

Additionally the *Assignment View* toolbar will be activated
whenever a student opens a notebook with nbgrader cells in it.
The toolbar displays a blue bar above each solution cell to
avoid confusion about where a student should write their answer.

For code cells the bar also includes a button to run the cell.
For markdown cells the bar allows you to switch between
edit mode (unrendered cell) and preview mode (rendered cell).

.. image:: img/assignment_view.png


Activate Student Assignment Mode
--------------------------------

To activate student assignment mode execute the following 
in a terminal:

.. code-block:: bash

   python -m e2xgrader activate student --sys-prefix