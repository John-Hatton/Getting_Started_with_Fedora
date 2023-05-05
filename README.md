#
Getting Started With Fedora

---

## Introduction


---

## Changing Hostname 

To change the Hostname of the newly installed machine, please do the following:

	hostnamectl status
	sudo hostnamectl set-hostname <new-hostname>

---

## Setting Static IP, Gateway, and DNS Servers

Fedora uses nmcli for this. We will do a nmcli connection show to determine the UUID of the 
interface, and then we change the connection properties using this UUID

	nmcli connection show
	sudo nmcli connection modify <UUID> IPv4.address <static-ip> IPv4.gateway <gateway> IPv4.dns "<dns1>, <dns2>"

For best results, perform a reboot at this step.

---

## Enable SSHD

To Enable ssh do the following:

	sudo systemctl enable sshd
	sudo systemctl start sshd

---

## Setup VIM as Default Editor

In order to setup VIM as the default editor, we will need to edit the .bashrc file.

Append the file with the following lines:

    export EDITOR=/usr/bin/vim

Then to get vim working the way I like it, append the following to the .vimrc file:

    syntax on
    colorscheme slate
    autocmd FileType go setlocal noexpandtab tabstop=4 shiftwidth=4 softtabstop=4
    let g:go_fmt_command = "goimports"


---


## Add XRDP to Login from Windows

In order to add XRDP, you will need to do the following:

    sudo dnf install xrdp
    sudo systemctl enable xrdp
    sudo systemctl start xrdp

Provided you've added the static-ip to the DNS server already, it should be resolvable by now. 
This means, from Windows, we can simply give the hostname, and we can remote in via RDP!

---

## Update Console Output


To get things looking a bit more fresh, you will want to do the following:


    oldps1 = $PS1
    PS1="\e[0;31m\W>:"
    echo $PS1

If by accident the original is lost, and you would like to set it back:

    export PS1="[\u@\h \W]\$"

Namaste.
=======
## Installing DEV Tools


### Installing Build Tools in Fedora

The first step is getting everything ready to build and compile. For this, we can include 
everything we could ever need with:

    sudo dnf group install "C Development Tools and Libraries" "Development Tools"

Et voilà!

---

