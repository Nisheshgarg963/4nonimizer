# 4nonimizer
A script which helps to become anonymous..!!
      
![4nonimizer logo](./images/logo.png)  


### I like the 4nonimizer, please help us with whatever you want!   


# What is 4nonimizer?

It is a bash script for anonymizing the public IP used to browsing Internet, managing the connection to TOR network and to different VPNs providers (OpenVPN), whether free or paid. By default, it includes several pre-configured VPN connections to different peers (.ovpn files) and download the credentials (if the corresponding provider support it). Also, it records each used IP that we use every 300 seconds in log files.

This script is enabled as a service in systemd systems and uses a default vpn (VPNBook) at system startup.

Since version 1.06 the dns resolution requests are done throught DnsCrypt (enable and disable with option enable_dns or disable_dns)

# Attention VPN Providers!  

If you are a provider, you support OpenVPN and want your VPN to be integrated into 4nonimizer contact the developers at hackplayers @ ymail.com.


# Installation 

Download the repo using git, execute the command **./4nonimizer install** in the directory, and follow the screen instructions, 4nonimizer will move to the directory **/opt/** and installed as a service.

This script has full compatibility with Kali Linux, although it has been properly tested and should also work on other distributions like Debian, Ubuntu and Arch (Manjaro). However there could be some bugs, or unexpected performances (please comments if you find any!).

# Options

Once installed 4nonymizer, enter the command **4nonimizer help** to get the help, which shows all the available parameters:

           ___                   _           _
          /   |                 (_)         (_)
         / /| |_ __   ___  _ __  _ _ __ ___  _ _______ _ __
        / /_| | '_ \ / _ \| '_ \| | '_  ` _ | |_  / _ \ '__|
        \___  | | | | (_) | | | | | | | | | | |/ /  __/ |
            |_/_| |_|\___/|_| |_|_|_| |_| |_|_/___\___|_|
                                             By Cyb3rCop (Nishesh)
                                           Version: 1.06-beta

Usage: 4nonymizer **\<parameter\>**  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**install**:  Install the script in run services  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**uninstall**: Disable run service and remove app directory  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**change_provider**: Change VPN Provider  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**change_ip**: Change IP from VPN current  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**vpn_status**: Check IP and provider VPN running  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**update_vpns**: Update all ovpn of VPNs  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**start**: Init the 4nonimizer service  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**stop**: Stop the 4nonimizer service  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**stop_nonet**: Stop the 4nonimizer service and shutdown network interfaces  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**restart**: Restart the 4nonimizer service  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**update_app**: Update this program via git  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**privoxy**: Install and configure privoxy with port 8118 (BETA)  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**proxychains4**: Install and configure proxychains4 for default in the system  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**browser**: Fire up a firefox browser with profile privoxy -> tor  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**test_availability**: Check peers availability and delete ovpn file if the IP/service is unreachable  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**location**: Now you can select a specific country or continent of the vpn peer  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**enableboot**: You can enable service in boot  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**disableboot**: You can disable service in boot  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**enable_dnscrypt**: Enable dnscrypt service  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**disable_dnscrypt**: Disable dnscrypt service    
  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**help**: Help (this screen)  


# Available VPNs

Currently it supports the following VPN providers:

\- HideMyAss <https://www.hidemyass.com/>

\- TorGuard <https://torguard.net/>

\- VPNBook (by default) <http://www.vpnbook.com/>

\- VPNGate <http://www.vpngate.net/en/>

\- VPNMe <https://www.vpnme.me/>

\- VPNKeys <https://www.vpnkeys.com/>

\- FreeVPN <https://freevpn.me/>

\- TunnelBear <https://www.tunnelbear.com/>

\- Cryptostrom <https://cryptostorm.is/>

\- PIA <https://www.privateinternetaccess.com/>

\- SlickVPN <https://www.slickvpn.com>  

\- 7Proxies <https://www.7proxies.com/>  

\- StrongVPN <https://strongvpn.com/>  

\- NordVPN <https://nordvpn.com>  

\- Vyprvpn <https://www.goldenfrog.com/es/vyprvpn>  

\- ExpressVPN <https://www.expressvpn.com>  

# Install a new VPN

To install an additional vpn we have to use the following structure in order to the 4nonimizer be able to integrate and perform operations with it.

First, we have to create the following dir structure **/vpn/** within 4nonimizer path:

![Alt text](./images/tree.png)

In our example we create the folder **/vpntest/** and within it placed all **.ovpn** files we have. If the files ovpn not have the certificate within each of them we put in the same folder as shown in the example **certificate.crt**.

In addition, we must place a file named **pass.txt** containing 2 lines: the first one with the username and the second one with the password, as shown below:

![Alt text](./images/pass.png)

If we have correctly performed all steps when we execute the command **4nonimizer change_provider** the menu will show our vpn:

![Alt text](./images/change_provider.png)

As you can see in the picture, option [7] it is the vpn we've created.

# Getting credencials and ovpn files automatically

If the VPN provider allows automation of credential and/or .ovpn files getting, 4nonimizer has standardized the following scripts names and locations:

\- /opt/4nonimizer/vpn/provider/**vpn-get-pass.sh**

![Alt text](./images/autopass_sample.png)

\- /opt/4nonimizer/vpn/provider/**vpn-get-ovpn.sh**

![Alt text](./images/autovpn_sample.png)

4nonimizer automatically detect the presence of both scripts and indicate (Auto-pass Login) or (Auto-get OVPN) if it finds in the first line of each file the expression '#4uto' or '#m4nual' depending on the performed actions.

![Alt text](./images/provider_new.png)


# Extras

\- Execute 'source 4nonimizer' to activate autocompletation of parameters.  
\- Copy .conkyrc in your home directory to load a 4nonimizer template and execute conky.  


# Versions

 Number | codename | date  
 --- | --- | ---  
 1.00-beta | .bye-world! | 5/10/2016    
 1.02-beta | .evol-time  | 11/10/2016   
 1.03-beta | .using-latin-i | 17/10/2016 
 1.04-beta | .locateit | 22/12/2016
 1.05-beta | .encrypting | 03/01/2017  
 1.06-beta | .1st-trial | 18/01/2017  
 
¡4nonimize the world!

