# director-lab-undercloud

This ansible playbook is designed to install and configure an OpenStack (virtualized) Undercloud according to the Red Hat Director lab exercises.  It is therefore similar to (but not the same as) TripleO Quickstart, and is meant for use with internal Red Hat repositories.  The point is to automate the monotonous Undercloud installation and configuration so you can just focus on the Overcloud instead.

So what exactly does this do?  It...

1. Configures the target machine to use internal Red Hat repos needed for access to OSP and Director

2. Installs libvirt and associated tools on target machine

3. Pulls down a RHEL guest image from internal Red Hat repos

4. Creates a VM on target machine using aforementioned guest image as the disk

5. Installs TripleO on VM

6. Creates Undercloud config file on VM

7. Installs Undercloud on VM based on aforementioned config file

8. Pulls Overlcoud images from internal Red Hat repos and uploads them to Undercloud on VM

9. Performs miscellaneous operations in support of aforementioned steps and to prepare for manual deploy of Overcloud

Use:

1. Put target host machine IP in hosts file [vm-hosts] group

2. Set guest image and repo settings in group_vars/all

3. ansible-playbook -i hosts site.yml

I've seen some timing issues around acquiring the Undercloud VM's IP and when it can actually be reached via SSH.  If you see "unreachable" errors, you can just try running the playbook again.  If you do run the playbook again, it will reuse the images and the guest (if it got that far).  Should you want it to start from scratch, include "-e destroy_undercloud=true" in the command line.

This playbook targets OSP 8 by default.
