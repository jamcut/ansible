# Ansible Things Repo
I have been hearing about Ansible for a while now, so I decided to check it out.  This repo is the result.  Mostly geared towards configuring boxes for red team stuff.

## Installing Ansible
You can get Ansible from [the GitHub repo](https://github.com/ansible/ansible), but is is probably easier to just run <pre>pip install ansible</pre>

## Playbooks
### configure_attack_box.yml
This is a playbook that will bootstrap a new attack system from a fresh install.  Mainly, it installs software packages through apt, and some of the tools I use most commonly.  The idea for this is that a base VM can be created, then before each assessment, the user can run this playbook and install all of their needed tools.  After the assessment, the original snapshot can be restored. This saves the user valuable time that would normally be spent updating tools after reverting to a clean snapshot, or manually configuring a new VM before each assessment.  The playbook is modular, mainly consisting of includes from the "modules" directory.  Tools that are not desired can be skipped by commenting out the appropriate lines in the main yml file.  This playbook is currently functional, but there are a few things to note:
- Testing was conducted on a VM running Ubuntu 14.04 x64, with 4gb ram.
- Time for playbook to complete was just under one hour.
- The Metasploit install is built using [Omnibus](https://github.com/rapid7/metasploit-omnibus)
  - I had some serious problems getting RVM to install and getting the correct Ruby version running (I didn't try rbenv)
  - Eventually, in order to get the correct version of Ruby I installed v2.1 from a repo maintained by [Brightbox](https://www.brightbox.com/docs/ruby/ubuntu/)
  - I was not able to install the necessary gems as an underprivileged user, so MSF will likely have to be run with sudo because of this.  This would be necessary if you wanted to bind to a privileged port anyway.
In the future I may rework the playbook to assume the user will be running everything as root.

## To Do
- Continue to add tools and packages to the installer
- ~~Make the playbook modular consisting of multiple plays which can be run independently of each other~~
