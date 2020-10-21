.. _incident_reports:

************************
Incident Reports
************************

* 15.07.2020:
	* Summary:
		* The time in the laptops did not sync with the server because the ntp server was blocked by the firewall.
	* ToDo:
		* Enable ntp server in the lernstick and recopy the image [DONE]

* 24.07.2020(WUS)
	* Summary:
		During WuS Klausur GrA, One of the node OOM due to being populated by 35 students (resource request calculation was wrong). One solution, double minimum requests.
	* Actions taken during the exam
		* Increased the resource req to 0.5GB per students so that they are evenly distributed
		* Not all students server were shutdown because they were working on the exam
	* Actions taken after exam for GrB
		* Increased the resource req to 0.5GB, and they were evenly distributed
	* ToDo:
		* Double min cpu and mem so that they can be scheduled evenly across multiple nodes [DONE]
		* Ask Christoph (FB02) to provide c4.m24 (4Vcpu and 24Gb mem), node with this resource can handle up to 40 students (assuming the requirement is about 250MB to run the notebook, and thus the request is 500MB (twice as much as requirement)).
      * This is actually not necessary since we already have c2.m12

* 21.10.2020 (RP)
	* Summary:
    Autosave was broken during the exam and this happened to three student servers.
		The manual save did not work too. When they saved the notebook, it says "Autosave Failed! last checkpoint 1 Hour ago".
	* Actions taken during the exam
    * Asked them to back up the notebook locally
			* Print it into pdf
			* Bakcup all answer cells into a text file
		* Close and shutdown the notebook server
		* Copy the answers from backup file to the notebook
	* ToDo:
    * Reproduce this error
		* Enable create notebook for student to make a backup into a jupyter notebook file instead of backing it up locally
		* Enable "Clear output and restart kernel" button
			* Sometimes clearing the output makes the autosave work again (This solution was suggested by some students, and it worked for them). This was caused by some plots.
