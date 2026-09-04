# VMware Workstation Pro + Kali Linux Installation Guide

This guide covers how to install **VMware Workstation Pro on Windows**, create a Kali Linux virtual machine using the official **Kali Linux ISO**, and install the **Kali Linux Large** toolset.

---

# 1. Requirements

Before starting, make sure your computer has:

* Windows 10 or Windows 11
* 64-bit Intel or AMD processor
* Hardware virtualization enabled
* At least 8 GB of system RAM
* At least 80 GB of available storage
* Internet connection

For a better Kali VM experience, **16 GB or more of system RAM** is recommended.

> **Note:** This guide is for an Intel/AMD Windows computer. Apple Silicon Macs require the **ARM64** version of Kali instead of AMD64.

---

# 2. Download VMware Workstation Pro

VMware Workstation Pro allows you to create and run virtual machines on Windows.

## Download

Download VMware Workstation Pro from TechSpot:

https://www.techspot.com/downloads/189-vmware-workstation-for-windows.html

Select the newest version of:

**VMware Workstation Pro for Windows**

The installer should be an `.exe` file.

Example:

```text
VMware-workstation-full-26H1-xxxxx.exe
```

---

# 3. Install VMware Workstation Pro

After the download finishes:

1. Open the downloaded VMware `.exe` installer.
2. If Windows asks for administrator permission, select **Yes**.
3. Select **Next**.
4. Accept the license agreement.
5. Select **Next**.
6. Leave the default installation location unless you have a reason to change it.
7. Select any optional features you want.
8. Continue through the installer.
9. Select **Install**.
10. Wait for VMware Workstation Pro to finish installing.
11. Restart Windows if prompted.

After installation, open:

**VMware Workstation Pro**

---

# 4. Download Kali Linux

Kali Linux should be downloaded directly from the official Kali Linux website.

Official Kali Linux download page:

https://www.kali.org/get-kali/

> **Important:** Download Kali Linux from the official Kali website.

---

# 5. Select the Kali Installer

On the Kali download page, find:

**Installer Images**

For a normal Intel/AMD Windows computer, select:

**64-bit / x86_64 / AMD64**

Download the **Installer** image.

The filename should look similar to:

```text
kali-linux-XXXX.X-installer-amd64.iso
```

For example:

```text
kali-linux-2026.2-installer-amd64.iso
```

The version number will change as new versions of Kali Linux are released.

---

# 6. Create the Kali Virtual Machine

Open **VMware Workstation Pro**.

Select:

**Create a New Virtual Machine**

Choose:

```text
Typical (recommended)
```

Then select:

**Next**

---

# 7. Select the Kali ISO

Choose:

```text
Installer disc image file (iso)
```

Select **Browse** and locate the Kali ISO you downloaded.

Example:

```text
C:\Users\USERNAME\Downloads\kali-linux-2026.2-installer-amd64.iso
```

Select the ISO and continue.

> If VMware does not automatically recognize the Kali ISO, continue with the installation and manually select Linux/Debian as described in the next section.

---

# 8. Select the Guest Operating System

If VMware asks you to manually select the operating system, choose:

```text
Guest Operating System: Linux
Version: Debian 13.x 64-bit
```

If your version of VMware does not have Debian 13 available, select the newest **Debian 64-bit** option available.

Kali Linux is based on Debian.

---

# 9. Name the Virtual Machine

Give the VM a descriptive name.

Example:

```text
Kali Linux
```

Choose where you want VMware to store the virtual machine.

Example:

```text
C:\Virtual Machines\Kali Linux
```

Make sure the drive you select has enough free storage.

---

# 10. Configure the Virtual Disk

For a Kali VM that will eventually have the **Kali Large** toolset installed, a good virtual disk size is:

```text
100 GB
```

A minimum of around **80 GB** can work, but 100 GB gives you more room for:

