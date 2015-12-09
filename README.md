# chef-compliance-installation-configuration-operation
This repo is for development of the initial chef-compliance course

# Objectives:
After completing this course, you should be able to:

Install and initially configure the Chef Compliance server

Perform scans with Chef Compliance

Remediate a compliance issue

Run Compliance Reports

Use InSpec to create and modify Chef Compliance profiles

View compliance statistics for a node

Note: You should have attended at least Chef Essentials, Chef Fundamentals or have equivalent Chef experience prior to attending this course.


# Classroom Lab
The hands-on labs require the following infrastructure which should be provided by the instructor and specified in Appendix Z.

Two standard AWS AMIs per student that are the same as the AMIs used in Chef Essentials training but upgrade to ChefDk 0.10.x
We need to put the chef user in the dockerroot group and make /var/run/docker.sock's group dockerroot in the future training images.
We need to build the shell init stuff for chef dk into the AMI images--the equivalent of 'echo 'eval "$(chef shell-init bash)"' >> ~/.bash_profile' then log out and in.

Students will install Chef Compliance on one instance and use the second instance to run compliance scans against.

# Student Workstations

Each student will need their own laptop workstation with the same specs as for Chef Essentials training.This course will not require virtual workstations.

# Modules
1. Intro
2. Installation
3. Running Scans, Remediation, and Testing
4. Using Compliance Profiles
5. Compliance Reports
6. Applying Compliance Frameworks using InSpec
7. Overview of using Compliance with Delivery?
8. Additional Resources
