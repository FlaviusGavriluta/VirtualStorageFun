# Virtual Storage Fun

## Story

Your boss asked you to create some important, top secret documents on a virtual disk.
You've raised your eyebrows and said _wut?_ ... then a few things happened and certain salaries and overtimes were mention, and finally you said _OK!_
She said _virtual machines deserved virtual disks!_ anyway.
So let's giddy up and learn about disks, formatting and whatnot!

## What are you going to learn?

- Hierarchical filesystem structure
- Create and attach a virtual disk to a VM
- Disks/drives, volumes/partitions
- Few important file system formats (FAT32, NTFS and ext2, ext3, ext4) and which to use in Linux
- Check if a disk contains a filesystem and what kind
- Format and create a filesystem on a disk
- Mount-points, how to mount/unmount a formatted volume to mount-point
- Determining file types with a command, or visually, viewing file contents
- Changing owner of a file with `chown`
- How to switch between virtual terminals in VirtualBox

## Tasks

1. Create a virtual disk (`.vdi`) that you attach to a VM and format in order to create and share files with others.
    - A 4 MB large, fixed-size virtual disk is created in `.vdi` format
    - The disk is named in `<Lastname><Firstname>.vdi` format, e.g. if your name is John Smith then your disk should be named as `SmithJohn.vdi`

2. Attach the disk to your VM and prepare it for usage inside the guest OS.
    - The disk is attached to your VMs SATA storage controller

3. To be able to use a raw disk a filesystem must be created on it first.
    - A single volume is created on the attached virtual disk
    - An `ext4` filesystem is created on the volume

4. To actually do anything useful, like creating files on the disk or copying files onto it, it must be mounted at a mount point in your filesystem.
    - The volume is mounted at `/home/ubuntu/disk`
    - The mount point must be owned by `ubuntu:ubuntu`
    - The mount point's permissions must be `drwxr-xr-x`

5. Create files on the mounted volume.
    - A `.txt` file is created on the volume inside the `/home/ubuntu/disk` directory
    - The file is named in `<Lastname><Firstname>.txt` format, e.g. if your name is John Smith then your file should be named as `SmithJohn.txt`
    - The file is saved with UTF-8 encoding
    - The file's content is your name in `<Lastname>, <Firstname>` format, e.g. if your name is John Smith then the file contains `Smith, John`, or your name is Françoise Inès Bokmål-Szabó then it should contain `Bokmål-Szabó, Françoise Inès`
    - The file's owner must be `ubuntu:ubuntu`
    - The file must only be readable and writable by the `ubuntu` user and no one else

## General requirements

- Only US ASCII letters used in filenames (no numbers, no spaces or other characters like `-`), e.g. if your name is Françoise Inès Bokmål-Szabó (with two firstname and a compound surname) then you should name your `.txt` files like `BokmalSzaboFrancoiseInes.txt`

## Hints

- Try using a _virtual console_ to practice "living" in the terminal, without _copy-pasta_ and a mouse, and most importantly to know how to "get out" of a virtual console if you get into one accidentally :)
- Creating partitions is not of utmost importance right now, it’s enough if you wipe the whole disk and create a single partition on the whole disk
- To test whether a block device or disk (like `/dev/sda`, etc.) contains a filesystem or not, use `file` with the `-s` or `--special-files` flag
- **When you are reading background materials:**
  - [Add a hard drive in VBox 6](https://www.youtube.com/watch?v=y1RsHeFqZqw) (focus on the first 2 minutes only, the rest is about how to add and format the created disk inside a Windows guest machine)
  - [Drive, Disk, Volume, Partition, and Image](https://www.maketecheasier.com/difference-between-disk-drive-volume-partition-image/) (you may also read [this Q&A](https://unix.stackexchange.com/q/87300) about this topic and make sure to read the question and [focus on this answer](https://unix.stackexchange.com/a/87305) in particular)
  - [Unix Filesystem Hierarchy Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure) (focus only on getting an overview of a few important paths, locations in a Unix/Linux environment for future reference)
  - [Different colorss meaning in `ls`?](https://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-ls) (Make sure to read [this answer](https://askubuntu.com/a/17300))
  - [Since Ubuntu version 17 the of the virtual consoles changed a bit.](https://askubuntu.com/a/917386) Pressing _Ctrl-Alt-F2_ switches to the GUI and pressing _Ctrl-Alt-F3_ through _Ctrl-Alt-F6_ switches to text-based console

## Background materials

- <i class="far fa-video"></i> <i class="far fa-exclamation"></i> [Add a hard drive in VBox 6](https://www.youtube.com/watch?v=y1RsHeFqZqw)
- <i class="far fa-exclamation"></i> [Drive, Disk, Volume, Partition, and Image](https://www.maketecheasier.com/difference-between-disk-drive-volume-partition-image/)
- <i class="far fa-video"></i> [Linux File System Types](https://www.youtube.com/watch?v=g7OkSvioFlU)
- [Unix Filesystem Hierarchy Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)
- <i class="far fa-exclamation"></i> <i class="far fa-video"></i> [File System Mounting](https://www.youtube.com/watch?v=A8ITr5ZpzvA)
- <i class="far fa-book-open"></i> [Format a Linux Disk as Ext4](https://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/)
- [Create filesystems with `mkfs`](https://www.unixtutorial.org/how-to-use-mkfs/)
- <i class="far fa-exclamation"></i> [Chown Command in Linux (File Ownership)](https://linuxize.com/post/linux-chown-command/)
- <i class="far fa-book-open"></i> [`file` command in Linux](https://www.geeksforgeeks.org/file-command-in-linux-with-examples/)
- <i class="far fa-book-open"></i> [Manual pages for `file`](https://man7.org/linux/man-pages/man1/file.1.html)
- <i class="far fa-book-open"></i> [Different colorss meaning in `ls`?](https://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-ls)
- <i class="far fa-book-open"></i> [Linux Virtual Console and Terminal](https://www.computernetworkingnotes.com/linux-tutorials/linux-virtual-console-and-terminal-explained.html)
- <i class="far fa-video"></i> [Virtual Terminals Explained (`tty`)](https://www.youtube.com/watch?v=vAr9PM9dEtE)
- <i class="far fa-book-open"></i> [Switching between virtual terminals](https://askubuntu.com/a/49573)
- <i class="far fa-book-open"></i> [Virtual consoles from Ubuntu 17.](https://askubuntu.com/a/917386)