* Kali tools
* Wordlists
* Package updates
* CTF files
* TryHackMe files
* Git repositories
* Custom scripts
* Captured files
* Forensics tools

VMware virtual disks normally grow as data is added, so creating a 100 GB virtual disk does not necessarily consume 100 GB of physical storage immediately.

For simplicity, you can select:

```text
Split virtual disk into multiple files
```

or:

```text
Store virtual disk as a single file
```

Either option will work.

---

# 11. Customize the Virtual Machine

Before starting the VM, select:

**Customize Hardware**

Recommended starting configuration:

| Setting        | Recommendation         |
| -------------- | ---------------------- |
| RAM            | 6–8 GB                 |
| CPU            | 2–4 Cores              |
| Storage        | 100 GB                 |
| Network        | NAT                    |
| USB Controller | Enabled                |
| Display        | Accelerate 3D Graphics |
| CD/DVD         | Kali Installer ISO     |

## Computer With 16 GB RAM

A good configuration is:

```text
RAM:     6 GB
CPU:     4 Cores
Disk:    100 GB
Network: NAT
```

## Computer With 32 GB+ RAM

A good configuration is:

```text
RAM:     8 GB
CPU:     4 Cores
Disk:    100 GB
Network: NAT
```

You can increase the resources later if necessary.

> **Important:** Do not give the VM all of your computer's CPU cores or RAM. Windows still needs enough resources to run properly.

---

# 12. Network Configuration

For most situations, start with:

```text
NAT
```

NAT allows Kali to access the internet through the Windows host while placing the VM behind VMware's virtual NAT network.

This is usually a good default for:

* TryHackMe
* CTFs
* Cybersecurity labs
* Learning Linux
* General pentesting practice

Common VMware network modes include:

```text
NAT
Bridged
Host-Only
```

## NAT

The VM accesses the network through the host computer.

```text
Kali VM
   |
VMware NAT
   |
Windows Host
   |
Network / Internet
```

This is the recommended default.

## Bridged

The VM connects to the same network as the host and appears as another device on that network.

```text
Kali VM --------\
                 \
Windows Host ----- Router / Network
```

Use Bridged mode when a lab specifically requires Kali to communicate directly with devices on the physical LAN.

## Host-Only

Creates an isolated virtual network between the host and virtual machines.

```text
Windows Host
     |
Host-Only Network
     |
   Kali VM
```

Host-Only networking is useful when creating isolated cybersecurity labs containing multiple virtual machines.

---

# 13. Start Kali

After configuring the VM:

1. Select **Finish**.
2. Select the Kali VM.
3. Click **Power on this virtual machine**.

The Kali Linux boot menu should appear.

---

# 14. Start the Kali Installer

From the Kali boot menu, select:

```text
Graphical install
```

The graphical Kali installer will start.

Follow the installation wizard.

You will configure:

* Language
* Location
* Keyboard
* Network
* Hostname
* Username
* Password
* Time zone
* Disk partitioning
* Desktop environment
* Software packages
* GRUB bootloader

---

# 15. Configure the Hostname

When Kali asks for a hostname, you can use:

```text
kali
```

Or choose another hostname for the machine.

Example:

```text
kali-ctf
```

---

# 16. Create Your Kali User

During installation, Kali will ask you to create a user account.

Choose:

* Your name
* Username
* Password

Remember the username and password because you will use them to log into Kali and execute commands with `sudo`.

---

# 17. Disk Partitioning

Because Kali is being installed inside a virtual machine, the disk being modified is the **VMware virtual disk**, not your normal Windows drive.

For a basic Kali VM, select:

```text
Guided - use entire disk
```

Select the VMware virtual disk.

Then select:

```text
All files in one partition
```

This is the simplest configuration for a Kali VM.

Continue and select:

```text
Finish partitioning and write changes to disk
```

Confirm the changes when prompted.

---

# 18. Software Selection

During installation, Kali will ask which desktop environment and software collections you want.

For a normal installation, keep the default selections.

