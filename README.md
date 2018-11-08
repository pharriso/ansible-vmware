Basic example for deploying a RHEL VM in VMware from a template
=========

Create RHEL VM
------------

Build a new RHEL VM from latest RHEL7 ISO. No special considerations here as far as I know. I just used defaults.

Prepare VM to become a template
------------

* Disconnect any CDROM devices.
* Ensure VMware Tools is installed - open-vm-tools is provided in rhel-7-server-rpms repo
* Ensure perl is installed - this is needed for guest customisations such as injecting IP & hostname details.

Seal template
------------

View the following KB for details on sealing a VM for use as a template:

https://access.redhat.com/solutions/198693

For my test I:

* Removed any MAC or UUID info from /etc/sysconfig/network-scripts/ifcfg-* files.
* Ensure BOOTPROTO=dhcp and ONBOOT=yes are set in /etc/sysconfig/network-scripts/ifcfg-* files.
* Removed ssh host keys ... rm -rf /etc/ssh/ssh_host_*

Variables
------------

Variables are listed in the inventory file. Usernames and passwords should be secured with vault or similar.

