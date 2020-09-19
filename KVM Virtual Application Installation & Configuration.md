#Procedure for installing the KVM virtualization platform

Before starting the installation check in the bios whether virtualization is Enabled or not. Also run the following command command and you are getting the output as "VT-x"

LC_ALL=C lscpu | grep Virtualization
Run following command and install the necessary packages
sudo pacman -S qemu virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat
sudo pacman -S ebtables iptables
Now, enable the libvirtd services using following commands.
sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
Edit the libvirtd,conf file as follows, a. Run the following command
sudo vim /etc/libvirt/libvirtd.conf b. Uncomment the following lines in the file.
unix_sock_group = "ibvirt"
unix_sock_rw_perms = "0770" G4. Add the user to libvirt group using following command
sudo usermod -a -G libvirt $(whoami)
Add new user group called libvirt using following command
newgrp libvirt
Restart libvirt service using following command
sudo systemctl restart libvirtd.service
Now create a new network bridge as follows:
Create a new file as br10.xml
copy following content to it ===================================================== br10
====================================================== * Execute following command: * sudo virsh net-define br10.xml * sudo virsh net-start br10 * sudo virsh net-autostart br10
For more details refer the following youtube video

https://www.youtube.com/watch?v=t-VpMbWzPZI

Also refer the following websites:
https://computingforgeeks.com/complete-installation-of-kvmqemu-and-virt-manager-on-arch-linux-and-manjaro/
https://kifarunix.com/how-to-fix-qemu-kvm-not-connected-error-on-ubuntu-20-04/
===========================================================================

###Procedure for creating a virtual operating system

Run virt-manager from dmenu
Click on "Create new virtual machine"
In the option select "Local install media(iso image or CDROM) and click forward button
In the next window, browse for the ISO file. Which will popup another window, in which add the "Downloads" directory using the "+" which is present in the left bottom, Give name for the folder. Now the available ISO files in the Download directory will be listed on the right side.
Now select the required ISO and click choose volume.
Give the operating system name if not selected automatically and click forward
Now allot the RAM and CPU and click forward
Allot the hardisk for the new virtual machine and click forward
If the default hard disk is not you can create a custom storage.
In the next window it show the setting that is selected for the virtual machine. check and verify
Also tick the customize configurarion before install check box and select the network and click finish
In the setting select the following:
Under overview, for firmware, select UEFI x86_64: /usr/share/edk2-ovmf/x64/OVMF_CODE.secboot.fd
Under boot option, enable boot menu and enable CDROM and move it to the top priority
Under Video QXL, select Virtio and enable 3d acceleration
Now we can begin the installation by clicking "Begin Installation"
===========================================================================
