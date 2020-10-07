.. _e2xgrader-submit:

Hashing of student submissions
==============================

Motivation
----------

Consider the following scenario:

A student submits an exam and after receiving the grade claims, that the exam
that has been graded was changed after submitting it.
If the student submits a hand-written paper exam, the university can consult
a hand-writing expert to prove, that there have not been any changes made by
other parties.

If the student submits an electronic exam, proving that there the exam graded
is actually the exam submitted, is not such an easy task.
Because of that we hash the student submission and let students sign a sheet
with this hashcode. This way the exam of the student can be hashed again and
compared to the signed hashcode. If it is the same, the exam has not been
tampered with.

How it works
------------

To enable hashing of student submissions, the assignment has to fulfill the
following requirements:

- The assignment can only contain a single notebook and some additional files
- The name of the notebook has to be the same as the name of the assignment
- The e2xgrader assignment_list extension has to be installed on the student
  side

When a student submits their assignment, the following happens:

1. The timestamp of the submission is appended to the notebook

.. image:: img/timestamped_notebook.png

2. The timestamped notebook is hashed using SHA1
3. The hashcode is truncated to only contain the first 20 digits in order to 
   make checking the hashcode easier
4. A file named *{username}_info.txt* with the username, timestamp
   and truncated hashcode is generated

.. image:: img/hashcode_txt.png

5. A html file named *{notebook_name}_hashcode.html* of the notebook containing 
   both the timestamp and the hashcode is generated and shown to the student

.. image:: img/submission_html.png

6. The student copies the hashcode to a sheet of paper, signs it and submits it
   after the exam