This is a playbook to tune the BIOS settings of a Dell server for VMware vSphere. Mainly, it gives the CPU Power Management into the control of the Hypervisor.

Tested with ansible 2.7.4 and Dell PowerEdge R740xd but should also work for other 14th generation (and maybe even 13th generation) PowerEdge servers.

See it at work with `asciinema play ansible-dell-bios.cast`.

**Important note:** Since ansible 2.7.2, CreateBiosConfigJob schedules a BIOS configuration job for the next reboot. If you use 2.7.0 or 2.7.1, ansible will reboot your server in order to reconfigure your BIOS!
