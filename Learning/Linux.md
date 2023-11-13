# History
BSD (Berkeley Software Distribution) --> FreeBSD, NetBSD, OpenBSD
# File Systems
Methods and structures that the OS uses to manage how data is stored, organized and accessed. 
Includes file naming, metadata, directories, folders, access rules, and privileges. 

Linux uses mount points whereas Windows uses Drive Letters as their mounting parameter. (C:\ vs /)
## Types of File Systems
### ext4
Great flash memory lifespan (utilizes <mark class="hltr-yellow">delayed allocation</mark> like xfs to prevent data fragmentation, however could potentially trigger some data loss).
Unallocated blocks are marked as such, and are skipped during disk checks wowow
Journal checksumming! 
Unfortunately it is difficult to detect data corruption. 
### xfs 
64bit
Performs well on large files and high degrees of concurrency (parallel I/O operations; designed based off allocation groups).
Also utilizes delayed allocation
Written in B+ trees, which is a lot more efficient. 
### btrfs 
Based on the copy-on-write mechanism. (File system won't overwrite existing information as you're writing - new data is written elsewhere.)
Has volume management built in (ext4 doesn't have this! it's just a filesystem.)
### NTFS 
This is the Windows file system. Allows users to apply compression. 
Uses compact OS to compress the entire system partition and writes in continuously allocated chunks
## Commands
| Command | Action |
| --- | --- |
|`mkfs`|make file system|
| `$ findmnt` | lists all mounted file systems | 
| `umount /dev/sda2` | unmounts a file system | 
| `mount /dev/sda1 /mnt` | mounts a file system (mounts sda1 at /mnt| 
| `dir_index` | speeds up name lookups in large directories |
[systemd](#Components)
# Partitioning 
Creating one or more separate regions on secondary memory so each region can be managed separately. 
Any block device (usually a disk, partition or array) is called a **volume**. 
## Partition Tables
Describes how the storage is divided. Also called a partition map. 
### Master Boot Record 
Contains the OS bootloader and the partition table, located in first 512 bytes. Usually used under BIOS systems. 
It's not actually in a partition - precedes it. 
Partition table usually consists of: 
- **Primary** - limited to 4 per disk, bootable. 
- **Extended** - replaces a primary partition if you need more than 4 partitions. 
	- Logical (named sda5, sda6 etc. )
Required if you want to dual boot using BIOS. 
### GPT (GUID Partition Table)
Typically used by Linux; utilizes GUID (Globally unique identifiers) to name and organize partitions. 
At the start of the GUID, there is a little bit of Protected MBR for GPT-unaware software. 
Required if you want to dual boot using UEFI mode.
## Discrete Partitions
Separates out the path of the partition and can be shared between operating systems. 
## fstab

# Systemd
System and service manager and starts the rest of the system. Systems include: daemon, mount points, devices and sockets. 
## Unit files
`unit` refers to any resource that the system knows how to operate on and manage.
When a new unit is downloaded, it is typically installed onto `/lib/systemd/system`. Unit files in this directory should not be edited, but instead overridden. 

`.service` is a service. lol. 
`.socket` is a socket... will always have a service associated with it. 
`.device` is a device determined to need systemd.
`.mount` is a mountpoint. Named after the mountpath with / instead of -. 
`.target` used to provide synchronization states when booting up or changing states. 
`.snapshot` are not permanent and used for temporary rollbacks. 

`systemctl` if you do not specify things, it will assume that you are looking for a service. 
### Locations
Two main ones
`/usr/lib/systemd/system/` - units provided by installed packages.
`/etc/systemd/system/` - units installed by system administrator. 
### Writing Unit Files
Not sure if I'm going to need this but if I do: https://wiki.archlinux.org/title/Systemd#Writing_unit_files
## Components 
| Command | Action |
| --- | --- | 
|`kernel-install` | used to move kernels to the boot partition.|
|`systemd-boot` |the UEFI boot manager.|
|`systemd-logind` |session management.|
|`systemd-networkd` |network configuration management|
| `systemd-timesyncd` | system time synchronization across network|
|`systemd-journal`|system logging| 
## Power management
`polkit` used for power management as an unprivileged user. 

| Command | Action |
| --- | --- |
| `systemctl reboot` | shut down and reboot the system | 
| `systemctl poweroff` | shut down and power off the system | 
| `systemctl suspend` | suspend the system | 
| `systemctl hibernate` | hibernates the system lol |
## Other
To run have system services run *after* the network is running, edit the `.services` file to include:
![[Pasted image 20231103102801.png]]
To enable installed units by default see: https://wiki.archlinux.org/title/Systemd#Enable_installed_units_by_default
# Commands
## General
### echo
`echo` is a command to output strings given to it as arguments. 
`echo [option] [string]`

| Command | Action |
| --- | --- |
|`\n`|vertical spaces (aka break)|
|`\t` | horizontal spaces|
|`\v` | vertical tab spaces (break + tab)|
|`>>` inside string| store string to a file (>> name.txt ; output is saved to a file instead)|
|`cat [file]`|displays the txt file|
|`echo $user`|displays the name of the user|
|`echo "This is the list of directories and files on this system: $(ls)"`| displays list of all directories and files on the system. Also can use below|
[display all directories and files on the system](#Commands)
## System Checks
`fsck` command used to conduct **file system checks** (check the consistency of a file system). Only on **ext4** or ext3. 
Can be used to repair corrupted file systems in situations where system fails to boot or partitions cannot be mounted. 
````sh
fsck [OPTIONS] [FILESYSTEM]
````
Only users with root or `sudo` access can clear the buffer. 
Never run `fsck`on a mounted partition, make sure to <mark class="hltr-yellow">unmount it first.</mark>

## File Systems
`pacman -Syu`system update 

(Single dash - each letter means something )
(Double dsh -- each word means something )

# Terminal 
good resource https://swcarpentry.github.io/shell-novice/03-create.html 
`ctrl+alt+T`
`ctrl-c` means cancel
`ctrl-shift-c` copy
`ctrl-w` delete one word
`&` run in background (detach from current task)

`sudo` run as super user
`super user`
`$` user
`#` root (superuser)

`ls` lists everything inside
`mv` move/rename
`mkdir` make a directory and everything above it
`touch` adds a new file in current directory
`rm -r `

`sudo systemctl re`
`pacman -Q` lists all user installed packages

`chsh` used to change user shell
## zsh
`zsh-newuser-install -f` if I want to run the new user setup in the future
# Other
highlight and middle click pastes the highlight!!! wowowie
`sh /etc/cron.daily/backup` runs my website
`Meta+F8` virtual desktop! 

