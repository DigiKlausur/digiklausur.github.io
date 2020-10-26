.. _e2xgrader-student:

*****************************************
E2xgrader Student Version
*****************************************

E2xstudent bundles the student side extensions for e2xgrader.

There are two sets of extensions:

- exam
- assignment

The assignment extensions come with multiple and single choice support
and a toolbar that indicates which cells students should put their answer
in. 

The exam extensions include:

- Restricted tree (disables creating notebooks and files)
- Restricted notebook (disable functionality such as adding or deleting cells)
- Exam toolbar with custom submit

Installation
============

Install e2xstudent

.. code-block:: bash

   git clone  https://github.com/DigiKlausur/e2xstudent.git
   cd e2xstudent
   pip install .

Enable custom assignment list (for configuration see :ref:`e2xgrader-configuration`)

.. code-block:: bash

   jupyter serverextension enable nbgrader --py --sys-prefix
   jupyter serverextension disable nbgrader.server_extensions.formgrader --sys-prefix
   jupyter serverextension disable nbgrader.server_extensions.assignment_list --sys-prefix
   jupyter nbextension install nbgrader --py --sys-prefix --overwrite
   jupyter nbextension enable nbgrader --py --sys-prefix
   jupyter serverextension enable e2xgrader --py --sys-prefix
   jupyter nbextension install e2xgrader --py --sys-prefix --overwrite
   jupyter nbextension enable e2xgrader --py --sys-prefix


Enable all extensions (exam and assignment):

.. code-block:: bash

   jupyter nbextension install e2xstudent --py --sys-prefix
   jupyter nbextension enable e2xstudent --py --sys-prefix

Enable only assignment extensions:

.. code-block:: bash

   jupyter nbextension install e2xstudent --py --sys-prefix
   jupyter nbextension enable e2xstudent --py --sys-prefix
   jupyter nbextension disable exam_view/main --sys-prefix
   jupyter nbextension disable restricted_tree/main --section=tree --sys-prefix
