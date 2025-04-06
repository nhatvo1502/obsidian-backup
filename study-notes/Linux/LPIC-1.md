# 101.2 Boot the system
*bootloader* 

# 1. BIOS
*BIOS* short for *Basic Input/Output System*, is a program stored in a non-volatile memory chip attached to the motherboard, executed every time the computer is powered on. This type of program is called *firmware* and its storage location is separate from the other storage devices the system may have.

*Bios* assumes that the first 440 bytes in the first storage device -- following the order defined in the BIOS configuration utility -- are the first stage of the bootloader (also called *bootstrap*). The first 512 bytes of a storage device are named the MBR (*Master Boot Record*) of storage devices using the standard DOS partition schema and, in addition to the first stage of the bootloader, contain the partition table. If the MBR does not contain the correct data, the system will not be able to boot, unless an alternative method is employed.

## Pre-operating steps to boot a system for BIOS:
1. The POST (*power-on self-test*) process is executed to identify simple hardware failures as soon as the machine is powered on.
2. The BIOS activates the basic components to load the system, like video output, keyboard and storage media.
3. The BIOS loads the first stage of the bootloader from the MBR (440 bytes of the first device, BIOS configuration utility)
4. The first stage of bootloader calls the second stage of bootloader, responsible for presenting boot options and loading the kernel

# 2. UEFI
UEFI, short for *Unified Extensible Firmware Interface* has some similar key points to BIOS. UEFI is also a firmware, but it can identify partitions and read many filesystems found in them. The UEFI does not rely on the MBR, taking into account only the settings stored in its non-volatile memory (*NVRAM*) attached to the motherboard. These definitions indicate the location of the UEFI compatible programs, called *EFI applications*, that will be executed automatically or called from a boot menu. EFI applications can be bootloaders, operating system selectors, tools for system diagnostics and repair, etc. They must be in conventional storage device partition and in a compatible filesystem. The standard compatible filesystems are FAT12, FAT16 and FAT32 for block devices and ISO-9660 for optical media. This approach allows for the implementation of much more sophisticated tools than those possible with BIOS.

The partition containing the EFI applications is called the *EFI System Partition* or just ESP. This partition must not be shared with other system filesystems, like the root filesystem or user data filesystems. The EFI directory in the ESP partition contains the applications pointed to by the entries saved in the NVRAM.

## Pre-operating steps to boot a system for UEFI:
1. The POST process is executed to identify simple hardware failures as soon as the machine is powered on.
2. The UEFI activates the basic components to load the system, like video output, keyboard and storage media.
3. UEFI's firmware reads the definitions stored in NVRAM to execute the pre-defined EFI application stored in the ESP partition's filesystem. Usually, the pre-defined EFI application is a bootloader.
4. If the pre-defined EFI application is a bootloader, it will load the kernel to start the operating system.

The UEFI standard also supports a feature called *Secure Boot*, which only allow the execution ò signed EFI applications, that is, EFI applications authorized by the hardware manufacturer. This feature increases the protection against malicious software, but can make it difficult to install operating systems not covered by the manufacturer's warranty.

# 3. Bootloader
The most popular bootloader for Linux in the x86 architecture is GRUB (*grand Unified Bootloader*). As soon as it is called by the BIOS or by the UEFI, GRUB displays a list of operating system available to boot. 

## How to access GRUB menu
Pressing and hold `Shift` during booting up with BIOS. In UEFI systems, the `ESC` key should be used instead.

## Popular kernel parameters:
**acpi** 
	Enables/disables ACPI support. acpi=off/on
**init**
	set alternative system initiator. For example, init=/bin/bash will set the Bash shell as the initiator. This means that a shell session will start just after the kernel boot process.
**system.unit**
	Sets the systemd target to be activated. For example, systemd.unit=graphical.target. Systemd also accepts the numberal runlevels as defined for *SysV*. To activate the runlevel 1, for example, it is only necessary to include the number 1 or the letter S (short for "single") as a kernel parameter.
**mem** 
	Sets the amount of vailable RAM for the system. This parameter is useful for virtual machines so as to limit how much RAM will be available to each guest. Using mem=512M will limit to 512 megabytes the amount of available RAM to a particular guest system.
**maxcpus**
	Limits the number of processors (or process cores) visible to the system in symmetric multi-processor machines. It is also useful for virtual machines. A value of 0 turns off the support for multi-process machines and has the same effect as the kernel parameter nosmp. The parameter maxpucs=2 will limit the number of processors available to the operating system to two.
**quite**
	Hides most boot messages.
**vga**
	Selects a video mode. The parameter vga=ask will show a list of the available modes to choose from.
**root**
	Sets the root partition, distinct from the one pre-configured in the bootloader. For example, root=/dev/sda3.
**rootflags**
	Mount options for the root filesystem.
**ro**
	Makes the initial mount of the root filesystem read-only.
**rw**
	Allows writing in the root filesystem during initial mount

Changing the kernel parameters is not usually required, but it can be useful to detect and solve operating system related problems. Kernel parameters must be added to the file /etc/default/grub in the line GRUB_CMDLINE_LINUX to make them persistent across reboots. A new configuration file for the bootloader must be generated every time /etc/default/grub changes, which is accomplished by the command grub-mkconfig -o /boot/grub/grub.cfg. Once the operating system is running, the kernel parameters used for loading the current session are available for reading in the file /proc/cmdline.



# 4. System Initialization

Apart from the kernel, the operating system depends on other components that provide the expected features. Many of these components are loaded during the system initialization process, varying from simple shell scripts to more complex service programs. Script are often used to perform short lived tasks that will run and terminate during the system initialization process. Services, also known as daemons, may be active all the time as they can be responsible for intrinsic aspects of the operating system.