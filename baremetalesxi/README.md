This playbook creates a custom ESXi ISO including a kickstart file to configure networking, boots the server with it and installs ESXi. Tested with ansible 2.9 and Dell PowerEdge R740xd with a BOSS card but should also work for other 14th generation PowerEdge servers and, hopefully, with later ansible versions. If you don't have a BOSS card you would need to change `--firstdisk="DELLBOSS VD"`, for example to `--firstdisk=local`.

Inspired by [baremetalesxi](https://github.com/bryansullins/baremetalesxi) but I'm using [GNU xorriso](https://www.gnu.org/software/xorriso/) to create the ISO instead of mkisofs.

What you need:
* An ESXi install ISO in `iso` (I'm using VMware-VMvisor-Installer-7.0U2-17630552.x86_64.iso here)
* `GNU xorriso`
* A web server (I'm using Apache here with `DocumentRoot "/data/www"`)
* The playbook assumes you are not root, so your user needs permissions to write files to /data/www/iso/ and also to start and stop the web server via sudo without a password

If you use a different install ISO you have to:
1. Extract `boot.cfg` or `efi/boot/boot.cfg` from it (they seem to be identical, at least in the ISO I'm using)
1. Copy it to `files/`
1. Change `kernelopt=cdromBoot runweasel` to `kernelopt=runweasel ks=cdrom:/KS.CFG`
