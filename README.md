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


