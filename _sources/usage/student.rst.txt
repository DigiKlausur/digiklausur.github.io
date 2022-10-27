.. _usage_student:

*****************************************
Students
*****************************************

Depending on the courses, students can have access to e2x JupyterHub servers to work on
assignments. These servers can also be used for a light computing or programming. However, if you 
need more resources (CPU, RAM and GPU) for your projects, you can have a look at 
`Bonn-Rhein-Sieg university scientific computing <https://wr0.wr.inf.h-brs.de>`_.

Currently, there are two JupyterHub servers running on our in-house infrastructure 
and external server running on Hetzner cloud.

**1. Hetzner cloud**: `notebooks.inf.h-brs.de <https://notebooks.inf.h-brs.de>`_ 
used for the following courses:

  * `Berechenbarkeit und Komplexität <https://notebooks.inf.h-brs.de/hub/spawn?profile=BuK-SS22--Student>`_

**2. In-house server**: `e2x.inf.h-brs.de/jupyterhub/uebung <https://e2x.inf.h-brs.de/jupyterhub/uebung>`_ 
used for the following courses:

  Active courses:
  
  * `Artificial Intelligence for Robotics (SS22) <https://e2x.inf.h-brs.de/jupyterhub/uebung/hub/spawn?profile=AIR-SS22--Student>`_
  * `Autonomous Mobile Robots (SS22) <https://e2x.inf.h-brs.de/jupyterhub/uebung/hub/spawn?profile=AMR-SS22--Student>`_
  * `Mathematics for Robotics and Control (SS22) <https://e2x.inf.h-brs.de/jupyterhub/uebung/hub/spawn?profile=MRC-SS22--Student>`_
  * `Deep Learning for Robot Vision (SS22) <https://e2x.inf.h-brs.de/jupyterhub/uebung/hub/spawn?profile=DLRV-SS22--Student>`_
  * `Bayesian Inference and Gaussian Processes (SS22) <https://e2x.inf.h-brs.de/jupyterhub/uebung/hub/spawn?profile=BIGP-SS22--Student>`_

Archived courses:

  * Grundlagen von Wahrscheinlichkeitstheorie und Statistik
  * Robot Perception
  * Robot Manipulation
  * Natural Language Processing
  * Neural Networks

.. note::
    
    The JupyterHub servers are not a replacement of the current LMS 
    (`LEA <https://lea.hochschule-bonn-rhein-sieg.de>`_.). You can use the servers 
    to work on your assignments. Most courses assignments are managed through the hub, 
    while some graders prefer the distribution and submission through LEA.
    The assignments and feedback might also be released on 
    `LEA <https://lea.hochschule-bonn-rhein-sieg.de>`_. LEA forum is also available 
    should you have any problem with the assignments or the server.

Login to E2x JupyterHub
=======================

1. Hetzner cloud: `notebooks.inf.h-brs.de <https://notebooks.inf.h-brs.de>`_ 
--------------------------------------------------------------------------------------

First, you need to sign up to the server if you have not done so, then the instructor will authorize you. 
However, if you have been registered on LEA course, you should be able to log in automatically 
once you have signed up. Otherwise you should contact you instructors in order 
to get access to the server.

* **Signup**

  Click on Signup and fill in your username (FB02 UID, for examlple `mwasil2s`) and your password.
  The server only accepts **FB02 UID** as username. Also, do not use the same password as your 
  username.

  .. figure:: images/e2x-native-login.jpg
    :align: center

  .. note::
    
    If you are already registered on the LEA course, you can sign in automatically
    after you have signed up. Otherwise you should contact you instructors and e2x 
    sys admin will authorize you upon your instructors approval.

* **Change password**

  If you are not happy with your password, you can change it via JupyterHub home. Open **control panel**
  on the top right,

  .. figure:: images/e2x-hub-control-panel.png
    :align: center

  Then on the top left, you will find a button **Change password** which brings you to `change-password` form

  .. figure:: images/e2x-hub-home-native.png
    :align: center

  **Change password form**

  .. figure:: images/e2x-hub-native-change-pw.png
    :align: center

.. warning::
    
    Do not use the same password as your username.
    If you forget your password, please contact your instructors or e2x admin.