A good starting configuration is:

```text
Desktop Environment: Xfce
Default Kali toolset
```

Do not worry about installing every Kali tool during the initial operating system installation.

The **Kali Large** toolset will be installed after the system is fully installed and updated.

---

# 19. Install GRUB

When prompted to install the GRUB bootloader, select:

```text
Yes
```

Install GRUB onto the main VMware virtual disk.

This allows Kali Linux to boot from its virtual disk after installation.

---

# 20. Finish the Kali Installation

After Kali finishes installing:

1. Complete the installer.
2. Allow the VM to reboot.
3. Kali should boot from the VMware virtual disk.
4. Log in using the username and password you created.

You should now have a working Kali Linux VM.

If the installer ISO boots again instead of the installed system, disconnect the ISO from the VM's virtual CD/DVD drive and reboot.

---

# 21. Update Kali Linux

After logging into Kali, open a terminal.

First update the package database:

```bash
sudo apt update
```

Then perform a full system upgrade:

```bash
sudo apt full-upgrade -y
```

Remove packages that are no longer required:

```bash
sudo apt autoremove -y
```

Reboot after the upgrade:

```bash
sudo reboot
```

---

# 22. Install VMware Guest Tools

Kali uses `open-vm-tools` for VMware integration.

After Kali reboots, open a terminal and run:

```bash
sudo apt update
sudo apt install -y open-vm-tools open-vm-tools-desktop
```

Then reboot:

```bash
sudo reboot
```

VMware integration provides features such as:

* Automatic display resizing
* Better mouse integration
* Clipboard integration
* Improved VMware guest support

After rebooting, verify the VMware Tools service:

```bash
systemctl status open-vm-tools
```

Press:

```text
q
```

to exit the status screen.

---

# 23. Install Kali Linux Large

Kali provides metapackages that allow you to install different collections of security tools.

The normal Kali installation does not necessarily contain every tool you may want.

For a larger pentesting/CTF workstation, install:

```text
kali-linux-large
```

First update your repositories:

```bash
sudo apt update
```

Install the Kali Large metapackage:

```bash
sudo apt install -y kali-linux-large
```

This can take a while because `kali-linux-large` installs a large collection of Kali tools and dependencies.

Make sure you have:

* A stable internet connection
* Plenty of free disk space
* Enough time for the installation to complete

After installation, clean unnecessary package files:

```bash
sudo apt autoremove -y
sudo apt clean
```

Then reboot:

```bash
sudo reboot
```

---

# 24. Verify Kali Large

After rebooting, you can verify that the metapackage is installed:

```bash
dpkg -s kali-linux-large
```

You should see:

```text
Status: install ok installed
```

You can also check with:

```bash
apt list --installed 2>/dev/null | grep kali-linux-large
```

---

# 25. Verify Network Connectivity

Verify that Kali can reach the internet:

```bash
ping -c 4 1.1.1.1
```

Then verify DNS resolution:

```bash
ping -c 4 kali.org
```

You can also check your network interfaces:

```bash
ip addr
```

And your routing table:

```bash
ip route
```

For a normal NAT configuration, Kali should receive an IP address from VMware's virtual network.

---

# 26. Verify Basic Kali Tools

Check that some common security tools are available:

```bash
nmap --version
```

```bash
gobuster version
```

```bash
john --list=build-info
```

```bash
hashcat --version
```

```bash
sqlmap --version
```

```bash
nikto -Version
```

You do not need every command for Kali to function. These simply provide a quick check that common security tools are installed.

---

# 27. Check Available Storage

Because `kali-linux-large` installs many packages, check your available storage:

```bash
df -h
```

Pay attention to the `/` filesystem.

You can also see how much space APT packages are consuming:

```bash
sudo du -sh /var/cache/apt
```

Clean the package cache when necessary:

```bash
sudo apt clean
```

---

# 28. Recommended Final Configuration

A good general-purpose Kali VM configuration is:

