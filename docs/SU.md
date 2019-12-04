# Tutorial Set Up

These tutorials are written for a linux operating system, specifically Ubuntu 18.04, with a [number of bioinformatic tools](APP_TOOLS.md) installed.

**Windows/Mac users** The easiest way to do the tutorials is to set up a virtual linux environment as described below. 
This will work for any laptop/computer whether it be a Windows or a Mac computer.

Otherwise, you can also install [the tools used](APP_TOOLS.md) in the tutorials on your Mac and download [the tutorial data](APP_DATA.md) yourself, if you want to. However, the install script provided below will (most likely) not work for Macs and you'll have to figure the installs out yourself.

<div style="background-color:lightyellow;border-radius:10px">
  {% octicon alert height:16 class:"right left" aria-label:hi %} If you are already working on Ubuntu 16.04 or 18.04 you can directly run the install script and download the tutorial data as described below. 
</div>


## Compute Requirements

To set up the virtual environment and do the tutorial I recommend a minimum of
* 40GB free disk space
* 4GB of RAM
* 4 CPU cores, i.e., a *Quad-core* processor as is found in most laptops

It will be possible to run the tutorial with half of the required specs but it will be slow and you will have to delete temporary files as you may not have enough free space to save all files at the same time.

<div style="background-color:lightyellow;border-radius:10px">
  {% octicon alert height:16 class:"right left" aria-label:hi %} You can install the virtual environment on a USB stick or external hard-drive in case you don't have 40GB on your computer to spare. An advantage is that you can take the tutorial with you and continue/finish it on another computer. However, make sure that the harddrive/stick has high read/write specs. Otherwise execution of the different commands may be very slow. 
</div>



## Virtual-Box-Set-Up


### 1. Download and install VirtualBox

To create the tutorial Environment first download the free software [VirtualBox](https://www.virtualbox.org/wiki/Downloads) as well as the *Expansion Pack*.

<img src="figures/VB_1.png" style="height:30%;">

After double-clicking VirtualBox installer follow the instructions on the screen to install.
The downloaded *Expansion Pack* will be used later.


### 2. Download Ubuntu 18.04 image

Next you will need a Ubuntu disk image that you can download for free from [here](https://ubuntu.com/download/desktop). After clicking the "Download" button just wait until the download starts and safe the file to your preferred location.

### 3. Create
