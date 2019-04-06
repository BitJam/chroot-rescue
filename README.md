# Chroot Rescue System

These programs are meant to supplement the fehlix live rescue
system.  The main thing is these allow you to get into a system
even if its initrd.img is broken.  It also let's you get into
multiple systems without rebooting.

If it has a problem identifying a Linux distro, please let me
know and (ideally) show me how to correctly identify that system.


## chroot-rescue

Chroot into a Linux file system to perform repairs or to poke
around.

```
Usage: chroot-rescue [options] <directory>  [[--] <command> [<args>]]
Bind Mount /sys /proc and /dev file and under <directory>.  Mount
run/ as tmpfs and then chroot into that directory using a command.

If <command> is given we try to find that command under the directory
and run it in the chroot.  Otherwise we look for /bin/bash and then
/bin/sh and run the first one that is found.

Options:
 -a  --add-prompt=<str>  Add <str> to top of prompt
  -h --help              Show this help
  -n --no-x              Don't allow Xwindows applications to launch
     --pause             Pause before normal exit
  -p --pretend           Don't actually execute commands
  -P --prompt=<str>      Use this string as the prompt
  -q --quiet             Only print error messages
  -t --title=<str>       Set the window title while in the chroot
  -u --umount            Umount all subdirectories of the given directory
  -V --verbose           Show commands that get executed
  -v --version           Show version and exit

```

## chroot-rescue-select

The chroot-rescue-select program will offer to chroot into any
Linux file system mounted under a directory (default /media).
The --scan option will cause it to mount all Linux filesystems
under the directory (if they are not already mounted there).

![chroot-recue-select screenshot](/images/chroot-rescue-select-02.png)

```
Usage: chroot-rescue-select [<options>]
Look for all Linux systems under the top directory (/media).
Then provide a menu to chroot into any of the Liux systems.

Options:
  -C  --color=<xxx>       Set color scheme to off|low|low2|bw|dark|high
  -d  --dir=<directory>   Directory to look for linux systems under
                          Default: /media
  -h  --help              Show this usage
  -m  --menu              Output menu information then exit
  -s  --separator=<x>     Character to separate columns of data
                          Default: \t
  -v  --version           Show the version number and date
```

## unpack-initrd

Unpack and repack our live initrd file or a Debian initrd file.

```
Usage:  unpack-initrd [options]

Unpack and repack the live initrd.gz for antiX and MX.  Also unpack
and repack Debian initramfs files.  Supports the following forms of
compression: bz2, gzip, lz4, lzip, lzma, xz (assuming the associated
(de)compression tool is available.  Also supports microcode
preambles.

Options:
  -C  --clear            Delete directory before unpacking
  -c  --compress=<prog>  Use <prog> to recompress the initrd
  -d  --dir=<dir>        Unpack in <dir> instead of ./initrd
  -f  --file=<file>      Unpack <file> instead of:
                            /live/boot-dev/antiX/initrd.gz
      --from=<file>      Same as --file
  -l  --level=<N>        Set compression level: 1 (fastest) -- 9 (best)
                         (only applies to certain compression methods)
  -h  --help             Show this usage
  -n  --no-md5           Don't make a .md5 file in --repack mode
  -N  --no-microcode     Do not repack microcode
  -p  --pretend          Show commands without running them
  -r  --repack           Repack the initrd file
  -s  --silent           Only show error messages
  -q  --quiet            Say very little
  -V  --verbose          Show commands in addition to running them
  -v  --version          Show the version then exit
```
