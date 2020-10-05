.. _exam_kernel-installation:

*****************************************
ExamKernel Installation
*****************************************

The ExamKernel can be found on `GitHub <https://github.com/DigiKlausur/exam_kernel>`_.

The ExamKernel acts as a wrapper around a standard Python kernel,
that sanitizes the code before executing it.
For this cell magics and terminal commands are blocked.
It also allows for executing an initialization code and blocking 
or allowing certain imports. For more details see the 
:ref:`exam_kernel-configuration` section.

To install, clone the repository and do

.. code-block:: bash

  git clone https://github.com/DigiKlausur/exam_kernel
  cd exam_kernel
  pip install .
  jupyter kernelspec install exam_kernel --sys-prefix
