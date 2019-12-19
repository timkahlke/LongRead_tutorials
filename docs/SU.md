# Tutorial Set Up

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](OV.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](SU_VB.md)

----
## Table fo Conternt

* [Set up VIrtual Box](SU_VB.md)
* [Install Ubuntu in your VirtualBox](SU_GA.md)
* [Add the VirtulaBox Guest Addition](SU_U.md)
* [Install the tools and packages needed](SU_I.md)
* [Download the tutorial data](SU_D.md)

----


These tutorials are written for a linux operating system, specifically Ubuntu 18.04, with a [number of bioinformatic tools](APP_TOOLS.md) installed. In case you don't work under Linux already, e.g. you have a Windows laptop, or don't want to install all the tools yourself this page gives detailed instructions on how to set up a tutorial environment on any computer using *VirtualBox*.

Setting up the environment is hopefully easy, definitely free and should not take longer than 60 minutes most of the time being downloads (so you can get a coffee or something to eat while your computer is doing the work). That said, the installation time depends on your internet connection, of course. Another advantage of the VirtualBox environment is that you can install it on a USB stick (>32GB) and then start, continue or re-do the tutorial on eny computer that has VirtualBox installed. All your data and temporary files will be stored in the environment on your stick. e\

#### Windows 10 - Ubuntu sub-system
Windows 10 users may also be able to run the install script and download the data into the Ubuntu sub-system. However, this has not been tested and it might be easier to just follow the instructions below to set up a Ubuntu VM.

#### Mac users
The easiest way especially for inexperienced Mac users is to follow the instructions below to set up a VirtualBox environment. However, it is also possible to install [the tools used](APP_TOOLS.md) in the tutorials and download [the tutorial data](APP_DATA.md) yourself. Unfortunately, the install script that downloads and sets up the Linux environment will (most likely) not work for Mac. You will therefore have to figure out potential installation problems yourself.

#### Linux users
If you are already working on Ubuntu 16.04 or 18.04 you can directly run the install script and download the tutorial data as described below. For other DEbian-based linux distributions the installation script should also work although this has so far not been tested.

<div style="background-color:#fce7e5;border-radius:5px;border-color:gray;border-style:solid;padding:5px">
  {% octicon alert height:32 class:"right left" aria-label:hi %} 
  The installation script will make changes to your *.bash_profile* and may create additional folders such as *~/github* and symlinks in */etc/bin*. If you don't like this please install the tutorial tools manually. 
</div>


## Compute Requirements
-----

To set up the virtual environment and do the tutorial I recommend a minimum of
* 40GB free disk space
* 4GB of RAM
* 4 CPU cores, i.e., a *Quad-core* processor as is found in most laptops

It will be possible to run the tutorial with half of the required specs but it will be slow and you will have to delete temporary files as you may not have enough free space to save all files at the same time.

<div style="background-color:#fcfce5;border-radius:5px;border-color:gray;border-style:solid;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  You can install the virtual environment on a USB stick or external hard-drive in case you don't have 40GB on your computer to spare. An advantage is that you can take the tutorial with you and continue/finish it on another computer. However, make sure that the harddrive/stick has high read/write specs. Otherwise execution of the different commands may be very slow. 
</div>