```text
Operating System: Kali Linux AMD64
Hypervisor:       VMware Workstation Pro
RAM:              6-8 GB
CPU:              4 Cores
Storage:          100 GB
Network:          NAT
Desktop:          Xfce
VMware Tools:     open-vm-tools
Toolset:          kali-linux-large
```

This configuration works well as a starting point for:

* TryHackMe
* CTF competitions
* CPTC practice
* Penetration-testing labs
* Network security labs
* Digital forensics
* Reverse engineering
* General Kali Linux practice

---

# 29. Useful Kali Commands

## Update Kali

```bash
sudo apt update
sudo apt full-upgrade -y
sudo apt autoremove -y
```

## Search for a Package

```bash
apt search PACKAGE_NAME
```

## Install a Package

```bash
sudo apt install PACKAGE_NAME
```

## Remove a Package

```bash
sudo apt remove PACKAGE_NAME
```

## Check Kali Version

```bash
cat /etc/os-release
```

## Check Kernel

```bash
uname -a
```

## Check IP Addresses

```bash
ip addr
```

## Check Routes

```bash
ip route
```

## Check Disk Space

```bash
df -h
```

## Check RAM

```bash
free -h
```

## Check CPU

```bash
lscpu
```

---

# 30. Useful Links

## VMware Workstation Pro

https://www.techspot.com/downloads/189-vmware-workstation-for-windows.html

## Kali Linux

https://www.kali.org/get-kali/

## Kali Documentation

https://www.kali.org/docs/

## Kali VMware Documentation

https://www.kali.org/docs/virtualization/

## Kali Metapackages

https://www.kali.org/docs/general-use/metapackages/

---

# 31. Quick Installation Checklist

## VMware

* [ ] Download VMware Workstation Pro
* [ ] Install VMware Workstation Pro
* [ ] Restart Windows if required

## Kali ISO

* [ ] Download Kali Linux AMD64 Installer ISO
* [ ] Save the ISO somewhere easy to find

## Virtual Machine

* [ ] Create a new VMware virtual machine
* [ ] Attach the Kali ISO
* [ ] Select Linux/Debian 64-bit
* [ ] Configure 6–8 GB RAM
* [ ] Configure 2–4 CPU cores
* [ ] Configure approximately 100 GB storage
* [ ] Set networking to NAT
* [ ] Boot the Kali installer

## Kali Installation

* [ ] Select Graphical Install
* [ ] Configure language and keyboard
* [ ] Configure hostname
* [ ] Create user account
* [ ] Configure disk partitioning
* [ ] Install Xfce
* [ ] Install default Kali toolset
* [ ] Install GRUB
* [ ] Finish installation
* [ ] Boot into Kali

## Post-Installation

* [ ] Update Kali
* [ ] Perform full system upgrade
* [ ] Install `open-vm-tools`
* [ ] Reboot
* [ ] Install `kali-linux-large`
* [ ] Reboot
* [ ] Verify internet connectivity
* [ ] Verify DNS
* [ ] Verify common Kali tools
* [ ] Check available disk space

---

# 32. Final Update Command

Once everything is installed, the main command sequence you will commonly use to keep Kali updated is:

```bash
sudo apt update
sudo apt full-upgrade -y
sudo apt autoremove -y
sudo apt clean
```

Reboot when a major kernel or system update requires it:

```bash
sudo reboot
```

---

# Notes

* Only perform penetration testing against systems you own or have explicit permission to test.
* Keep Kali updated before beginning labs.
* NAT is a good default VMware network mode unless a lab requires something different.
* Use Host-Only networking when you need to build an isolated virtual lab.
* Use Bridged networking only when you specifically need the VM directly connected to the physical LAN.
* Keep important projects, scripts, notes, and CTF files backed up outside the VM.
* `kali-linux-large` installs many tools and requires significantly more storage than the default Kali installation.
* Additional tools can always be installed later with `apt`.
