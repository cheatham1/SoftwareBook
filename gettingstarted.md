# Setup Your Environment

We have provided the datasets and software in a variety of formats.  You choose how you want to use them:

* If you want to have a quick look at the data, not investing too much time, you can use the small virtual machine, which contains 10% of the data.  This takes takes about 15 minutes to download and setup.


* If you want to invest more time, or are setting up a lab for students, then you can use the medium virtual machine which contains all the data.  This takes 1-2 hours to download and setup.


* If you are a physicists, it is likely you already have ROOT installed, so you can just download the software and datasets separately if you wish.

These instructions explain how to setup your environment for the first situation.  The virtual machine book (the other gitbook in this Data & Tools section of the website) explains how to setup for the second.

## What is a virtual machine ?

A virtual machine will transform your computer into an analysis machine!

Your physical computer will be the "host", while the virtual machine will be a "guest". Most of the guest code runs unmodified, directly on the host computer, and the guest operating system "thinks" it's running on a real machine.

A virtual machine allows an unmodified operating system with all of its installed software to run in a special environment, on top of your existing operating system. 

There are five virtual machines available.
We suggest you start with the **small** version.  It contains everything you need to start looking at the data.

**Now you will learn how to download and prepare a virtual machine to run on your computer**.  This will then enable you to take a look at ATLAS data. You have to download and install VirtualBox.  To save time, start downloading the  virtualmachine.

There are three steps to setup your environment
1. Download a virtual machine.
2. Download and install VirtualBox.
3. Setup your virtual machine.

# Step 1: Download the Small Virtual Machine (VM Version S)

A small virtual machine using Lubuntu in conjunction with ROOT-5.34.14 and 10% of the data has been prepared. This is 1.7Gb in size so can be downloaded fairly quickly. 

**Make sure you download the SMALL virtual machine if you are following these instructions.**

# Step 2: Download and install VirtualBox

Use the VirtualBox website to download the software

<a href="https://www.virtualbox.org/" target="_blank"> Go to the VirtualBox website</a>

Select **Download VirtualBox**
 
![](Pictures/VB5.1.jpg)

Take care to select the appropriate **VirtualBox platform package**.


![](Pictures/DownloadVB.jpg)
 
Proceed with the installation of VirtualBox:

![](Pictures/VBinstall1.png)


![](Pictures/VBinstall2.png)


![](Pictures/VBinstall3.png)




## Step 3: Set up your Virtual Machine

Start VirtualBox.

Look for the VirtualBox icon in your Applications (folder). Double click to get the main interface of VirtualBox:


![](Pictures/VMempty.png)


Select File/ Import Appliance

![](Pictures/VMimportAppliance.png)


An empty text box will appear


![](Pictures/VMimportApplianceSelect.png)



Use the yellow folder icon on the right hand-side of the empty text box to select your virtual machine (the .ova file you downloaded at the start of this chapter).  Then press "Continue".

**Make sure you have downloaded the small virtual machine.  It will be called "ATLASOpenDataSmall.ova"**


![](Pictures/VMselectOVA.png)



The default settings are displayed.  We recommend you use these.  Press "Import"


![](Pictures/VMapplianceSettings.png)



Import will take afew minutes


![](Pictures/VMimporting.png)



Select your virtual machine 'ATLASOpenDataSmall' (which is powered off)

**Make sure you have downloaded the small virtual machine.  It will be called "ATLASOpenDataSmall"**

![](Pictures/VMpoweredOff.png)


Your VM will then be displayed

**Check that the name of your virtual machine displayed on the right is "ATLASOpenDataSmall"
**
![](Pictures/VMATLASopenDataSmall.png)


Press the green 'Start' arrow.


WAIT afew minutes whilst the virtual machine sets up.  

When it has completed you will see 
the terminal for using the code, with the Readme file opened using the atom editor.

![](Pictures/VMrunningREADME.png)

In the menu on the left handside, you see the contents of the root directory.

In the root directory there are five directories (Analysis, Configurations, Input, Plotting and Output), the README file plus two python scripts. The python scripts are RunScript.py and PlotResults.py. 


At the bottom of your window, you will notice a tab labelled "atlas@atlas-vm".

![](Pictures/VM-atlas.png)

Select this tab, circled in red in the screen-shot.  A terminal window will then be available. 

Type "ls" and you will see the folders and files in your main directory.

![](Pictures/VMterminalWindow.png)


You are now ready to start looking at the ATLAS data.

**If your session goes to sleep and requires the atlas password, it is 'atlas'.** 


