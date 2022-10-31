# Prepare your System

Once you have your server computer and user computer, plus your USB drive; you can get started here.  

### Remember, the server computer and USB drive will be wiped of all files, pictures, games, videos, etc.  Only use a spare computer and a spare USB drive you don't mind being committed to the project!

## Download, flash, and boot the ISO

In order to prepare the server computer for Nextcloud, it first must have Linux installed.  This is an alternative to Windows or MacOS that is free and developer friendly.  See more info [here](about.md), or continue on.

We will be using Linux Mint for this guide, but feel free to choose a different distro (debian based for the purposes of this guide) if you know what you are doing.  

### On the **user** computer: (the one that you are leaving alone)
1. Download the ISO file from [linuxmint.com](https://www.linuxmint.com/download.php).  There are three options presented. Choose from: 
   1. XFCE (Recommended for old or slow computers)
   2. Cinnamon (Recommended for faster computers)
   3. MATE
2. Download and install [balenaEtcher](https://www.balena.io/etcher/)
3. Open balenaEtcher:
   1. Click `flash from file` and choose the ISO file you just downloaded off of linuxmint.com
   2. Insert your USB drive, and select it as the target under `Select Target`
   3. **Ensure the USB drive has nothing important on it, it will be deleted**
   4.  Click `Flash!`
   5.  Remove the USB drive once balenaEtcher notifies you the flash was successful

### On the **server** computer: (the one you are wiping)
1. For MacOS computers, [follow these steps](https://www.ianmaddaus.com/post/refind/) to disable System Integrity Proection and install rEFInd, which allows Linux bootability
2. For all other computers, [follow these steps](https://www.makeuseof.com/tag/disable-secure-uefi-dual-boot/) to disable secure boot
3. Insert the USB drive and reboot the system.  MacOS users do nothing, Windows users hold down shift, escape, or F2 to reach the boot manager.  For both MacOS and Windows users: select the option that says EFI, Linux, Mint, or shows a pendrive or big penguin  
4. Wait for linux to boot.

Now, welcome to Linux Mint! You will find through the course of this guide that Mint is simple, fast, and usable.  Right off the bat you may notice it looks like Windows, and that is the goal.  It can serve as a perfect alternative to Windows.  So although the computer will be committed to Nextcloud, feel free to use it as you would a normal computer. 

## Install Linux Mint

### On the **server** computer:
1. On your new interface, head over to the bottom right corner and click on the two crossed arrows.  That will open the wifi menu, where you can select your network and input your password.  This is required before continuing.
2. On the top right of the desktop, click the little disk symbol marked install Linux Mint.  
3. Follow the steps regard language and keyboard.  Check off `add multimedia codecs` at that menu.  Once you get the the disk partition menu, select `wipe disk and install Linux Mint.`  As the installer warns you, all your data stored on the device will be gone.  (Advanced users:  You can manual partition for dual boot if they wish).
4. Follow the next steps, creating a password and selecting your timezone.  Then click install and sit back and relax.  This does take a while on older computers and computers with HDD drives.
5. Reboot the computer when the installer says it is complete, and make sure to remove your USB drive.

### Update Linux Mint
1. Boot into Linux Mint, either by waiting for the reboot or selecting it (macOS users).  Make sure your USB drive is unplugged.
2. Read the welcome screen, and feel free to change your personal appearance settings to your hearts desire.  You will find it is much more customizable than Windows or MacOS.  Make sure to `install additional drivers` but please **skip the update manager.**
3. In the bottom left corner, click the `lm` symbol.  Type in software sources, and find the yellow icon and open it.  Enter your password.
4. In the top middle of software sources, click on the URL that appears next to a flag of a country.  Wait a couple minutes for the computer to test the speed of multiple update servers.  This will give you the quickest update times from here on.  Once it has completed ranking servers in or around your area (you can scroll down), click the highest one on the list to get the same speed, than click ok.  Do the same process for the URL below the first one, next to `ubuntu:`
5. Click `OK` in the bottom middle green banner, and enter your password if needed.
6. Open up a terminal in the button left corner, by clicking the black box.  This is how you will enter commands from now on.  Commands in the guide will look like this:  
            `~$ the command here`
7. For the sake of making this guide easy to follow and duplicate, we will be using terminal commands for most tasks.  But, there is a graphic interface for most things, so really you can achieve the same things using the apps in Linux Mint.  To update linux mint, enter the commands below, making sure to hit `y` when prompted.  This will take a while as it is the first update.  
            `~$ sudo apt update`  
            `~$ sudo apt upgrade`

Alright, you have successfully installed Linux Mint, and are ready to install Nextcloud!