2. In-house server: `e2x.inf.h-brs.de/jupyterhub/uebung <https://e2x.inf.h-brs.de/jupyterhub/uebung>`_
-------------------------------------------------------------------------------------------------------

* **Access**

  Starting from SS21, students can access the `university server <https://e2x.inf.h-brs.de/jupyterhub/uebung>`_ 
  without using vpn or ssh-ing to the FB02 network.

* **Login**

  The local server uses FB02 LDAP to authenticate the users. Thus, you do not need to signup to get 
  access to the server. The username and password are the same as your `horde account <https://horde.inf.h-brs.de>`_.

  .. figure:: images/e2x-jupyterhub-login.png
    :align: center

  If you are registered in multipe courses, you will be prompted with different server options during spawning. 
  In some cases, we provide different environments with datasets, particular libraries, etc. 
  Unless requested, each course uses the same environment as defined in :ref:`Environment <server_environment>`.

  .. figure:: images/e2x-server-options.png
    :align: center

  .. warning::
  
    `Default` server does not have any course and the data is not persistent, meaning 
    it will be destroyed once the server is shut down.

Assignments
===========

We use `nbgrader` to manage the assignments. The due date should be the same as on LEA. So you have 
to submit the assignments before the due date.

* **Fetch Assignments**

  * Navigate to the **assignments** tab and click **fetch**

    .. figure:: images/assignment-fetch.png
      :align: center

  * Open the fetched assignments

    .. figure:: images/assignment-open.png
      :align: center

    You can also go to **Files** tab, and refresh the page to see all fetched assignments.

    .. warning::

      Do not open the assignment in multiple tabs, windows or browser. You might overwrite unsaved changes!

* **Submit Assignments**

  To submit the assignments, go to **Assignments** tab again, and click **Submit**. You can submit your 
  assignments multiple time as long as you do it before the due date.

  .. figure:: images/assignment-submit.png
    :align: center

  .. note::

    If you have problems submiting the assignments via the servers, you can of course submit them via 
    `LEA <https://lea.hochschule-bonn-rhein-sieg.de>`_.

* **Fetch Feedback**

  Under **Assignments** tab, you will be notified if the feedback has been released by the instructors.

  .. figure:: images/feedback-available.png
    :align: center

    You will see **feedback available to fetch** if it has been released. You can then fetch it.

  Once you fetch it, you can now open it.

  .. figure:: images/feedback-fetched.png
    :align: center

    Click **view feedback** to open the assignment feedback.

  .. note:: 

    You can also find your feedback under the assignment directory e.g. *WuS-01/feedback*

Resources and Quota
===================

The student server is limited to 2 cores of CPUs and 1GB of RAM, and 1GB of storage.
Anything under `/home/jovyan` is persistent and the rest will be regenerated when you restart the 
server. This storage can be increased according to the request from the instructors, but this can only 
be done if the request is proposed before the semester starts.

**Automatic kernel and server culling**

* Culling idle kernel

  Idle notebook kernel whithout any activities for *one hour* will be culled automatically.
  If this happens and you want to come back to your work, you should restart your kernel by going 
  to **Kernel** tab and choose **Restart and Clear Output**. You can also close your notebook and 
  reopen it.

  You can also restart your server by going to **Control Panel** menu (on the top right) and choose 
  **Stop My Server** and once it's done stopping the server, click **Start My Server** to 
  start your server.

* Culling idle server

  The idle culler automatically shuts down singleuser notebook servers when they are not used for 
  *one hour* to reduce the resource usage. Users need to relogin to spawn a new server.

  We also recommend you to shutdown or close your Jupyter Notebook server if you are not using it 
  and help us reducing the resource usage. 

.. note::

  The persistent data will be deleted after `Einsicht` which is regularly scheduled in the next 
  semester after the exam. 
  
  We suggest you to always backup you data in your local machine.

  Zip and dowload files from the server

  .. figure:: images/zip-and-download-hw.png
    :align: center


.. _working_on_assignments_locally:

Working on the assignments locally
==================================

The easiest way to setup your local environment is via docker. With docker, you can just pull 
our docker image and mount the assignments you have downloaded from the server to your container.

