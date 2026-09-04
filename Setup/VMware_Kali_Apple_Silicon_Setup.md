# VMware Fusion Pro + Kali Linux Installation Guide for Apple Silicon

This guide covers how to install **VMware Fusion Pro on an Apple Silicon Mac** and create a **Kali Linux ARM64 virtual machine** using the official Kali Linux installer ISO.

This guide applies to Macs using Apple Silicon processors such as:

```text
Apple M1
Apple M1 Pro
Apple M1 Max
Apple M1 Ultra

Apple M2
Apple M2 Pro
Apple M2 Max
Apple M2 Ultra

Apple M3
Apple M3 Pro
Apple M3 Max
Apple M3 Ultra

Apple M4
Apple M4 Pro
Apple M4 Max

Apple M5
```

---

# 1. Requirements

Before starting, make sure your Mac has:

* Apple Silicon processor
* macOS
* At least 8 GB of system RAM
* At least 80–100 GB of available storage
* Internet connection
* Administrator access to macOS

For a better Kali VM experience:

```text
16 GB RAM or more recommended
100 GB+ free storage recommended
```

> **Important:** Apple Silicon Macs use the ARM architecture. You must download the **ARM64 version of Kali Linux**.

Do **not** use:

```text
AMD64
x86_64
Intel 64-bit
```

on an Apple Silicon Mac.

You want:

```text
ARM64
Apple Silicon
aarch64
```

---

# 2. Confirm Your Mac Uses Apple Silicon

Click:

```text
Apple Menu
→ About This Mac
```

Look for:

```text
Chip: Apple M1
Chip: Apple M2
Chip: Apple M3
Chip: Apple M4
Chip: Apple M5
```

If you see an Apple M-series chip, continue with this guide.

You can also check from Terminal:

```bash
uname -m
```

On Apple Silicon, the result should be:

```text
arm64
```

If the result is:

```text
x86_64
```

you have an Intel Mac and should use the AMD64 Kali installer instead.

---

# 3. Download VMware Fusion Pro

VMware Fusion Pro is VMware's virtualization platform for macOS.

It performs a similar role on Mac as VMware Workstation Pro does on Windows.

## Download

You can download VMware Fusion Pro from TechSpot:

https://www.techspot.com/downloads/2755-vmware-fusion-mac.html

Download the newest version of:

```text
VMware Fusion Pro for macOS
```

For example:

```text
VMware Fusion Pro 26H1
```

The installer will normally be provided as a macOS disk image:

```text
.dmg
```

Example:

```text
VMware-Fusion-26H1.dmg
```

> VMware Fusion Pro does not require a license key for normal free use.

---

# 4. Install VMware Fusion Pro

After VMware Fusion finishes downloading:

1. Open **Finder**.
2. Open the **Downloads** folder.
3. Double-click the VMware Fusion `.dmg` file.
4. Double-click the **VMware Fusion** icon.
5. macOS may ask whether you want to open the application.
6. Select **Open**.
7. Enter your Mac administrator password if prompted.
8. Follow the VMware Fusion installation process.
9. Allow any permissions VMware Fusion requests that are necessary for virtualization.
10. Open VMware Fusion.

You can later open VMware Fusion from:

```text
Applications
→ VMware Fusion
```

---

# 5. Allow VMware Permissions in macOS

Depending on your macOS version, VMware Fusion may request permissions.

Open:

```text
System Settings
→ Privacy & Security
```

If macOS displays a message regarding VMware system software or permissions, approve it.

VMware may request access to features such as:

* Network access
* USB devices
* Accessibility
* Files and folders
* Virtualization features

Only grant permissions that are required for the VMware features you intend to use.

You may need to restart VMware Fusion after approving permissions.

---

# 6. Download Kali Linux

Download Kali Linux directly from the official Kali Linux website:

https://www.kali.org/get-kali/

Find:

```text
Installer Images
```

Kali provides separate architecture options.

For an Apple Silicon Mac, choose:

```text
Apple Silicon (ARM64)
```

---

# 7. Select the Kali ARM64 Installer

Download the normal Kali installer image for:

```text
Architecture: ARM64
Platform: Apple Silicon
Image: Installer
```

