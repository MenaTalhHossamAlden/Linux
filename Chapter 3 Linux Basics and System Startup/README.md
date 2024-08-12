**Partition:** a logical part of the disk.
**Filesystem:** a method of storing files and finding files in hard disk.

By dividing the hard disk into partitions, data can be grouped and separated as needed. When a failure or a mistake occurs only the data in the affected partition will be damaged, while data on the other partitions will likely survive.

# Boot Process

The process of initializing the system from when the computer is switched on until the user interface is fully operational.

The boot process has multiple steps, starting with the BIOS which triggers the bootloader to start up the linux kernel. From there the init RAM FS file system is invoked which triggers the init program to complete the startup process. 

**1. BIOS**: BIOS initialize the hardware including the screen and keyboard and test the main memory. This process is also called POST(Power-On Self Test) and passes control to the bootloader.

**2. Bootloader (e.g., GRUB, LILO)**: The bootloader is responsible for loading the Linux kernel and initial RAM disk or file system into memory. The bootloader allows the user to select the operating system (if multiple OSs are installed) and passes control to the selected OS.

**3:** the OS kernel takes over and initializes the system by setting up hardware, mounting filesystem, starting essential services, and presenting a login interface.

# The Filesystem Hierarchy Standard

Linux systems store their files according to standard layout called the Filesystem Hierarchy Standard (FHS).

- **Root Directory /**: The top-level directory in the Linux file system hierarchy. All other directories and files are under this root directory.

# Linux Installation: Install Source

Like other OSs, Linux distribution is provided on a removable media like USB drives, CDs, or DVDs. Most Linux distribution also supports booting a small image and downloading the rest of the system over the network. It is possible to perform install without using any local media. many installers can do an installation completely automatically using a configuration file to specify installation options. This file called "Kickstart file" for RHEL, "auto yes profile file" for SUSE, and "precede file" for Debian.

# Install distribution on VM under VMware hypervisor

**1. Booting the VM from the ISO:**
ISO Attachment: The ISO image is attached to the VM as a virtual CD/DVD drive.
Boot Sequence: When the VM starts, it checks for bootable media, finds the ISO, and begins the boot process.

**2. Loading the Bootloader:**
Bootloader Execution: The bootloader is a small program located on the ISO. The VM loads this bootloader into memory (RAM) and executes it.
Bootloader Role: The bootloader's primary job is to load the operating system kernel into memory and pass control to it.

**3. Booting the OS Kernel:**
Kernel Loading: The bootloader loads the OS kernel from the ISO image into RAM.
Kernel Initialization: The kernel initializes the system, setting up hardware, memory management, and essential system services.

**4. Launching the Installer:**
Installer Start: After the kernel has initialized the basic system, it launches the installer program.
Installer Role: The installer provides a user interface (either graphical or text-based) that guides you through the OS installation process. This includes selecting language, partitioning the disk, configuring network settings, and more.

**5. Installing the OS and Packages:**
Installation Process: The installer copies the OS files from the ISO (or downloads them if necessary) to the VM's virtual hard drive.
Package Installation: Any additional software packages or updates required by the OS are also installed at this stage.
Configuration: The installer applies the selected configurations (such as user accounts, timezone, and network settings) to the new OS installation.

**6. Finalization and Reboot:**
Completing the Installation: Once all files are copied, packages installed, and configurations applied, the installer finishes the setup.
Reboot: The VM is then rebooted, and this time, it boots from the newly installed OS on the virtual hard drive, rather than from the ISO.
