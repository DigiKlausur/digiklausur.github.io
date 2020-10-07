.. _e2xgrader-scramble:

Permute notebook during fetching
================================

You can change the order of questions in a notebook randomly during fetching
the assignment.

For this you have to make sure to adhere to the naming scheme for cells
described in the :ref:`e2xgrader-task-view` section.
Otherwise e2xgrader will not find all the cells associated to a solution cell.

To enable permutation of questions, you have to add a cell to your notebook
at the top. It does not matter what type (code, markdown, ...) the cell is.
This cell should only contain a single keyword:

.. code-block:: python

   %% scramble

How it works
------------

During fetching the username of the student is used as a seed for the 
pseudo-random number generator. 
Next the notebook is partitioned into questions using the following 
approach:

..

   1. Find all solution cells
   2. Find all cells where the grade id contains a solution cell id
   3. If a cell contains multiple solution cell ids, the solution cells
      and associated cells are grouped together
   4. All cells not associated to a solution cell will be moved to the
      top of the notebook
   5. The remaining grouped cells will be shuffled and appended to the
      notebook


When permuting notebooks, it is favorable to use the :ref:`e2xgrader-task-view`
since questions for submitted notebooks are not ordered again.