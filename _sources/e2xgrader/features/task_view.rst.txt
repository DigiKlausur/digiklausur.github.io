.. _e2xgrader-task-view:

Per cell grading view
=====================

Nbgrader comes with a per notebook view for grading, where you 
always see the full submission of each student.

E2xgrader adds a view where you can look at a single student answer
to a specific question.
This is based on the grade ids of the solution cells in the notebook.

The per cell grading view can be activated by selecting
*Manual Grading (Task View)*. First you select the assignment, then the notebook
and finally the name of the solution cell you want to look at.
Suppose you select a solution cell with the name *ColorA*. 
Then additionally to showing this cell, the per cell grading view will show
all cells where the grade id contains the string *ColorA*.
To make sure, that the question is displayed alongside the answer, you have to
adhere to a specific naming scheme.

Naming scheme for cells
^^^^^^^^^^^^^^^^^^^^^^^

The per cell grading view is just a cell filter, that only displays
cells containing a the id of a solution cell.

Assume you have cells with the following ids:

..

   - ColorA_ColorB_Description (A cell with information for ColorA and ColorB)
   - ColorA_Description (The question for ColorA)
   - ColorA (The solution cell, where the students put their answer)
   - test_ColorA (A test cell for ColorA)
   - ColorB_Description (The question for ColorB)
   - ColorB (The solution cell for ColorB)
   - test_ColorB (A test cell for ColorB)

The per cell grading view will let you select one of the two solution
cells *ColorA* and *ColorB*.

Assume we select the cell *ColorA*. Then all cells with the substring
*ColorA* will be displayed together. In the example above these are
*ColorA_ColorB_Description*, *ColorA_Description*, *ColorA* and *test_ColorA*.

All cells that do not contain the id *ColorA* will be hidden.