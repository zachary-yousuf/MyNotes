#==Post Arch Installation==

1. Create new user and add to sudoer list
	* $ useradd -mG wheel zachary
	* $ passwd zachary and provide the password
	* $ sudo vim /etc/sudoers and uncomment the line which syats "%wheel ALL=(ALL) ALL"
2. Do the system update and upgrade using "sudo pacman -Syu"
3. Install "yay"
4. Add multilib repository, to do that edit /etc/pacman.conf file and uncomment following line:
	1.
