# Chef Compliance: Installation, Configuration and Operation

This repo is a repository for developing Chef Compliance.

## Abstract / Description

The Chef Compliance Installation, Configuration, and Operation course is an instructor-led course covering the Chef Compliance solution. In this course you will learn how to install and initially configure the Chef Compliance server, perform compliance scans against Windows and Linux nodes, remediate compliance issues with Chef, and run Compliance reports.

In addition, you will learn how to use InSpec to create and modify Chef Compliance profiles and learn how to locate CIS (Center for Internet Security) and DoD (Department of Defense) compliance specifications that you can use to write Chef Compliance profiles. This course includes hands-on exercises to reinforce the material.

Prerequisite: You should have attended at least Chef Essentials, Chef Fundamentals or have equivalent Chef experience prior to attending this course.


##Objectives:

After completing this course, you should be able to:

* Describe the capabilities of Chef Compliance.
* Install and initially configure the Chef Compliance server.
* Perform scans with Chef Compliance.
* Remediate compliance issues.
* Use InSpec to create, modify, and test Chef Compliance profiles.
* Schedule and run compliance reports.
* Manage users, organizations, teams and permissions.

## Learner Requirements

Attendees need a network-enabled laptop with a terminal that supports SSH and a Remote Desktop Client that supports RDP.

