# Configuring Nextcloud

[TOC]

Nextcloud has multiple configuration files which define how the program works.  First, however, we can configure it from the internet.

## Basic setup  


First, we need to know the **server computer** ip address to open the site.  Run this from the **server computer** to get the address:  
                `~$ hostname -I | awk '{print $1}'`

Run this command in your **server computer**, replacing <YOUR_IP> with the IP from the above command:
                `~$ sudo nextcloud.occ config:system:set trusted_domains 1 \
    --value=<YOUR_IP>`  

Now, in your **user computer**, open a browser and navigate to the IP address you found in the previous step.  You should see an account creation page.

Make a **strong** username and password, and **don't forget them!**

Click `install` and wait a couple minutes for the installation to complete.  

Next, Nextcloud will ask you if to install recommended apps.  If they look like something you may use, go ahead.  Otherwise, click `cancel`.  You can always install these later. 

Congrats, you have a successful Nextcloud installation!  There are a lot of settings that must be changed from the terminal, but feel free to look around your new cloud file sharing site before you dive into the next step.  You will see a place for images and files in the top left, and your icon and a settings dropdown in the top right.

### PHP Memory Setting

We should configure PHP first in order to maximize performance.  Exit out of firefox, and open the terminal again.  

Increase the amount of memory PHP can use.  512 megabytes is the recommended (use `512M`, M for megabytes (default is 128)).  You can raise this if your computer has a lot of memory, but be careful to not go near or over the actual memory in the computer.  Replace `<MEMORY_LIMIT>` with your desired memory (ex `512M`).  
                `~$ sudo snap set nextcloud php.memory-limit=<MEMORY_LIMIT>`

## HTTPS/SSL

This next step is important to provide secure yet easy access to your nextcloud instance on the go.  There are multiple ways to go about this.  If you have a multi-user use case or need to access your server outside of your home wifi, you need a hostname.  First, a quick PSA that this is not technically permissible to sone internet service providers.  It also leaves your server vulnerable, so please weigh these risks against the benefit of on-the-go access.  More technical VPN based access is possible, but is often challenging for new users.

### Obtaining a domain (free)
Get a hostname at [freedns.afraid.org](https://freedns.afraid.org).  Create an account then head over to Registry. In the list find a domain name interesting to you.  Click on the domain, then enter your subdomain. The subdomain is the first word before the `.`, so if the URL is `abc.moo.com` the subdomain is `abc`.  Under destination, enter the IP address that comes up when you search up whats my ip into another tab (any VPN service must be off).  Now enter the security code, and click save.

### Obtaining a certificate

A RSA certificate encrypts and secures your connection.  We must open the server to the internet so it can reach a certificate authority and obtain the RSA certificate for your new subdomain.  First, allow this connection.  Enter your URL as subdomain.domain.global, (example: abc.moo.com).  Do not put "https" or "www".
                `~$ sudo nextcloud.occ config:system:set trusted_domains 2 \
    --value=<YOUR_URL>`

Now we must expose the server to the internet.  Follow [this guide](https://www.softwaretestinghelp.com/how-to-open-ports-on-router/) to open ports 80 and 442 to the server.  The server IP address is the same one you discovered earlier with `~$ hostname -I | awk '{print $1}'`.

Check that you can access your Nextcloud site at your subdomain on the web.  

Now, lets enable HTTPS and get a Lets Encrypt cert.  Follow the instructions:
                `~$ sudo snap run nextcloud.enable-https lets-encrypt`

Reload the site, and there should be a lock next to the browser.

### Changing Ports

This is highly recommended, but not required.  Changing ports increases security and reduces legal and other risks.  First, go to your router and remove the port 80 forward.  Next, change the 443 port forward to a random number above 500, the higher the better (max 65,000).  Ensure it is not on [this list](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers).  Now update the server to that port.
                ~~$ sudo snap set nextcloud ports.https=<YOUR_PORT>`

Now, your server can be accessed at subdomain.domain.global:PORT (example with port 8443 https://abc.moo.com:8443).  Congrats, HTTPS is fully configured.  You must repeat this process every three months to keep your cert up to date, including moving ports back to 80 and 443 on both the router and the server.


## Upgrading

You should upgrade regularly in order to ensure you have the latest and most performant Nextcloud features.  You may also use the web interface to upgrade, however this command is easier to track progress and see failure messages.
                `~$ sudo snap run nextcloud.occ upgrade`

### Check for issues

Nextcloud contains a built in scanner and issue detection engine.  Open admin settings on the site (top right corner > administration settings), and click Overview.  Ignore messages related to phone and email, as those configurations are not covered in this guide.  Other issues can be easily googled to find helpful remedies.  