The filename should look similar to:

```text
kali-linux-XXXX.X-installer-arm64.iso
```

For example:

```text
kali-linux-2026.2-installer-arm64.iso
```

The version number will change as Kali releases new versions.

> **Do not download `installer-amd64.iso` for an Apple Silicon Mac.**

Correct:

```text
kali-linux-2026.2-installer-arm64.iso
```

Incorrect:

```text
kali-linux-2026.2-installer-amd64.iso
```

---

# 8. Why ARM64 Is Required

Apple Silicon processors use the ARM64 architecture.

Your virtualization setup is:

```text
macOS
  |
Apple Silicon ARM64 CPU
  |
VMware Fusion
  |
Kali Linux ARM64
```

VMware Fusion can efficiently virtualize an ARM64 operating system because the host and guest use the same CPU architecture.

Trying to install the normal x86_64/AMD64 Kali ISO will not work as a normal Apple Silicon virtual machine.

---

# 9. Verify the Kali ISO

It is good security practice to verify the downloaded Kali image before installing it.

Kali publishes SHA256 hashes for official images.

Open Terminal.

Move to your Downloads directory:

```bash
cd ~/Downloads
```

Calculate the SHA256 hash:

```bash
shasum -a 256 kali-linux-*-installer-arm64.iso
```

For example:

```bash
shasum -a 256 kali-linux-2026.2-installer-arm64.iso
```

Compare the result against the SHA256 value provided on:

https://www.kali.org/get-kali/

The values should match exactly.

If they do not match, delete the ISO and download it again from the official Kali website.

---

# 10. Create the Kali Virtual Machine

Open:

```text
VMware Fusion
```

Select:

```text
File
→ New
```

Or select:

```text
Create a New Virtual Machine
```

Choose:

```text
Install from disc or image
```

Depending on your VMware Fusion version, the wording may appear as:

```text
Install from disk or image
```

---

# 11. Select the Kali ISO

Drag the Kali ARM64 ISO into the VMware Fusion window.

Or select:

```text
Use another disc or disc image
```

Navigate to:

```text
Downloads
```

Select:

```text
kali-linux-XXXX.X-installer-arm64.iso
```

Example:

```text
kali-linux-2026.2-installer-arm64.iso
```

Then continue.

---

# 12. Select the Guest Operating System

If VMware Fusion asks you to choose the operating system manually, select:

```text
Operating System: Linux
```

Then select the newest available ARM64 Debian option.

A common choice is:

```text
Debian 12.x 64-bit Arm
```

or, if available:

```text
Debian 13 64-bit Arm
```

The exact wording may vary depending on your version of VMware Fusion.

The important parts are:

```text
Linux
Debian
ARM64 / ARM
```

Kali Linux is based on Debian.

---

# 13. Name the Virtual Machine

Give the VM a descriptive name.

Example:

```text
Kali Linux ARM64
```

Other examples:

```text
Kali-CTF
Kali-THM
Kali-Pentest
Kali-ARM64
```

A simple default is:

```text
Kali Linux
```

---

# 14. Choose the Virtual Machine Location

VMware Fusion normally stores virtual machines in:

```text
~/Virtual Machines.localized/
```

You can leave the default location.

A Kali VM may eventually consume significant storage, especially if you install:

```text
kali-linux-large
```

or store:

* Wordlists
* Packet captures
* CTF files
* Forensic images
* Git repositories
* Malware samples
* Reverse engineering files

Make sure the Mac has plenty of available disk space.

---

# 15. Configure Virtual Disk Size

For a normal Kali VM, use approximately:

```text
80 GB
```

For a Kali VM where you plan to install:

```text
kali-linux-large
```

I recommend:

```text
100 GB
```

If you expect to store many CTF files, forensic images, packet captures, or tools, consider:

```text
120–150 GB
```

A good general-purpose setup is:

```text
Virtual Disk: 100 GB
```

VMware virtual disks normally grow as data is added, so allocating a maximum size of 100 GB does not necessarily consume all 100 GB immediately.

---

# 16. Customize the Virtual Machine

Before starting Kali, open:

```text
Virtual Machine
→ Settings
```

