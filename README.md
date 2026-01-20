# Macos-Linux

i will be using this a script almost for this https://docs.getutm.app/guides/ubuntu/
I will also be using UTM and a ISO of linux from UTMs gallery

Installing Ubuntu on UTM - Step-by-Step Guide
This guide walks you through installing Ubuntu on macOS using UTM virtualization software.
Prerequisites
1. Download UTM

Visit mac.getutm.app
Download the free version (UTM.dmg)
Alternatively, purchase from Mac App Store ($9.99) for automatic updates
Open the DMG file and drag UTM to your Applications folder

2. Download Ubuntu ISO
Choose the appropriate version for your Mac:
For Apple Silicon Macs (M1/M2/M3):

Download Ubuntu Server ARM64 from ubuntu.com/download/server/arm
Use Ubuntu 22.04 LTS or 24.04 LTS (recommended)

For Intel Macs:

Download the standard x86_64 Ubuntu Server ISO

Installation Steps
Step 1: Create a New Virtual Machine

Open UTM
Click the "+" button at the top
Select "Virtualize"
Select "Linux"

Step 2: Configure Boot Settings

Use Apple Virtualization: Enable this for better performance on Apple Silicon (optional but recommended)
Boot ISO Image: Click "Browse" and select your downloaded Ubuntu ISO file
Click "Continue"

Step 3: Set Hardware Resources

Memory (RAM):

Default: 4096 MB (4 GB)
Recommended: At least 4 GB, or half your Mac's available RAM


CPU Cores: Choose based on your Mac's capabilities (4-8 cores recommended)
Leave "Enable Hardware OpenGL Acceleration" unchecked
Click "Continue"

Step 4: Configure Storage

Storage Size:

Default: 64 GB
Minimum recommended: 30 GB
Adjust based on your needs and available disk space


Click "Continue"

Step 5: Shared Directory (Optional)

You can select a directory to share between macOS and Ubuntu
This can be configured later, so feel free to skip for now
Click "Continue"

Step 6: Save and Start

Click "Save" to create the VM
Click the Play button to start the virtual machine

Ubuntu Installation Process
Step 7: Begin Ubuntu Installation

When the VM boots, select "Try or Install Ubuntu Server"
Press Enter
Wait for the installer to load (may take a few moments)

Step 8: Configure Installation Settings
Navigate using Tab, Arrow Keys, and Enter to confirm:

Language: Select your preferred language
Keyboard Configuration: Choose your keyboard layout
Network Connections: Accept defaults (note your assigned IP address)
Proxy: Leave blank unless you need one
Ubuntu Archive Mirror: Accept default
Storage Configuration:

Select "Use an entire disk"
Confirm the disk selection


Profile Setup:

Enter your name
Choose a server name
Create a username
Create a password


SSH Setup: Enable "Install OpenSSH server" (recommended for remote access)
Featured Server Snaps: Select any additional software you want (optional)

Step 9: Wait for Installation

The installation will begin copying and configuring files
This process takes 10-30 minutes
Do not interrupt the installation

Step 10: First Reboot

When prompted, select "Reboot Now"
The reboot may fail or hang
If it doesn't reboot automatically:

Click the Power button icon in the top left to stop the VM
In the VM overview menu, select the CD/DVD icon
Choose "Clear" or "Eject" to remove the ISO
Restart the VM



Step 11: First Login

Wait for Ubuntu to boot to the command line
Login with the username and password you created during installation

Post-Installation Setup
Step 12: Install Desktop Environment (Optional)
If you want a graphical interface instead of just the command line:
bashsudo apt update
sudo apt install ubuntu-desktop
Wait for installation to complete (20-30 minutes), then reboot:
bashsudo reboot now
Step 13: Install SPICE Tools
For better integration, shared folders, and display resolution:
bashsudo apt install spice-vdagent spice-webdavd
sudo reboot now
Step 14: Configure Shared Folder
If you want to access files from macOS:

Stop the VM
Right-click the VM and select "Edit"
Go to "Drives" or "Sharing"
Add a shared directory from your Mac
In Ubuntu, the shared folder will appear in /media/share or can be mounted manually

Step 15: Optimize Display (Optional)
For better resolution on high-DPI displays:

Stop the VM
Right-click the VM and select "Edit"
Go to "Display"
Enable "HiDPI (Retina)"
Keep "Dynamic resolution" enabled
Save and restart the VM

Step 16: Extend LVM Partition (If Needed)
If the disk doesn't use the full allocated space:
bashsudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
Troubleshooting
Issue: VM Won't Boot After Installation

Make sure the installation ISO is ejected (see Step 10)
Try entering the EFI Shell by pressing Esc during boot
Verify the boot order in VM settings

Issue: "Display output is not active"

Wait 1-2 minutes for the desktop to load
This is common with QEMU virtualization

Issue: No Internet Connection
Check DNS settings:
bashsudo nano /etc/systemd/resolved.conf
Add or uncomment:
DNS=1.1.1.1
Save and restart the service:
bashsudo systemctl restart systemd-resolved
Summary
You now have Ubuntu running on your Mac via UTM! You can:

Use it for Linux development and testing
Run server applications
Learn Linux commands
Test software in an isolated environment

Remember to regularly update your Ubuntu installation:
bashsudo apt update && sudo apt upgrade

here are images of the processes
<img width="2568" height="1514" alt="image" src="https://github.com/user-attachments/assets/e972e2ed-f5f2-43cf-88e3-a350300ebc6b" />


