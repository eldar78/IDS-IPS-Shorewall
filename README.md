# IDS-IPS-Shorewall
Secure your VPS with IDS/IPS

First Install Shorewall 
sudo apt-get install shorewall -y

nano -w /etc/default/shorewall

Change

startup = 0
to
startup = 1

save, and exit.