Configure the virtual machine hardware.

Recommended settings:

| Setting      | Recommendation          |
| ------------ | ----------------------- |
| RAM          | 6–8 GB                  |
| CPU          | 4 Cores                 |
| Storage      | 100 GB                  |
| Network      | NAT / Share with my Mac |
| USB          | Enabled                 |
| CD/DVD       | Kali ARM64 ISO          |
| Architecture | ARM64                   |

---

# 17. Recommended Configuration for an 8 GB Mac

If your Mac only has:

```text
8 GB RAM
```

use approximately:

```text
RAM:     4 GB
CPU:     2 Cores
Disk:    80–100 GB
Network: NAT
```

Do not allocate most of the Mac's memory to Kali.

macOS still needs enough RAM to operate properly.

---

# 18. Recommended Configuration for a 16 GB Mac

For a Mac with:

```text
16 GB RAM
```

use:

```text
RAM:     6 GB
CPU:     4 Cores
Disk:    100 GB
Network: NAT
```

This is a good general-purpose Kali configuration.

---

# 19. Recommended Configuration for a 24 GB or 32 GB Mac

For:

```text
24 GB RAM
```

or:

```text
32 GB RAM
```

use approximately:

```text
RAM:     8 GB
CPU:     4 Cores
Disk:    100–150 GB
Network: NAT
```

You can increase Kali to:

```text
12 GB RAM
```

if you regularly run memory-intensive tools or multiple applications inside Kali.

---

# 20. CPU Configuration

A good default is:

```text
4 CPU Cores
```

For lighter systems:

```text
2 CPU Cores
```

For powerful Apple Silicon systems:

```text
4–6 CPU Cores
```

Avoid assigning all CPU cores to Kali.

macOS still needs CPU resources.

---

# 21. VMware Display Settings

Open:

```text
Virtual Machine
→ Settings
→ Display
```

Use VMware's normal recommended display settings.

If you experience graphical problems such as:

* Black screen
* Desktop corruption
* Login screen problems
* Display freezes

try disabling:

```text
Accelerated 3D Graphics
```

Kali's VMware documentation specifically notes that accelerated 3D graphics can cause issues in some VMware configurations.

---

# 22. Network Configuration

VMware Fusion provides several virtual networking modes.

For most Kali users, start with:

```text
Share with my Mac
```

This is VMware Fusion's NAT-style networking option.

Your network path looks approximately like:

```text
Kali VM
   |
VMware NAT
   |
macOS
   |
Wi-Fi / Ethernet
   |
Internet
```

This is a good default for:

* TryHackMe
* Hack The Box
* CTF competitions
* CPTC practice
* Linux practice
* General pentesting labs

---

# 23. NAT / Share with My Mac

Use:

```text
Share with my Mac
```

for most situations.

Advantages:

* Kali gets internet access
* Easy configuration
* VMware handles virtual networking
* Kali is not directly exposed as a separate physical LAN device

This should be your default network mode.

---

# 24. Bridged Networking

Bridged networking makes Kali appear as another device on your physical network.

The network looks approximately like:

```text
             ┌── macOS Host
Router ──────┤
             └── Kali VM
```

Use Bridged networking when:

* A lab specifically requires it
* Kali must communicate directly with LAN devices
* You are building an authorized home cybersecurity lab
* You need Kali to receive an IP address from your physical router

Do not use Bridged mode unless you need it.

---

# 25. Host-Only Networking

Host-Only networking creates an isolated virtual network.

Example:

```text
macOS
  |
VMware Host-Only Network
  |
Kali VM
  |
Other Lab VMs
```

This is useful for:

* Vulnerable VM labs
* Malware analysis labs
* Network attack practice
* Metasploitable
* Custom CTF environments
* Isolated penetration-testing environments

Host-Only is useful when you do not want a vulnerable lab machine directly connected to your real LAN.

---

# 26. Start Kali

After configuring the VM:

1. Save the VMware settings.
2. Start the Kali virtual machine.
3. VMware Fusion should boot from the Kali ARM64 ISO.

The Kali boot menu should appear.

---

# 27. Start the Kali Installer

Select:

