# chef-compliance-installation-configuration-operation
This repo is for development of the initial chef-compliance course

# Objectives:
After completing this course, you should be able to:

Install and initially configure the Chef Compliance server.
Perform scans with Chef Compliance.
Remediate compliance issues.
Schedule and run compliance reports.
Use InSpec to create, modify, and test Chef Compliance profiles.
Manage Users, Organizations, Teams and Permissions

Note: You should have attended at least Chef Essentials, Chef Fundamentals or have equivalent Chef experience prior to attending this course.


# Classroom Lab
The hands-on labs require the following infrastructure which should be provided by the instructor and specified in Appendix Z.

Two standard AWS Linux instances per student that use the same as the AMI used in Chef Essentials training but upgrade to ChefDk 0.10.x
We need to put the chef user in the dockerroot group and make /var/run/docker.sock's group dockerroot in the training image.
We need to build the shell init stuff for chef dk into the AMI images--the equivalent of 'echo 'eval "$(chef shell-init bash)"' >> ~/.bash_profile' then log out and in.

Students will install Chef Compliance on one instance and use the second Linux instance to run compliance scans against.

One Windows node per student to be used as a second target and as a virtual Windows workstation. The Windows node should use Sean's ami-ae1a4cc4 but with inspec preinstalled and the path to inspec added to the user's PATH variable (c:\Users\Administrator\AppData\Local\chefdk\gem\ruby\2.1.0\gems\inspec-0.9.7\bin\inspec)  ?
Something akin to this might set the PATH variable."chef shell-init powershell | Invoke-Expression" >> $PROFILE

Test Kitchen should be preconfigured to work on the Windows node too.

# Student Laptops

Each student will need their own laptop workstation with the same specs as for Chef Essentials training. The student laptops need to be able to ssh to Linux nodes and use HTTP to use the Compliance Server. The student's laptops should also have a Remote Desktop Client that supports RDP:

Windows 7 with Remote Desktop Connection

Mac OS X 10.11 (El Capitan) with Microsoft Remote Desktop

Ubuntu 12.04 with Remmina Remote Desktop Client


This course requires at least one Linux virtual workstation as stated above.

# Modules
1. Introduction
2. Installation
3. Running Scans, Remediation, and Testing
4. Running Scans on Windows Nodes
5. Creating Custom Profiles
6. Scheduling Scans and Running Compliance Reports
7. Applying Compliance Frameworks using InSpec
8. Users, Organizations, Teams, and Permissions
