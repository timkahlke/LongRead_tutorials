# Install Ubuntu in your Virtual Machine

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](SU_VB.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](SU_GA.md)

Your newly created Virtual Machine (VM) should appear in VirtualBox in the menu on the left. Select the VM by clicking on it in the menu and then start it up.

<img src="figures/VB_12.png" height="200px">

In the new window choose the downloaded Ubuntu *iso* file and press "Start" 

<img src="figures/VB_13.png" height="150px">

<div style="background-color:#fce7e5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon alert height:32 class:"right left" aria-label:hi %} 
Make sure your internet connection is working as Ubuntu will download updates and additional packages during the installation process.
</div>


The language should already be English. Start the installation by pressing "Install Ubuntu"

<img src="figures/VB_14.png" height="200px">

In the next windows the defaults should be ok, so just press "Continue" for "Keyboards" and "Install". Then press "Install Now" and "Continue" when asked to "Write the changes to disk"

<img src="figures/VB_15.png" height="300px">

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Initially the screen may be quite small. We will change this as soon as Ubuntu is installed properly.
</div>

Next you'll have to configure your Ubuntu. First, set the time zone but clicking on the map and press continue.

<img src="figures/VB_16.png" height="300px">

In the next screen you can set your user details. You can configure most values as you like except for the user name: **if you change the user name the install script for the tools and packages will not work properly**. For simplicity, I recommend setting the name, user name and password all to "course_user", the computer name to "LongReadVM" and also check the "Log in automatically" option so you don't have to type in a password on start up. Your window should look like the one below:

<img src="figures/VB_17.png" height="300px">

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  When typing the password Ubuntu will not show the actual characters you type but blank them out with black dots. That is a normal security feature, it will still remember your password correctly.
</div>

When done press "Continue". Ubuntu should now start the installation process. This may take a few minutes depending on your computer. When the installation process is done press "Restart Now". When asked to "Remove the disk" just press "Enter", VirtualBox will automatically remove it on restart.

<img src="figures/VB_18.png" height="300px">  <img src="figures/VB_19.png" height="300px">

Congratulations, you now have a Ubuntu 18.04 Virtual Machine to work with! :)

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Ubuntu may ask you to install/update software and software packages after the installation is done. If so just confirm the installation and, if needed, type your Ubuntu password again.
</div>

Next set up the [VirtualBox Guest Additions](SU_GA.md)
