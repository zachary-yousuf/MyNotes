#Installation procedure

For more details go to https://wiki.archlinux.org/index.php/Installation_guide

Now we will start the installation procedure:
1. set the system time using the following command:
	* timedatectl set-ntp true

2. Now we need to prepare the hard disk for the installation of the Linux, for that we need to create the partion.
	* $ lsblk and identify the hard disk in which we are going to install the OS
	* $ fdisk /dev/sda   // sda - which is to updated as per the lsblk out
	* press "n" for new partition
	* press enter to select default partition numer
	* prss enter to select the default start location
	* enter +200M to allocate 200 MB for the first partion that will be used as the boot partion
	* Repeat the same steps for root partition and for the home partition
	* verify the partion by pressing "p" and once everthing is fine, press "w" to write the partion table

3. Once the partiton is done we need to make the file system using mkfs command as follows
	* mkfs.ext4 /dev/sda1
	* mkfs.ext4 /dev/sda2
	* mkfs.ext4 /dev/sda3

4. After creating the file system we need to mount above. To do that follow below command:
	* $ mount /dev/sda2 /mnt       ## this will mount the root partition to /mnt
	* we need to create two folder namely /boot and /home under /mnt so do the following:
		* mkdir /mnt/boot
		* mkdir /mnt/home
	* We then mount the above folders as follows:
		* mount /dev/sda1 /mnt/boot
		* mount /dev/sda3 /mnt/home

5. Once this is done we need to make the fstab so the above partitions are mounted automatically every time we boot the machine. for that run below command:
	* genfstab -U /mnt >> /mnt/etc/fstab

6. Now we are ready to install the linux for that run the following command:
	* pacstrap /mnt base base-devel linux linux-firmware vim
	* Wait till the installation is complete
7. We need to change from live USB to our actual system for that we need to use:
	* arch-chroot /mnt
8. Next step is to generate the locale, for that we will run the following commands:
	* vim /etc/locale.gen
	* uncheck the "#" for the lines which says " en_US" and save the file.
	* $ locale-gen 			## This will generate the locale
	* $ vim /etc/locale.conf and add the following:
		* LANG=en_US.UTF-8
	* save the file and close.
9. Now we need to set our local time, to do that:
	* ln -sf /usr/share/zoneinfo/Asia/Kolkata /etc/localtime
10. Set the hostname in "/etc/hostname" file
11. Change the password using "passwd" command for the root user
12. exit chroot using "exit" command
13. unmount all the partition using
    	* $ umount -R /mnt
14. Reboot the system
