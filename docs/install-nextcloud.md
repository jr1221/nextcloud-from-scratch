# Install Nextcloud

Now it is time to actually install Nextcloud.  We will be using the snap package for the sake of simplicity, a manual installation method is coming soon.  

### Enable snap
Snap is a controversial product, as the web backend is closed source and it provides extremely large downloads and slow startup times.  So Linux Mint disables it by default. However, it makes the task of installing nextcloud effortless, whereas a manual installation is sometimes troublesome even for expert users.  So, we will enable and install it.  
                `~$ sudo rm /etc/apt/preferences.d/nosnap.pref`  
                `~$ sudo apt update`
                `~$ sudo apt install snapd`

### Install nextcloud from snap
Run this to pull the nextcloud snap package and install it.  
                `~$ sudo snap install nextcloud`

There your go.  Nextcloud is installed.  Next we will configure it to meet your needs.
