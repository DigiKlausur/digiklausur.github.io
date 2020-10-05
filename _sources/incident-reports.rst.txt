.. _incident_reports:

************************
Incident Reports
************************

* 15.07.2020:
	* Summary:
		* The time in the laptops did not sync with the server because the ntp server was blocked by the firewall.
	* ToDo:
		* Enable ntp server in the lernstick and recopy the image [DONE]

* 24.07.2020
	* Summary:
		During WuS Klausur GrA, One of the node OOM due to being populated by 35 students (resource request calculation was wrong). One solution, double minimum requests.
	* Actions taken during the exam
		* Increased the resource req to 0.5GB per students so that they are evenly distributed
		* Not all students server were shutdown because they were working on the exam
	* Actions taken after exam for GrB
		* Increased the resource req to 0.5GB, and they were evenly distributed
	* ToDo:
		* Alerting when too many pods are scheduled to one nodes?
		* Ask Christoph (FB02) to provide c4.m24 (4Vcpu and 24Gb mem), node with this resource can handle up to 40 students (assuming the requirement is about 250MB to run the notebook, and thus the request is 500MB (twice as much as requirement)) 