```text
Graphical install
```

The graphical installer will start.

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
* Kali packages
* GRUB bootloader

---

# 28. Select Language

Choose your preferred language.

For example:

```text
English
```

Continue.

---

# 29. Select Location

Choose your country or region.

For example:

```text
United States
```

Continue.

---

# 30. Configure Keyboard

Choose your keyboard layout.

For most US users:

```text
American English
```

Continue.

---

# 31. Configure the Hostname

When Kali asks for a hostname, you can use:

```text
kali
```

Other examples:

```text
kali-ctf
kali-thm
kali-lab
kali-arm
```

A simple recommendation is:

```text
kali
```

---

# 32. Configure the Domain Name

If Kali asks for a domain name and you are not joining an existing domain, you can normally leave it blank.

Example:

```text
Domain name:
<blank>
```

Continue.

---

# 33. Create Your Kali User

Create your user account.

Kali will ask for:

* Full name
* Username
* Password

Example:

```text
Username: kali
```

You may choose any username you want.

Remember the password because you will use it for:

```bash
sudo
```

commands.

---

# 34. Disk Partitioning

Since Kali is running inside VMware Fusion, the disk shown by the installer is a **virtual disk**.

It is not your normal macOS disk.

For a standard Kali VM, select:

```text
Guided - use entire disk
```

Select the VMware virtual disk.

Then select:

```text
All files in one partition
```

This is the simplest configuration for a Kali VM.

---

# 35. Confirm Disk Changes

Select:

```text
Finish partitioning and write changes to disk
```

When asked:

```text
Write the changes to disks?
```

select:

```text
Yes
```

Kali will partition the VMware virtual disk.

---

# 36. Software Selection

During installation, Kali will ask which desktop environment and tools you want.

A good starting configuration is:

```text
Xfce
Default Kali toolset
```

You do not need to install every possible Kali package during the initial installation.

We will install:

```text
kali-linux-large
```

after Kali is fully installed and updated.

---

# 37. Install GRUB

When prompted to install the GRUB bootloader, select:

```text
Yes
```

Install GRUB to the VMware virtual disk.

GRUB allows the Kali virtual machine to boot normally after installation.

---

# 38. Finish the Kali Installation

After Kali finishes installing:

1. Complete the installation.
2. Allow Kali to reboot.
3. VMware Fusion should boot Kali from the virtual disk.
4. Log in with the username and password you created.

You should now have Kali Linux ARM64 running on your Apple Silicon Mac.

---

# 39. Disconnect the Installer ISO if Necessary

If Kali starts the installer again after rebooting, shut down the VM.

Open:

```text
Virtual Machine
→ Settings
→ CD/DVD
```

Disconnect the Kali ISO.

Then start the VM again.

Kali should now boot from the virtual disk.

---

# 40. Update Kali Linux

After logging in, open Terminal inside Kali.

Run:

```bash
sudo apt update
```

Then perform a full upgrade:

```bash
sudo apt full-upgrade -y
```

Remove unnecessary packages:

```bash
sudo apt autoremove -y
```

Clean downloaded package files:

```bash
sudo apt clean
```

Then reboot:

```bash
sudo reboot
```

---

# 41. Install VMware Guest Tools

Kali uses:

```text
open-vm-tools
```

for VMware integration.

The Kali installer may automatically install VMware guest tools when it detects that it is running inside VMware.

You can make sure they are installed with:

```bash
sudo apt update
sudo apt install -y open-vm-tools open-vm-tools-desktop
```

Reboot:

```bash
sudo reboot
```

---

# 42. Verify VMware Guest Tools

Check the VMware Tools service:

```bash
systemctl status open-vm-tools
```

You should see that the service is running.

Press:

```text
q
```

to exit the status screen.

VMware Guest Tools provide features such as:

* Better display resizing
* Better mouse integration
* Clipboard integration
* Guest/host communication
* VMware filesystem integration
* Improved virtual hardware support

---

# 43. Install Kali Linux Large

The default Kali installation contains a useful selection of tools.

For a larger cybersecurity workstation, install:

```text
kali-linux-large
```

First update the repositories:

```bash
sudo apt update
```

