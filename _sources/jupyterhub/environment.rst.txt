.. _environment:

**********************
Environment
**********************

Grading and Assignment Environment
==================================

All environments we use in the servers can be found on our github repository 
`https://github.com/DigiKlausur/docker-stacks <https://github.com/DigiKlausur/docker-stacks/tree/dev>`_.

The generic image that we use for all courses:

* `ghcr.io/digiklausur/docker-stacks/notebook:latest <https://github.com/DigiKlausur/docker-stacks/tree/1ba0bc25385b8b45883cab6dccfe27d7941ea9a9>`_

The image can be run locally on your local PC running Linux, Mac OS or Windows, 
please follow :ref:`this instruction for more details <working_on_assignments_locally>`.

Exam Environment
================

The exam environment is derived from the same assignment or grading environment.
The differences lay on the restrictions on what exam users can do during exams, 
for example: default Jupyter Notebook menus are removed; files cannot be deleted;
there are some exam extensions installed. 

.. figure:: images/exam_environment.png
   :alt: an example of restricted view in exam environment
   :align: center

   an example of restricted view in exam environment

.. note::
  
   If you want some libraries to be available on the servers, feel free to contribute to our github repositories.

   All the software we use and develop are open source,
   feel free to comment and/or contribute to `our github https://github.com/DigiKlausur/ <https://github.com/DigiKlausur/>`_.