* **Linux and Mac OS**

  * `Install docker engine for Linux <https://docs.docker.com/engine/install/ubuntu/>`_
  * `Install docker engine for Mac OS <https://docs.docker.com/docker-for-mac/install/>`_
  * Open terminal and run our image (this will automatically pull and run the docker image)

    .. code-block:: bash

      docker run -it --name notebook -v $HOME/assignments:/home/jovyan/assignments --rm -p 8888:8888 digiklausur/notebook-dev:latest

    Replace the following:
      * `$HOME/assignments` --> replace this with the path to your assignment in your local machine
    
    You can also replace the image, 
      * digiklausur/notebook-dev:latest --> digiklausur/notebook:latest

    where `latest` and `8bf9827` are the image tags.

  * The output should look like the following

    .. code-block:: bash

      [I 13:24:27.563 NotebookApp] The Jupyter Notebook is running at:
      [I 13:24:27.564 NotebookApp] http://8ad5cc4be28c:8888/?token=b537e4e4a92b8ba7ac0ca2f5ea2034ac36fcc1d20d0eb53a
      [I 13:24:27.564 NotebookApp]  or http://127.0.0.1:8888/?token=b537e4e4a92b8ba7ac0ca2f5ea2034ac36fcc1d20d0eb53a

    Click on the `http://127.0.0.1:8888/?token=...`.

    This will take you to your browser once you click that link.

  * You can also open your browser manually and go to `localhost:8888 <localhost:8888>`_. Then input your token manually if asked. 
  
    In this example, your token is `b537e4e4a92b8ba7ac0ca2f5ea2034ac36fcc1d20d0eb53a`.

* **Windows**

  * `Follow this instruction to install docker engine on Windows 10 <https://docs.docker.com/docker-for-windows/install/>`_
  * Once it gets installed, open `Command Prompt`
  * Run our docker figure:

    .. code-block:: bash

      docker run -it --name notebook -v C:\Users\MohammadWasil\Downloads\WuS-WS20 --rm -p 8888:8888 digiklausur/notebook-dev:latest

    This may take some times to pull from docker image.
    
    Replace *C:\\Users\\MohammadWasil\\Downloads\\WuS-WS20* with the proper path to your assignments or course.

  * Once it is done pulling from docker hub, you will get the link and the token, copy that link and open 
    it in your browser

    .. figure:: images/e2x-docker-windows-run-token.png
      :align: center

  * Open Jupyter Notebook server

    .. figure:: images/e2x-docker-windows-nb-tree.png
      :align: center
      
      Notebook tree which shows all files and directories under *C:\\Users\\MohammadWasil\\Downloads\\WuS-WS20*
  
  * Open the assignment

    .. figure:: images/e2x-docker-windows-nb-tree-assignment.png
      :align: center
      
      Assignment 01 directory `(WuS-HW01)` for WuS.

    .. figure:: images/e2x-docker-windows-nb-hw.png
      :align: center
      
      SuperTest.ipynb is the notebook file that you have to work on.
      
.. note::

  If you work locally on your machine, you should re-upload your work to the server, under the corresponding
  assignment directory. Only files under `assignment directory` are uploaded to the grading server.
  Also, make sure all the files required to run your assignment are also uploaded and the paths to the files
  are properly given in the notebook file.

The Don'ts
==========

.. raw:: html
  
  <font color="red"><b>You are not allowed to:</b></font>

* Change the cell metadata
* Change directory structure of the assignment
* Rename directories or files
* Use other libraries which are not defined in 
  `our environment <https://github.com/DigiKlausur/docker-stacks/blob/master/notebook/requirements.txt>`_ 
* Use different version of our libraries
* Change the kernel

.. warning::

  Your submission may fail to run on the grading server, or cannot be graded 
  if you do the don'ts.

.. _server_environment:

Environment
===========

All environments we use on the servers can be found :ref:`here <environment>`.


FAQs
====

* **[notebooks.inf.h-brs.de] I cannot login after signup**. You may not be registered on the LEA course,
  contact your instructors to authorize you.
* **[notebooks.inf.h-brs.de] my username is already used**. Please contact your instructors, e2x admins 
  or post this on LEA forum so that they can check and come back to you as soon as possible.
