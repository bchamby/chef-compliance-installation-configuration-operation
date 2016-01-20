# Changelog for Chef Compliance

## 2016-01-19

Changes made by Nathen in preparation for a Compliacne Workshop at a pop-up event.

### 01-intro

* Add another objective to the course, participants will be able to describe the capabilities of Chef Compliance.
* List '...create, modify, and test...' without an extra 'and'
* Oxford comma for pre-built profiles
* Do not mention Serverspec.  It should be in the instructor notes and the instructor should be ready to answer questions about it.  Learners who have no experience with Serverspec may be confused by the reference.
* Show some sample InSpec when describing it.

### 02-install

* An updated empty Compliance dashboard screen shot

### 03-initial-configuration-scans

* An updated screen shot of adding a node
* Add a period after 'Log into your target node.'
* Leave the 'environment' field blank, a 'default' environment will be automatically created.
* Adjust the arrow pointing at the base/ssh compliance profile
* Update screen shot in Scan Results
* Change the header of the slide for creating the cookbooks directory
* Specify that the template command is creating an 'SSH Config Template'
* Update the impact of the 'ssh-4' rule, 1.0, not 3.0
* Update the screen shot of the ssh compliance rule
* Hide the InSpec verifier slides.  It doesn't work with Docker, why show it?
* Re-run `inspec exec` after re-converging the kitchen.  This way we verify the remdiation before applying it
* Spell out 'command line interface'

### 05-creating-custom-profiles

* Add a missing period to the first objective
* Update objective:  'Use InSpec...' not 'Using InSpec...'
* Spell out 'command line interface'
* Change the header of the slide for creating the profile directory
* Change the header of the slide when creating the metadata.rb file, use 'Create' instead of 'Creating'
* Downloading the zipped profile and uploading it are two different objectives
* Align the output of the zip command
* Correct the title of the slide when re-scanning the node 'Scan Your Node' instead of 'Upload the Profile to Chef Compliance'
