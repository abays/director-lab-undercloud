# director-lab-undercloud

This ansible playbook is designed to install and configure an OpenStack (virtualized) Undercloud according to the Red Hat Director lab exercises.  It is therefore similar to (but not the same as) TripleO Quickstart, and is meant for use with internal Red Hat repositories.  The point is to automate the monotonous Undercloud installation and configuration so you can just focus on the Overcloud instead.

Use:
1. Put target host machine IP in hosts file [vm-hosts] group
2. Set guest image and repo settings in group_vars/all
3. ansible-playbook -i hosts site.yml

I've seen some timing issues around acquiring the Undercloud VM's IP and when it can actually be reached via SSH.  If you see "unreachable" errors, you can just try running the playbook again.  If you do run the playbook again, it will reuse the images and the guest (if it got that far).  Should you want it to start from scratch, include "-e destroy_undercloud=true" in the command line.

This playbook targets OSP 8 by default.
