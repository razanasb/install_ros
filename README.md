# install_ros steps :
download virtualbox
Open the VirtualBox website. Go to https://www.virtualbox.org/ in the computer Internet browser. This is the website from which you'll download the VirtualBox setup
Click Download VirtualBox. It's a blue button in the middle of the page. Doing so will open the downloads page.
Click Windows hosts. You'll see this link below the "VirtualBox 6.1.14 platform packages" heading. The VirtualBox EXE file will begin downloading onto your computer.
Open the VirtualBox EXE file. Go to the location to which the EXE file downloaded and double-click the file. Doing so will open the VirtualBox installation window.
Navigate through the installation prompts. Do the following:
Click Next on the first three pages.
Click Yes when prompted.
Click Install
Click Yes when prompted.
Click Install when prompted. Doing so will allow VirtualBox to begin installing on your computer.
Click Finish when prompted. It's in the lower-right side of the window. Doing so will close the installation window and open VirtualBox. Now that you've installed and opened VirtualBox, you can create a virtual machine in order to run any operating system on your PC.
Make sure that you don't uncheck the "Start" box before doing this.
next install ubuntu on virtualbox
Open VirtualBox and select New . A new window will come out.
Choose your guest OS and architecture (32 vs. 64 bit, e.g select Ubuntu)
Set your Base Memory (RAM)
Click next until it show the vm storage size. Put how much space you need depending on your hardisk and finish the wizard by clicking the create button.
On VirtualBox main window, select START and pick your MEDIA SOURCE. In your case, select the .iso on your desktop.
Finish the installation as normal install.
Remove your installation .iso from the virtual optical disk drive before restarting the VM.
Install Guest Additions.
then install ros on ubunto 
Configure your Ubuntu repositories
Configure your Ubuntu repositories to allow "restricted," "universe," and "multiverse." You can follow the Ubuntu guide for instructions on doing this.

Setup your sources.list
Setup your computer to accept software from packages.ros.org.


sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

Mirrors

Source Debs are also available

Set up your keys
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
Installation
First, make sure your Debian package index is up-to-date:

sudo apt update
Now pick how much of ROS you would like to install.

Desktop-Full Install: (Recommended) : Everything in Desktop plus 2D/3D simulators and 2D/3D perception packages

sudo apt install ros-noetic-desktop-full
or click here

Desktop Install: Everything in ROS-Base plus tools like rqt and rviz

sudo apt install ros-noetic-desktop
or click here

ROS-Base: (Bare Bones) ROS packaging, build, and communication libraries. No GUI tools.

sudo apt install ros-noetic-ros-base
or click here

There are even more packages available in ROS. You can always install a specific package directly.

sudo apt install ros-noetic-PACKAGE
e.g.
sudo apt install ros-noetic-slam-gmapping
To find available packages, see ROS Index or use:

apt search ros-noetic

Environment setup
You must source this script in every bash terminal you use ROS in.


source /opt/ros/noetic/setup.bash
It can be convenient to automatically source this script every time a new shell is launched. These commands will do that for you.

Bash


If you have more than one ROS distribution installed, ~/.bashrc must only source the setup.bash for the version you are currently using.


echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
zsh

echo "source /opt/ros/noetic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
Dependencies for building packages
Up to now you have installed what you need to run the core ROS packages. To create and manage your own ROS workspaces, there are various tools and requirements that are distributed separately. For example, rosinstall is a frequently used command-line tool that enables you to easily download many source trees for ROS packages with one command.

To install this tool and other dependencies for building ROS packages, run:


sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
Initialize rosdep
Before you can use many ROS tools, you will need to initialize rosdep. rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS. If you have not yet installed rosdep, do so as follows.


sudo apt install python3-rosdep
With the following, you can initialize rosdep.


sudo rosdep init
rosdep update