* Windows 7+ with [Putty](http://www.putty.org/) or [Cygwin with OpenSSH](https://www.cygwin.com/) and with [Remote Desktop Connection](http://www.wikihow.com/Use-Remote-Desktop-in-Windows-7)

* Mac OS X 10.11 (El Capitan) with [Microsoft Remote Desktop](https://itunes.apple.com/us/app/microsoft-remote-desktop/id715768417?mt=12)

* Ubuntu 14.04 with [Remmina Remote Desktop Client](http://www.remmina.org/wp/)


It’s best that learners have some familiarity and comfort with the following:

* Chef Essentials or Chef Fundamentals or equivalent experience.

## Agenda

1. Introduction
2. Installation
3. Running Scans, Remediation, and Testing - Linux
4. Running Scans, Remediation, and Testing - Windows
5. Creating Custom Profiles
6. Applying Compliance Frameworks using InSpec
7. Scheduling Scans and Running Compliance Reports
8. Users, Organizations, Teams, and Permissions
9. Further Resources

## Published Content

The latest published version of these training materials are located as follows:

### Participant Guide

The participant guide is a PDF that contains the notes export from the content slides.

The content can be found here: CONTENT IS CURRENTLY IN DEVELOPMENT

### Instructor Kit

* All slides for each module

* Instructor Guide for you to learn from, practice with, and perhaps use as reference while teaching. The instructor guide contains the notes export from the content slides with additional instructor notes and lab setup instructions.

* Participant Guide

This content can be found here: CONTENT IS CURRENTLY IN DEVELOPMENT

### Screencast Videos

This content can be found here: NOT YET CREATED

### Publishing Process

How to export the content from [slides to guides](https://drive.google.com/file/d/0B4WmSTt8VtdKZDY5RnhIWVVYZkk/view?usp=sharing
) for Chef members.

## Known Issues

* Module 04 - At the current moment the version of InSpec (0.9.2) that ships with Chef Development Kit (ChefDK) and the Chef Compliance Server does not properly support Windows. To complete the Group Lab defined in this module you will need to update both versions of InSpec

Login to the Compliance Server and run the following:

```
$ sudo /opt/chef-compliance/embedded/bin/gem install inspec -v 0.10.1
```

Login to the Windows Node and run the following:

```
$ gem install inspec -v 0.10.1
```
* Module 05-creating-custom-profiles is under construction so it will support ChefDK  0.11.2 (which includes inspec 0.14.2) . inspec 0.14.2 changes module 05-creating-custom-profiles to use `inspec init profile` and the new `inspec compliance upload'.

## Environment

These modules focus on getting learners engaged with the content as quickly as possible. Details on setting up these instances can be found in Appendix Z in the Instructor Kit.

### Amazon Machine Instances

This content requires the attendee to have 2 Linux Nodes and 1 Windows Node.

* Compliance - CentOS 6.7 - 1.0.3 (ami-0d6f4267)

* Compliance - Windows 2012 - 1.0.0 (ami-0af8d260)

> The CentOS AMI was generated with the following [ChefDK Image Project](https://github.com/chef-training/chefdk-fundamentals-image). The Windows AMI was generated manually based on scripts found in the the [ChefDK Image Project](https://github.com/chef-training/chefdk-fundamentals-image). If you would like access to this AMI to deliver training please contact [training@chef.io](mailto:training@chef.io) the request that includes your Amazon Account Id.

### Creating the Linux Instance

> An chef recipe that automates the creation of the workstation can be found in the [ChefDK Image](
https://github.com/chef-training/chefdk-image/blob/master/cookbooks/workstations/recipes/compliance.rb) project

* Installation of ChefDK

* Create a user named 'chef' with the password 'chef'

* Ensure the yum package repository is up-to-date

```
$ yum update -y
```

* INSTALL various editors and tools that the attendee will install: vim; emacs; nano; tree; and git.

* Install [Docker on CentOS](https://docs.docker.com/engine/installation/centos/)

* Allow Password Authentication

* Disable the iptables service

* Disable SELINUX

* Added an ec2 json hints file (content: `{}`) to `/etc/chef/ohai/hints/ec2.json`


### Creating the Windows Instance

The AMI was generated with the following actions:

> NOTE: The creation of the image is a manual process of executing a number of steps and then saving that current working instance as an image.

* [Change](https://support.managed.com/kb/a472/how-to-change-the-administrator-password-in-windows-server-2003-2008-r2-or-2012.aspx) the Administrator's password to "Cod3Can!"

* Enable PowerShell Script Execution

```
Set-ExecutionPolicy RemoteSigned
```

* Installed the basic components through the Nordstrom's ChefDK bootstrap script

```
(Invoke-WebRequest -Uri https://raw.githubusercontent.com/Nordstrom/chefdk_bootstrap/master/bootstrap.ps1).Content | Invoke-Expression
```

* Installed the Atom FoodCritic Linter
* Installed the Atom Rubocop Linter

* Added an ec2 JSON hints file (content: `{}`) to `C:\chef\ohai\hints\ec2.json`

* Write a `kitchen-template.yml` to the "\\Users\\Administrator" that contains the following [content](https://github.com/chef-training/chef-essentials-windows/blob/master/kitchen-template.yml).

* Install the kitchen-ec2 gem

```
chef gem install kitchen-ec2
```

* Add `C:\opscode\chefdk\embedded\bin` to the PATH.

```
$LocalMachinePathRegKey = 'HKLM:\System\CurrentControlSet\Control\Session Manager\Environment'
$ChefDkEmbeddedBin = 'C:\opscode\chefdk\embedded\bin'

Push-Location
Set-Location $LocalMachinePathRegKey
$CurrentPath = (Get-ItemProperty . Path).Path
$PathWithInSpec = "$CurrentPath;$ChefDkEmbeddedBin"
Set-ItemProperty . -Name Path -Value $PathWithInSpec
Pop-Location
```

* Update the Version of InSpec to a known working version

```
Invoke-Expression "chef gem install inspec -v 0.10.1"
```

* Enable remote administration via WINRM

```
# WinRM
write-output "Setting up WinRM"
write-host "(host) setting up WinRM"

cmd.exe /c winrm quickconfig -q
cmd.exe /c winrm quickconfig '-transport:http'
cmd.exe /c winrm set "winrm/config" '@{MaxTimeoutms="1800000"}'
cmd.exe /c winrm set "winrm/config/winrs" '@{MaxMemoryPerShellMB="1024"}'
cmd.exe /c winrm set "winrm/config/service" '@{AllowUnencrypted="true"}'
cmd.exe /c winrm set "winrm/config/client" '@{AllowUnencrypted="true"}'
cmd.exe /c winrm set "winrm/config/service/auth" '@{Basic="true"}'
cmd.exe /c winrm set "winrm/config/client/auth" '@{Basic="true"}'
cmd.exe /c winrm set "winrm/config/service/auth" '@{CredSSP="true"}'
cmd.exe /c winrm set "winrm/config/listener?Address=*+Transport=HTTP" '@{Port="5985"}'
cmd.exe /c netsh advfirewall firewall set rule group="remote administration" new enable=yes
cmd.exe /c netsh firewall add portopening TCP 5985 "Port 5985"
cmd.exe /c net stop winrm
cmd.exe /c sc config winrm start= auto
cmd.exe /c net start winrm
```
