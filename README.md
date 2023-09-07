# Anbox-Setup

## Anbox Installation

### Step-by-step instructions for installing Anbox: 

### Installation of VirtualBox:
a. Begin by downloading VirtualBox from https://www.virtualbox.org/wiki/Downloads. 


### Creating a New Virtual Machine: 
a. Open VirtualBox.

b. Click on "New" to create a new virtual machine.

c. Name your virtual machine (e.g., "Ubuntu").

d. Choose "Linux" as the type and "Ubuntu (64-bit)" as the version.

e. Allocate memory (RAM) as needed, ensuring it stays within the green zone.

f. Create a new virtual hard disk with sufficient space (e.g., 20GB or more).

g. Click "Create."


### Downloading Ubuntu 20.04 Image:


a. Download the Ubuntu 20.04 image from https://releases.ubuntu.com/20.04.6/?_ga=2.87788561.862535173.1694009354-534867877.1693694408. 


### Configuring Virtual Machine Settings:


a. In the VirtualBox Manager, right-click on your newly created virtual machine and select "Settings."

b. Under "System," go to the "Motherboard" tab, and make sure the "Enable EFI" option is CHECKED, and the "Enable Secure boot" option is UNCHECKED.

c. Under "System," go to the "Processor" tab and allocate the desired number of CPU cores.

d. Under "Display," increase the video memory for better performance. e. Under "Storage," add the Ubuntu ISO file to the virtual CD/DVD drive in the "Controller: IDE" section. Delete the existing empty image. 



### Installing Ubuntu: 


a. Start your virtual machine by clicking "Start."

b. The Ubuntu installer should boot from the ISO file. Follow the on-screen instructions to install Ubuntu. Select "Erase disk and install Ubuntu" or a similar option when prompted. Make sure to remember the username and password you enter during installation.


### Kernel Installation: 
a. Open a terminal. 

b. Run sudo su. 

c. Run modprobe binder_linux (it should run with no output). 

d. Run modprobe ashmem_linux (it should return an error). Follow the steps below to install this kernel

e. Install necessary packages by running:

f. apt install git 

g. apt install dkms 

h. git clone https://github.com/choff/anbox-modules

i. cd anbox-modules 

j. ./INSTALL.sh 

k. cp anbox.conf /etc/modules-load.d/ 

l. cp 99-anbox.rules /lib/udev/rules.d/ 

m. cp -rT ashmem /usr/src/anbox-ashmem-1 

n. cp -rT binder /usr/src/anbox-binder-1 

o. dkms install anbox-ashmem/1 

p. Restart the virtual machine. 


### Installing Anbox:
a. Open a terminal again. 

b. Run sudo su. 

c. snap install --devmode --edge anbox 


### Completing the Installation: 
a. Under applications, click "Anbox Application Manager" to start Anbox.

