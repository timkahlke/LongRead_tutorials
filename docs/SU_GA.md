# Install the VirtualBox Guest Additions

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](SU_U.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](SU_D.md)

In order to be get the complete functionality of VirtualBox such as resizing and sharing of folders, you'll have to add the Expension Pack.

## 1. Start your Ubuntu VM

If your Ubuntu is not already started up go to your VirtualBox menu, select the created VM and press "start" and wait until you see the Ubuntu Desktop screen.

## 2. Add the Guest Edition

Click the "Devices"-tab of your VirtualBox window and select the "Insert Guest Additions CD image" option (Sorry, can't provide a Screen Shot). On Mac it's located in the top menu bar of the Ubuntu VM window.

This should automatically download the needed files into your Ubuntu. You may have to confirm the download and type in your password to proceed.

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Remember that this is <b>not</b> your normal computer password but the one you set when installing Ubuntu. If you went with my recommendations then the password is <i>course_user</i>
</div>

If everything worked as planned you should now be able to resize the window to adjust the size.

For further information on how to start/stop the VM, increase font size and other features see the [Frequently Asked Questions](FAQs.md) section.

Next, [install the tools and packages](SU_I.md) needed for the tutorial.
