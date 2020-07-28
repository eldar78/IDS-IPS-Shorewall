# IDS-IPS-Shorewall
Secure your VPS with IDS/IPS



First Install Shorewall 
sudo apt-get install shorewall -y
#################################
nano -w /etc/default/shorewall

Change

startup = 0
to
startup = 1

save, and exit.



Setting Shorewall

The program will not start unless you change the shorewall configuration file /etc/shorewall/shorewall.conf .You can do this in following way:
nano /etc/shorewall/shorewall.conf

Change the first line from

STARTUP_ENABLED=No
to
STARTUP_ENABLED=Yes

Save and Exit


Turning on Forwarding

Finally we get to the last necessary file, /etc/shorewall/shorewall.conf. This file manages global shorewall options, and you should read it through completely.
nano -w /etc/shorewall/shorewall.conf

We need to find the section of the file that talks about "IP_FORWARDING" and change it from "Off" to "On". If you don't, your packets won't be able to get from one interface to the other.
IP_FORWARDING=On

Save and Exit



Checking Your Configs and Starting Shorewall
shorewall check

Starting Firewall
systemctl start shorewall

Enabling service of shorewall firewall
systemctl enable shorewall




Newx we need to to this

 Next create or edit sudo nano /etc/shorewall/interfaces
 
 #eth0 is your network device (usualy)
 
 
#ZONE   INTERFACE       BROADCAST       OPTIONS
net     eth0            detect          tcpflags,logmartians,nosmurfs
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

Save and Exit

Next create or edit sudo nano /etc/shorewall/policy 
#add this lines

#SOURCE		DEST		POLICY		LOG LEVEL	LIMIT:BURST
fw              all             ACCEPT
net             all             DROP            info
 
#The FOLLOWING POLICY MUST BE LAST
all             all             REJECT          info
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

Save and Exit

Next create or edit sudo nano





