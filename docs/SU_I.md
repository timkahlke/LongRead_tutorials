[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](SU_GA.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](SU_D.md)

# Installation of packages, tools and data

Installation of all tools and packages needed can be done using the [install script]() of the tutorial. First open FireFox in your Ubuntu VM, navigate to this page, i.e., https://timkahlke.github.io/LongRead_tutorials/SU.html, and download the [install script]().

Now open the command line terminal: Open Ubuntus App Center, type *terminal* in the search field and click the *Terminal* app.

<img src="figures/INST_1.png" height="300px">  

This will open a command line window, your main "Bioinformatics tool".

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  You can also add the <i>Terminal</i> app to the side-bar of you Ubuntu so you don't have to always open it through the App Center. When the Terminal is open simply right-click on it in the side-bar and choose <i>Add to Favourites</i>. 
  
  <img src="figures/INST_2.png" height="200px">  
</div>

Now execute the file you just downloaded. By default Firefox downloads files into the *Downloads* folder in your home directory. To execute the install script type 

    sudo bash ~/Downloads/install_script.sh

This will automatically download and install all needed tools and packages and set-up your tutorial environment.

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Depending on your internet connection and computer this may take up to an hour. However you can just leave it running in the background until it's done.
</div>

After the install script is done close the terminal and re-open it. Your Ubuntu is now ready to do some serious bioinformatics! 

Last but not least [download the tutorial data](SU_D.md) and you are finally ready to go.
