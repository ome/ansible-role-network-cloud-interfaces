Network Cloud Interfaces
========================

Automatically initialise multiple network interfaces in a virtual machine.

This is intended for use with virtual machines running a standard cloud image where by default only the first NIC is initialised, and you wish to activate additional NICs.
All networks must have DHCP enabled.

This is not recommended for use on physical servers, use the `network` role instead.


Role Variables
--------------

- `network_cloud_interfaces`: A list of network interfaces to be added, default is to attempt to add all.
  Existing interfaces will not be modified, even if they are in this list.
- `network_cloud_interface_regex`: A regular expression used to match interfaces to be activated, default `.*`.
  An example use is on Docker servers where you want to ignore virtual interfaces.


Example playbook
----------------

    - hosts: cloud-instance
      roles:
      - role: network-cloud-interfaces
        network_cloud_interface_regex: '^eth.*'


Author Information
------------------

ome-devel@lists.openmicroscopy.org.uk
