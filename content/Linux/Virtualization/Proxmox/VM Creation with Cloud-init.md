
**Link**: [[Proxmox]]

Cloud-init is a package that configure the OS in the very first boot. You download to pre-packaged .qcow2 image (from Debian for example), import it as the main disk. 

Then, you add the cloud-init disk, which is a small disk that holds the configuration parameters like hostname, ssh keys etc.


## VM Creation
- In OS, select "Do not use any media"
- In disks, remove all disks
- After creation, remove CD/DVD drives
- Add cloudinit drive (This drive is a small IDE drive that only holds your configuration parameters like hostname, ssh keys etc. Set as default, you can put to local)
- We will use a cloud image instead of a disk. We will import the .qcow2 image, resize it, and use it as the main OS drive in SCSI format.
#### Cloud image
A cloud image is a pre-made virtual machine disk that is ready to use and designed to be automatically set up using cloud-init when it starts.

Suggested to download via CLI to the location `/var/lib/vz/template/vm_disks`.

### Installation Steps
1. `qemu-img resize cloudimg.qcow2 20G` : This resizes the disk for appropriate use. This is not the actual disk size, just the virtual size. It means the disk can grow up to 20G.
> You can use `qemu-img info cloudimg.qcow2` to check its size and other info

2. `qm importdisk <vm_id> cloudimg.qcow2 local-lvm` : This import the disk to the template you will create. You can specify the location changing the local-lvm. This is the location I use for my VM disks and storage. This will copy the cloud image, turn it into a bootable disk, and attach to the VM

3. In GUI, go to template and Hardware. It will show Unused Disk. Edit and add it

4. Disable network boot via Options > Boot order

5. Convert into a template

Then you can edit cloud-init options.
You might also wanna change /etc/hostname




---
Then, you can convert this VM to the template: [[VM Template & Cloud-init]]