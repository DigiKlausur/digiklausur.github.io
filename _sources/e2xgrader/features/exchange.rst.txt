.. _e2xgrader-exchange:

Custom Exchange
===============

E2xgrader comes with a custom exchange that has the following
features:


Personalized Inbound
--------------------

If activated, the custom exchange uses a personalized inbound
directory for each student.

Assume you have the course *MyCourse* and the assignment
*MyAssignment*. In the original nbgrader exchange the student
will submit to :code:`<exchange_directory>/MyCourse/inbound/`.
This will be the same for each student and causes a potential security 
issue. If a student knows the name of the submission of another student,
they can read their submission.

If the personalized inbound is used, the student will submit to
:code:`<exchange_directory>/MyCourse/personalized-inbound/<student_id>/`.
This directory is only readable by the student.


Personalized Outbound
---------------------

If activated, the custom exchange uses a personalized outbound
directory for each student.

This allows for creating custom versions of an assignment per student.
Students will fetch from 
:code:`<exchange_directory>/MyCourse/outbound/MyAssignment/<student_id>/`.

For this to work you will need a release version for each student.
In your formgrader you will need to create a folder for each student 
under the release version of an assignment.

Instead of having your notebooks under
:code:`release/MyAssignment/MyNotebook.ipynb` you will need to create a
directory for each student as
:code:`release/MyAssignment/<student_id>/MyNotebook.ipynb`. These notebooks
can then be personalized.

.. _e2xgrader-exchange-config:

Configuring the Exchange
------------------------

To activate the custom exchange you need to edit to your *nbgrader_config.py*.

Activating the Exchange
***********************

.. code-block:: python

   # nbgrader_config.py
   from e2xgrader.config import configure_exchange

   c = get_config()

   # Register the custom exchange
   configure_exchange(c)

Activating the Personalized Inbound
***********************************

By default the personalized inbound is deactivated. To activate it, add the
option :code:`c.Exchange.personalized_inbound = True` to your 
*nbgrader_config.py*.

.. code-block:: python

   # nbgrader_config.py
   from e2xgrader.config import configure_exchange

   c = get_config()

   # Register the custom exchange
   configure_exchange(c)

   # Activate the personalized inbound directory
   c.Exchange.personalized_inbound = True

Activating the Personalized Outbound
************************************

By default the personalized outbound is deactivated. To activate it, add the
option :code:`c.Exchange.personalized_outbound = True` to your 
*nbgrader_config.py*.

.. code-block:: python

   # nbgrader_config.py
   from e2xgrader.config import configure_exchange

   c = get_config()

   # Register the custom exchange
   configure_exchange(c)

   # Activate the personalized outbound directory
   c.Exchange.personalized_outbound = True