Then install:

```bash
sudo apt install -y kali-linux-large
```

This installs a much larger collection of Kali security tools.

The installation may download a significant amount of data.

Make sure you have:

* Reliable internet connection
* Enough virtual disk space
* Enough free physical storage on the Mac

---

# 44. Clean Up After Kali Large Installation

After installation:

```bash
sudo apt autoremove -y
```

Then:

```bash
sudo apt clean
```

Reboot:

```bash
sudo reboot
```

---

# 45. Verify Kali Linux Large

Check whether the package is installed:

```bash
dpkg -s kali-linux-large
```

Look for:

```text
Status: install ok installed
```

You can also use:

```bash
apt list --installed 2>/dev/null | grep kali-linux-large
```

---

# 46. Verify ARM64 Architecture

Since this is an Apple Silicon VM, verify that Kali is running ARM64.

Run:

```bash
uname -m
```

The result should be:

```text
aarch64
```

You can also run:

```bash
dpkg --print-architecture
```

You should see:

```text
arm64
```

This confirms that Kali is running the ARM64 architecture.

---

# 47. Important ARM64 Tool Compatibility Note

Most common Kali Linux tools are available for ARM64.

Examples include:

```text
Nmap
Gobuster
John the Ripper
Hashcat
Metasploit
SQLMap
Nikto
Burp Suite
Wireshark
Hydra
Netcat
Python
GDB
Git
```

However, some cybersecurity tools or third-party binaries are only distributed for:

```text
x86_64
AMD64
```

Those tools may not run natively on Kali ARM64.

This is one of the main differences between:

```text
Windows Intel/AMD Kali VM
```

and:

```text
Apple Silicon Kali VM
```

For most TryHackMe, CTF, CPTC, Linux, networking, and general pentesting work, ARM64 Kali works well.

---

# 48. Verify Network Connectivity

Test basic internet connectivity:

```bash
ping -c 4 1.1.1.1
```

Then test DNS resolution:

```bash
ping -c 4 kali.org
```

Check network interfaces:

```bash
ip addr
```

Check routing:

```bash
ip route
```

You should have a VMware virtual network interface and a default route.

---

# 49. Verify Common Kali Tools

Check Nmap:

```bash
nmap --version
```

Check Gobuster:

```bash
gobuster version
```

Check John:

```bash
john --list=build-info
```

Check Hashcat:

```bash
hashcat --version
```

Check SQLMap:

```bash
sqlmap --version
```

Check Nikto:

```bash
nikto -Version
```

Check Metasploit:

```bash
msfconsole --version
```

Not every tool needs to be present for Kali to function.

These commands simply verify common packages.

---

# 50. Check Disk Space

Check filesystem usage:

```bash
df -h
```

Pay attention to:

```text
/
```

because Kali Large and cybersecurity tools can consume significant disk space.

You can also check APT cache usage:

```bash
sudo du -sh /var/cache/apt
```

Clean it with:

```bash
sudo apt clean
```

---

# 51. Check Memory

Check available RAM:

```bash
free -h
```

If Kali regularly runs out of RAM, shut down the VM and increase its memory allocation in VMware Fusion.

---

# 52. Check CPU

Run:

```bash
lscpu
```

You should see an ARM-based processor architecture.

You can also run:

```bash
nproc
```

to see how many virtual CPU cores Kali can access.

---

# 53. Shared Folders

VMware Fusion can share folders between macOS and Kali.

Open:

```text
Virtual Machine
→ Settings
→ Sharing
```

You can enable shared folders if needed.

For security-sensitive labs, avoid sharing your entire home directory.

Instead, create a dedicated folder such as:

```text
~/VM_Shared
```

or:

```text
~/Kali_Shared
```

Share only that folder with Kali.

---

# 54. Clipboard Sharing

VMware Guest Tools can allow clipboard sharing between macOS and Kali.

This makes it easier to copy commands such as:

```bash
nmap -sC -sV TARGET
```

from macOS notes into Kali.

If clipboard sharing is unavailable, verify:

```bash
systemctl status open-vm-tools
```

and confirm that:

```text
open-vm-tools-desktop
```

is installed.

---

