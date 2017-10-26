# Zimbra
In this Repository you will find different Zimbra Scripts for install Zimbra Collaboration on an automated way

# ZimbraEasyInstall
##What is the ZimbraEasyInstall
This Script install and configures bind9 with the domain and IP that is defined while invoke the command. After that the Scripts prepare the keystroke script with a default installation of Zimbra Collaboration 8.6 (without dnscache) and the config.defaults script, using the domain, IP and password that is defined while invoke the command. Once everything is ready the Script download the latest version of Zimbra Collaboration 8.6, uncompress it and install it using the keystrokes script and the config script.

##Advantages of use the Script
 * Time saving
 * Fully automated
 * Easy to use
 * Good for a quick Zimbra Preview

##Usage and Example
The ZimbraEasyInstall Script is an easy way to install Zimbra Collaboration, without be worry of the DNS configuration, OS depencies, etc. Just execute it and after a few minutes have Zimbra up and running.

Just run the Script adding the TLD domain for your Zimbra Collaboration server, the IP of the DNS server (usually will be the same of the server, but instead you are using different eth interfaces), and add the password for the Zimbra Collaboration server.
```bash
./ZimbraEasyInstall zimbralab.local 192.168.211.40 Zimbra2016
```
###Bind as a DNS Server###
You can now choose if you want dnsmasq or bind for your DNS Server with ZimbraEasyInstall, by default if you don't select anything after the password, it will automatically install dnsmasq, if you add the flag bind, then it will install bind before ZCS:
```bash
./ZimbraEasyInstall zimbralab.local 192.168.211.40 Zimbra2016 bind
```
##Access to the Web Client and Admin Console
The Script will take care of everything and after a few minutes you can go to the IP of your server and use the next URL:
 * Web Client - https://YOURIP
 * Admin Console - https://YOURIP:7071

## ZimbraEasyInstall-87
If you want to deploy the new ZCS 8.7.1, now you can, with the new Script ready for ZCS 8.7.x, which also detect if you are in Ubuntu 14.04 or 16.04 and install the proper version depending the OS
##Usage and Example
The ZimbraEasyInstall Script is an easy way to install Zimbra Collaboration, without be worry of the DNS configuration, OS depencies, etc. Just execute it and after a few minutes have Zimbra up and running.

Just run the Script adding the TLD domain for your Zimbra Collaboration server, the IP of the DNS server (usually will be the same of the server, but instead you are using different eth interfaces), and add the password for the Zimbra Collaboration server.
```bash
./ZimbraEasyInstall-87 zimbralab.local 192.168.211.40 Zimbra2016
```
##Access to the Web Client and Admin Console
The Script will take care of everything and after a few minutes you can go to the IP of your server and use the next URL:
 * Web Client - https://YOURIP
 * Admin Console - https://YOURIP:7071
 
## ToDo
- [ ] Prepare and configure automatically the Reverse DNS Zone
- [ ] Make it multi-platform to use it in CentOS/RedHat, Suse and Ubuntu 12.04
- - [x] CentOS/RedHat, Suse and Ubuntu 12.04
- - [ ] Suse
- - [ ] Ubuntu 12.04
- [ ] Make it Multi-Server, to install in each server only the rol that selects (LDAP, Mailbox, MTA, PROXY, UI)
- [x] Have the option to select Bind, dnsmasq, or external DNS
- [ ] Have the option to select the Timezone, the default one is Los Angeles
