https://github.com/GShatrawJr/CSC131-CalTrans-Project/blob/a6ff61eb07f03abcc1cef30f093efeb5f0c5a77c/Resources/PeopleSense%20Logo.png

People Sense partners with transit agencies to leverage the power of IoT sensors, machine learning, and data visualizations to bring the transit network to life using real time data, GPS maps, and historical time series data.  This gives our partners a living picture of their network that can be used to make vital decisions about resource management and network usage. Our goal is to use our system to turn our partners’ networks into smart devices that serve their customers, while generating and serving data back to the operators making those key decisions.

Download and install VirtualBox https://www.virtualbox.org/wiki/Downloads
Download Ubuntu ISO image https://ubuntu.com/download/desktop
Create a new virtual machine using the Ubuntu ISO image and use settings that make sense for your environment.
Once the virtual machine is booted, you may want to view things in full screen. This can be done by:
Selecting “Devices” and then “Insert Guest Additions CD image”.
It should automatically run but if it doesn’t, run the “autorun.sh” file stored on the CD image and wait for it to complete.
Once finished, restart the virtual machine and hit “Ctrl f” to view things in full screen.
Launch a new terminal and update packages: sudo apt update
The user might need to be added to the sudoers file:
Type su and enter the password
Type sudo usermod -a -G sudo <username> with your username
Restart the machine, open a new terminal, and re-enter the sudo apt update command.
Install docker https://docs.docker.com/engine/install/ubuntu/
Clone the PeopleSense project repo
Run the setup.sh script in PeopleSense-Proj/PeopleSense/containers/
Type bash setup.sh

