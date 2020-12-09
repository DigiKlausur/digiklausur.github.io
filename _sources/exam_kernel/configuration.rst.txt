.. _exam_kernel-configuration:

*****************************************
ExamKernel Configuration
*****************************************

The ExamKernel can be configured using the
`IPython Configuration System <https://ipython.readthedocs.io/en/stable/config>`_.
This file is usually located under ``~/.ipython/profile_default``.
If it does not exist you can create it.

There are three configuration options for the ExamKernel.

1. Initialization Code
----------------------

This is the code that will be executed every time the kernel is initialized 
and can be set via the configuration option ``init_code``.

Example config:

.. code-block:: python

  # sample ipython_config.py
  c = get_config()

  c.ExamKernel.init_code = 'import random'

In this example the library ``random`` is imported every time the kernel is initialized,
making it available to the user right away. You can execute arbitrary code here.


2. Allowed Imports
----------------------

If you want to allow the user to only use certain libraries, you can specify them using
the allowed_imports configuration option. All other libraries will be blocked by default
if this option is set.

Example config:

.. code-block:: python

  # sample ipython_config.py
  c = get_config()

  c.ExamKernel.allowed_imports = ['math', 'numpy', 'scipy']

In this example the student can only import the libraries math, numpy and scipy.
If the user tries to import any other library (e.g. matplotlib), he or she will
see the following message:

.. code-block:: python

  ---------------------------------------------------------------------------
  ModuleNotFoundError                       Traceback (most recent call last)
  <ipython-input-5-041c468338fc> in <module>
  ----> 1 raise ModuleNotFoundError('No module named matplotlib or matplotlib blocked by kernel.')

  ModuleNotFoundError: No module named matplotlib or matplotlib blocked by kernel.
  Allowed imports are: [math, numpy, scipy]


3. Blocked Imports
----------------------

If you want to block the user from importing certain libraries,
but let them use all others, you can use the blocked_imports configuration option.

.. hint::

  If the ``allowed_import`` list is not empty, the ``blocked_imports`` option will take no effect.

Example config:

.. code-block:: python

  # sample ipython_config.py
  c = get_config()

  c.ExamKernel.blocked_imports = ['math', 'numpy', 'scipy']

In this example the user can not import the libraries ``math``, ``numpy`` and ``scipy``.
If the user tries to import a blocked library (e.g. math), he or she will see the following message:

.. code-block:: python

  ---------------------------------------------------------------------------
  ModuleNotFoundError                       Traceback (most recent call last)
  <ipython-input-5-041c468338fc> in <module>
  ----> 1 raise ModuleNotFoundError('No module named math or math blocked by kernel.')

  ModuleNotFoundError: No module named math or math blocked by kernel.
  The following imports are blocked: [math, numpy, scipy]


4. Allowed Magics
-----------------

If you want to allow the user to only use cell and line magics, you can specify them using
the allowed_magics configuration option. All other magics will be blocked by default
if this option is set.

Example config:

.. code-block:: python

  # sample ipython_config.py
  c = get_config()

  c.ExamKernel.allowed_magics = ['time', 'timeit']

In this example the student can use the magics time and timeit.
If the user tries to use another magic, he or she will see the following message:

.. code-block:: python

  ---------------------------------------------------------------------------
  ValueError                                Traceback (most recent call last)
  <ipython-input-3-9ac756e7870e> in <module>
  ----> 1 raise ValueError('No magic named history or history blocked by kernel.\nAllowed magics are: [time, timeit]')

  ValueError: No magic named history or history blocked by kernel.
  Allowed magics are: [time, timeit]



5. Blocked Magics
-----------------

If you want to block the user from using certain magics,
but let them use all others, you can use the blocked_magics configuration option.

.. hint::

  If the ``allowed_magic`` list is not empty, the ``blocked_magicss`` option will take no effect.

Example config:

.. code-block:: python

  # sample ipython_config.py
  c = get_config()

  c.ExamKernel.blocked_magics = ['history']

In this example the user can not use the magic ``history``.
If the user tries to use a blocked import (e.g. history), he or she will see the following message:

.. code-block:: python

  ---------------------------------------------------------------------------
  ValueError                                Traceback (most recent call last)
  <ipython-input-3-9ac756e7870e> in <module>
  ----> 1 raise ValueError('No magic named history or history blocked by kernel.\The following magics are blocked: [history]')

  ValueError: No magic named history or history blocked by kernel.
  The following magics are blocked: [history]


6. Terminal Commands
--------------------

By default all lines starting with ``!`` will be removed. 
If you want students to be able to use terminal commands, 
you need to set the ```block_terminal_commands``` option.

Example config:

.. code-block:: python

  # sample ipython_config.py
  c = get_config()

  c.ExamKernel.block_terminal_commands = False