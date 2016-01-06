.. _deployment-checklist:

Deployment Checklist
--------------------

**Documentation:**
All steps to deploy a project are explicitly written down and, wherever 
possible, fully automated to ensure consistency and repeatability. For web 
service deployments, we have found `Fabric <http://www.fabfile.org>`_ to be a 
valuable tool.

**Source Code Management:**
All source files that are to be deployed must be managed using a source control
system as described under :doc:`Source Code, Data, and Reproducibility 
<coding_and_software>`. The *deployment* procedure should not assume that code 
will be deployed from a `default` or `master` code branch and must make it 
simple to select a branch or specific revision to deploy. (This makes it 
easier to roll back flawed updates and deploy hot fixes while preserving our 
policy that all code must be reviewed before entering the GreeneLab Bitbucket 
repository.)