# 55. USB Devices

VMware Fusion can attach USB devices to Kali.

When connecting a USB device, VMware may ask whether it should connect to:

```text
Mac
```

or:

```text
Kali Linux
```

Select Kali only when the VM needs direct access to that device.

Examples might include:

* USB storage
* Hardware security keys
* Supported USB network adapters
* Lab hardware

---

# 56. Apple Silicon and Wi-Fi Adapters

The Mac's built-in Wi-Fi interface generally cannot simply be passed directly into Kali as a raw wireless adapter for monitor mode.

If you need Kali to perform authorized wireless security labs requiring:

```text
Monitor Mode
Packet Injection
```

you may need a compatible external USB Wi-Fi adapter that:

1. Supports monitor mode
2. Supports packet injection
3. Has Linux ARM64 driver support
4. Can be passed through VMware Fusion

Always verify chipset and ARM64 driver compatibility before purchasing a Wi-Fi adapter.

---

# 57. Recommended Final Configuration

A good general-purpose Apple Silicon Kali VM is:

```text
Host:             Apple Silicon Mac
Hypervisor:       VMware Fusion Pro
Guest OS:         Kali Linux ARM64
Architecture:     ARM64 / aarch64
RAM:              6–8 GB
CPU:              4 Cores
Storage:          100 GB
Network:          NAT / Share with my Mac
Desktop:          Xfce
VMware Tools:     open-vm-tools
Toolset:          kali-linux-large
```

---

# 58. Recommended Setup by Mac RAM

## 8 GB Mac

```text
Kali RAM:     4 GB
CPU:          2 Cores
Disk:         80–100 GB
Network:      NAT
```

## 16 GB Mac

```text
Kali RAM:     6 GB
CPU:          4 Cores
Disk:         100 GB
Network:      NAT
```

## 24 GB Mac

```text
Kali RAM:     8 GB
CPU:          4 Cores
Disk:         100–120 GB
Network:      NAT
```

## 32 GB+ Mac

```text
Kali RAM:     8–12 GB
CPU:          4–6 Cores
Disk:         100–150 GB
Network:      NAT
```

---

# 59. Recommended Setup for CTF / TryHackMe / CPTC

For cybersecurity practice:

```text
Guest:        Kali Linux ARM64
RAM:          8 GB
CPU:          4 Cores
Storage:      100 GB
Network:      NAT
Desktop:      Xfce
Toolset:      kali-linux-large
```

This is a good starting setup for:

* TryHackMe
* Hack The Box
* CPTC practice
* CTF competitions
* Network enumeration
* Web application testing
* Linux privilege escalation
* Password cracking practice
* Forensics
* Reverse engineering
* General security labs

---

# 60. Useful Kali Commands

## Update Kali

```bash
sudo apt update
sudo apt full-upgrade -y
sudo apt autoremove -y
sudo apt clean
```

## Install a Package

```bash
sudo apt install PACKAGE_NAME
```

## Search for a Package

```bash
apt search PACKAGE_NAME
```

## Remove a Package

```bash
sudo apt remove PACKAGE_NAME
```

## Check Kali Version

```bash
cat /etc/os-release
```

## Check CPU Architecture

```bash
uname -m
```

## Check Debian Architecture

