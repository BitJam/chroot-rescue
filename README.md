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
  -h --help            Show this help
  -n --no-x            Don't allow XWindows applications to launch
  -p --pretend         Don't actually execute commands
  -P --prompt=<str>    Add this string to the prompt
  -q --quiet           Only print error messages
  -u --umount          Umount all subdirectories of the given directory
  -v --verbose         Show commands that get executed

```

## chroot-rescue-select

Offer to chroot into any Linux file system mounted under a directory
(default /media).  The --scan option will cause it to mount all
Linux filesystems under the directory (if they are not already
mounted there).


```
Usage: chroot-rescue-select [<options>]
Look for all Linux systems under the top directory (/media).
Provide a menu of all systems found and chroot into the selected
one.

Options:
  -C  --color=<xxx>       Set color scheme to off|low|low2|bw|dark|high
  -d  --dir=<directory>   Directory to look for linux systems under
                          Default: /media
  -h  --help              Show this usage
  -m  --menu              Output menu information then exit
  -s  --scan              Scan all partitions for Linux systems
  -S  --separator=<x>     Character to separate columns of data
                          Default: \t
  -v  --version           Show the version number and date
```
