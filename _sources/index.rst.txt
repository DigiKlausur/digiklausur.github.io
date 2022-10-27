.. E2x DigiKlausur documentation master file, created by
   sphinx-quickstart on Wed May  6 16:20:34 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

################
E2X E-assessment
################

This site contains documentation and guidelines for :ref:`instructors <usage_instructor>` 
and :ref:`students <usage_student>` for using our service. The guidelines are mainly 
for teaching and examination purposes. The :ref:`JupyterHub section <e2x-jupyterhub>` describes 
our system architecture and environment we use.

.. toctree::
   :maxdepth: 1

   about
   research
   talks
   people
   incident-reports
   news

.. admonition:: News

  .. include:: /news.rst
    :start-line: 6
    :end-line: 13

  :ref:`More on news <news>`

.. toctree::
   :maxdepth: 2
   :caption: Usage

   usage/student
   usage/instructor

.. toctree::
   :maxdepth: 2
   :caption: JupyterHub

   jupyterhub/e2x-jupyterhub
   jupyterhub/environment
   jupyterhub/dynamic-config
   jupyterhub/deployment

.. toctree::
   :maxdepth: 2
   :caption: E2xgrader

   e2xgrader/e2xgrader
   e2xgrader/installation
   e2xgrader/configuration

.. toctree::
   :maxdepth: 2
   :caption: Nbassignment

   nbassignment/nbassignment
   nbassignment/installation

.. toctree::
   :maxdepth: 2
   :caption: ExamKernel

   exam_kernel/exam_kernel
   exam_kernel/installation
   exam_kernel/configuration
