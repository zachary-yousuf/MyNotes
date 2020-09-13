========Procedure for installing the KVM virtualization platform=======

Before starting the installation check in the bios whether virtualization is Enabled or not.
Also run the following command command and you are getting the output as "VT-x"
   LC_ALL=C lscpu | grep Virtualization

1. Run following command and install the necessary packages
   sudo pacman -S qemu virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat
   sudo pacman -S ebtables iptables
2. Now, enable the libvirtd services using following commands.
   sudo systemctl enable libvirtd.service
   sudo systemctl start libvirtd.service
3. Edit the libvirtd,conf file as follows,
   a. Run the following command
      sudo vim /etc/libvirt/libvirtd.conf
   b. Uncomment the following lines in the file.
      unix_sock_group = "libvirt"
      unix_sock_rw_perms = "0770"
4. Add the user to libvirt group using following command
      sudo usermod -a -G libvirt $(whoami)
5. Add new user group called libvirt using following command
      newgrp libvirt
6. Restart libvirt service using following command
      sudo systemctl restart libvirtd.service

For more details refer the following youtube video https://www.youtube.com/watch?v=t-VpMbWzPZI
Also refer the website https://computingforgeeks.com/complete-installation-of-kvmqemu-and-virt-manager-on-arch-linux-and-manjaro/
===========================================================================

=============Procedure for creating a virtual operating system=============
