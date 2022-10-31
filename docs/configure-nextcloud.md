# Configuring Nextcloud

Nextcloud has multiple configuration files which define how the program works.  First, however, we can configure it from the internet.

## Basic setup  


Open firefox to the page with this command:  
                `~$ firefox localhost`  

Make a username and password, and **don't forget them!**

Click `install` and wait a couple minutes for the installation to complete.  

Next, Nextcloud will ask you if to install recommended apps.  If they look like something you may use, go ahead.  Otherwise, click `cancel`.  You can always install these later. 

Congrats, you have a successful Nextcloud installation!  There are a lot of settings that must be changed from the terminal, but feel free to look around your new cloud file sharing site before you dive into the next step.  You will see a place for images and files in the top left, and your icon and a settings dropdown in the top right.

### PHP Memory Setting

We should configure PHP first in order to maximize performance.  Exit out of firefox, and open the terminal again.  

Increase the amount of memory PHP can use.  512 megabytes is the recommended (use `512M`, M for megabytes (default is 128)).  You can raise this if your computer has a lot of memory, but be careful to not go near or over the actual memory in the computer.  Replace `<MEMORY_LIMIT>` with your desired memory (ex `512M`).  
                `~$ sudo snap set nextcloud php.memory-limit=<MEMORY_LIMIT>`

## HTTPS/SSL

This next step is important to provide secure yet easy access to your nextcloud instance on the go.  There are multiple ways to go about this.  If you have a multi-user use case or need to access your server outside of your home wifi, you need a hostname.  Get one at [freedns.afraid.org](https://freedns.afraid.org).




<!--
### Option 2: Using your user computer
First, from your **user computer** find your ip address using [this guide](https://mashable.com/article/how-to-find-your-ip-address).  Then run this command in your **server computer**:
                `~$ sudo nextcloud.occ config:system:set trusted_domains 1 \
    --value=<YOUR_IP>`  

Next, we need to know the **server computer** ip address to open the site.  Run this to get the address:  
                `~$ hostname -I | awk '{print $1}'`

Now, in your **user computer**, open a browser and navigate to the IP address you found in the previous step.  You should see an account creation page. --->