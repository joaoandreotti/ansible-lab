# ansible-lab

## About
Based on a Red Hat article on how to [Build a lab in 36 seconds][1] with ansible, I created this derivation.
My motivation was that the article is using a Fedora Cloud qcow2 image, and I want to build my own.
My goal was to create a base qcow2 image based on Fedora Workstation to later create clones of this image into isolated test environments.

## How
I created two roles, one for the base image, which is heavily based on the article, but with a twist. Instead of getting the cloud image, it'll make a netinst boot of fedora, using a template kickstart file.
I used [Example article on kickstart][2], and [Red hat documentation on using unattended installs][3] as a reference to use a kickstart file with libvirt.
To build the kickstart file it was a mix using the [ImageFactory Fedora documentation][4] and [Libosinfo database][5].
Both [ImageFactory][6] and [Libosinfo][7](virt-install [options] --unattended) are alternatives to do what I did.

Then, creating the derivative image was rather easy using [virt-clone][9] and [virt-customize][8] tool.

[1]: <https://www.redhat.com/sysadmin/build-VM-fast-ansible> "Build a lab in 36 seconds"
[2]: <https://www.cyberciti.biz/faq/kvm-install-centos-redhat-using-kickstart-ks-cfg/> "Example article on kickstart"
[3]: <https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/sect-guest_virtual_machine_installation_overview-creating_guests_with_virt_install> "Red hat documentation on using unattended installs"
[4]: <https://docs.stg.fedoraproject.org/en-US/fedora-server/tutorials/imagefactory/> "ImageFactory Fedora documentation"
[5]: <https://gitlab.com/libosinfo/osinfo-db/> "Libosinfo database"
[6]: <https://github.com/redhat-imaging/imagefactory> "ImageFactory"
[7]: <https://gitlab.com/libosinfo/> "Libosinfo"
[8]: <https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/sect-guest_virtual_machine_disk_access_with_offline_tools-using_virt_customize> "Virt-customize"
[9]: <https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/cloning-a-vm> "Virt-clone"
