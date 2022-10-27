.. _incident_reports:

************************
Incident Reports
************************

21.03.2022 
==========

* Summary:

  * Safe Exam Browser (SEB) asks for an admin passoword on the client side (Windows)
  * SEB client is already running (macOS)

* Solution:

  * Windows

    * Navigate to `C:\\Users\\<PC\_USER>\\AppData\\Roaming\\SafeExamBrowser` 
      (Replace <PC\_USER> with your PC name)
    * Remove `SebClientSettings`
  * MacOS

    * Close SEB
    * Open terminal and run 
    
      .. code-block:: bash
        
        defaults delete org.safeexambrowser.SafeExamBrowser

24.11.2021 
==========

* Summary:

  * Midterm: MRC-Midterm-WS21
  * The seb config did not work on some student laptops:
    * On Windows: SEB service was nor running
    * On Mac: SEB was already running
  * Some students who came in person to the exam room brought laptops which do not have LAN port.

10.03.2021 
==========

* Summary:

  * Exam: WuS-WS20 trial
  * The connection to the server was sluggish after resizing some openstack instances. 
  * Four k8s nodes were not accessible from the load balancer instance.
  * OpenStack scheduler failed to schedule a big instance to a proper hardware node, 
    which resulted in OOM in that hardware node, thus killed the networking.

* Actions taken

  * [e2x sysadmin] found out which nodes were affected.
  * [fb02 sysadmin] did live migration and fix the scheduler.

* Future consideration before resizing an instance: inform fb02 sysadmin

21.10.2020 
==========

* Summary: 

  * Exam: RP-SS20
  * Autosave was broken during the exam and this happened to three student servers. 
    The manual save did not work too. When they saved the notebook, it says "Autosave Failed! last checkpoint 1 Hour ago".
* Actions taken during the exam

  * Asked them to back up the notebook locally

    * Print it into pdf
    * Bakcup all answer cells into a text file
  * Close and shutdown the notebook server
  * Copy the answers from backup file to the notebook
* Solutions:

  * Reproduce this error
  * Enable create notebook for student to make a backup into a jupyter notebook file instead of backing it up locally
  * Enable "Clear output" button
  * Clearing the output makes the autosave work again (this solution was suggested 
    by some students, and it worked for them). This was caused by some plots. 
    The feature has been added to e2xgrader by this `pull request <https://github.com/DigiKlausur/e2xgrader/pull/26>`_.
    
24.07.2020 
==========

* Summary: 

  * Exam: WuS-WS19
  * During WuS Klausur GrA, One of the node OOM due to being populated by 35 students 
    (resource request calculation was wrong). One solution, double minimum requests.
* Actions taken during the exam

  * Increased the resource req to 0.5GB per students so that they are evenly distributed
  * Not all students server were shutdown because they were working on the exam
* Actions taken after exam for GrB

  * Increased the resource req to 0.5GB, and they were evenly distributed
* Solutions:

  * Double min cpu and mem so that they can be scheduled evenly across multiple nodes
  * Ask Christoph (FB02) to provide c4.m24 (4Vcpu and 24Gb mem), node with this 
    resource can handle up to 40 students (assuming the requirement is about 250MB 
    to run the notebook, and thus the request is 500MB (twice as much as requirement)). 
    This is actually not necessary since we already have c2.m12

15.07.2020
==========

* Summary: 

  * The time in the laptops did not sync with the server because the ntp server was blocked by the firewall.
* Solution:

  * Enable ntp server in the lernstick and recopy the image
