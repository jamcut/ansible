# Ansible Attack Repo
I have been hearing about Ansible for a while now, so I decided to check it out.  This repo is the result.  Mostly geared towards configuring boxes for red team stuff.

## configure_attack_box.yml
This is a playbook that will bootstrap a new attack system from a fresh install.  There are a few things to note:
- I have only tested this on Ubuntu 14.04 (LTS)
- The VM I used for testing had 4GB memory
- The Metasploit install is built using [Omnibus](https://github.com/rapid7/metasploit-omnibus)
  - In order to get the correct version of Ruby I installed v2.1 from a repo maintained by [Brightbox](https://www.brightbox.com/docs/ruby/ubuntu/) 
  - I was not able to install the necessary gems as an underprivileged user, so MSF has to be run with sudo using this method.

## More to come...