```bash
dpkg --print-architecture
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

## Check Storage

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

# 61. Useful Links

## VMware Fusion Pro

https://www.techspot.com/downloads/2755-vmware-fusion-mac.html

## Official Kali Linux Downloads

https://www.kali.org/get-kali/

## Kali VMware Apple Silicon Documentation

https://www.kali.org/docs/virtualization/install-vmware-silicon-host/

## Kali Virtualization Documentation

https://www.kali.org/docs/virtualization/

## Kali VMware Guest Documentation

https://www.kali.org/docs/virtualization/install-vmware-guest-vm/

## Kali Metapackages

https://www.kali.org/docs/general-use/metapackages/

---

# 62. Quick Installation Checklist

## Check Mac

* [ ] Confirm Mac uses an Apple M-series processor
* [ ] Run `uname -m`
* [ ] Confirm result is `arm64`
* [ ] Make sure enough storage is available

## VMware Fusion

* [ ] Download VMware Fusion Pro
* [ ] Install VMware Fusion Pro
* [ ] Open VMware Fusion
* [ ] Approve necessary macOS permissions

## Kali

* [ ] Open official Kali download page
* [ ] Select Installer Images
* [ ] Select Apple Silicon / ARM64
* [ ] Download the ARM64 installer ISO
* [ ] Do NOT download AMD64
* [ ] Verify SHA256 hash

## Create VM

* [ ] Create new VMware Fusion VM
* [ ] Choose Install from Disk or Image
* [ ] Select Kali ARM64 ISO
* [ ] Select Linux
* [ ] Select Debian ARM64
* [ ] Name Kali VM
* [ ] Configure storage

## Hardware

* [ ] Configure 6–8 GB RAM
* [ ] Configure approximately 4 CPU cores
* [ ] Configure approximately 100 GB storage
* [ ] Set networking to NAT / Share with my Mac
* [ ] Confirm Kali ARM64 ISO is connected

## Kali Installation

* [ ] Boot Kali
* [ ] Select Graphical Install
* [ ] Choose language
* [ ] Choose keyboard
* [ ] Configure hostname
* [ ] Create user
* [ ] Configure password
* [ ] Use guided virtual disk partitioning
* [ ] Install Xfce
* [ ] Install default Kali toolset
* [ ] Install GRUB
* [ ] Reboot

## Post Installation

* [ ] Boot installed Kali
* [ ] Update package repositories
* [ ] Run full system upgrade
* [ ] Install `open-vm-tools`
* [ ] Install `open-vm-tools-desktop`
* [ ] Reboot
* [ ] Install `kali-linux-large`
* [ ] Reboot
* [ ] Verify `aarch64`
* [ ] Verify networking
* [ ] Verify DNS
* [ ] Verify common security tools
* [ ] Check available storage

---

# 63. Final Update Command

Once Kali is installed, use:

```bash
sudo apt update
sudo apt full-upgrade -y
sudo apt autoremove -y
sudo apt clean
```

Reboot when required:

```bash
sudo reboot
```

---

# 64. Architecture Comparison

The most important difference between the Windows setup and Apple Silicon setup is the CPU architecture.

## Windows Intel/AMD

```text
Windows
   |
Intel / AMD x86_64 CPU
   |
VMware Workstation Pro
   |
Kali Linux AMD64
```

Use:

```text
kali-linux-XXXX.X-installer-amd64.iso
```

## Apple Silicon

```text
macOS
   |
Apple M-Series ARM64 CPU
   |
VMware Fusion Pro
   |
Kali Linux ARM64
```

Use:

```text
kali-linux-XXXX.X-installer-arm64.iso
```

---

# 65. Final Apple Silicon Setup

Your final architecture should look like:

```text
┌─────────────────────────────────┐
│              macOS              │
│                                 │
│      Apple Silicon M-Series     │
│           ARM64 CPU             │
├─────────────────────────────────┤
│       VMware Fusion Pro         │
│                                 │
│            NAT Network          │
├─────────────────────────────────┤
│      Kali Linux ARM64 VM        │
│                                 │
│  RAM:        6–8 GB             │
│  CPU:        4 Cores            │
│  Disk:       100 GB             │
│  Desktop:    Xfce               │
│  Tools:      kali-linux-large   │
│  VMware:     open-vm-tools      │
└─────────────────────────────────┘
```

---

# Notes

* Apple Silicon requires **Kali ARM64**, not AMD64.
* ARM64 may also appear as `aarch64` inside Linux.
* Use VMware Fusion rather than VMware Workstation on macOS.
* NAT / **Share with my Mac** is a good default network configuration.
* Keep Kali updated before starting labs.
* Install `kali-linux-large` if you want a broader collection of Kali tools.
* Not every third-party x86_64 security tool has an ARM64 build.
* VMware Guest Tools improve display, clipboard, mouse, and host integration.
* Avoid sharing your entire macOS home directory with Kali.
* Keep important scripts, notes, CTF files, and projects backed up outside the VM.
* Only perform penetration testing on systems you own or have explicit authorization to test.
