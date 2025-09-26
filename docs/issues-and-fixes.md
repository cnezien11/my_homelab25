Set up issues and fixes

 Proxmox Web UI Not Reachable via Suggested IP

 Problem

After installing Proxmox VE, the system provided an IP address (https://192.168.x.x:8006) for accessing the web interface. However, when I was trying to reach this from another PC it failed because the address was unreachable.

 Root Cause:

Proxmox assigned itself an IP that didn't match my actual network/subnet. The suggested IP didn't route properly on my LAN after I checked. 

 Solution

1. I accessed the Proxmox terminal directly (on the ThinkCentre).
2. I used the `ip a` command to view current network interfaces.
3. I then manually edited the network config file after reading proxmox documention
4. On the proxmox terminal I used the command under to edit the network interface. 
   nano /etc/network/interfaces
5. And finally rebooted my pc.
6. After all of that, I was able to reach by proxmox Web UI using the new ip I assigned to my proxmox.


Lesson Learned:

Always double-check what subnet your Proxmox host is on after installation. Default IPs might not match your home network, especially if DHCP is disabled or inconsistent.
