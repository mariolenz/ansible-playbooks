!!! This is still work in progress !!!

This playbook creates a custom ESXi ISO including a kickstart file to configure networking, boots the server with it and installs ESXi. Tested with ansible 2.9 and Dell PowerEdge R740xd with a BOSS card but should also work for other 14th generation PowerEdge servers and, hopefully, with later ansible versions.

Inspired by [baremetalesxi](https://github.com/bryansullins/baremetalesxi) from [bryansullins](https://github.com/bryansullins) although I'm using [GNU xorriso](https://www.gnu.org/software/xorriso/) to create the ISO instead of mkisofs.
