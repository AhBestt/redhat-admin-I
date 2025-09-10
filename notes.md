# Note
## Basic Command Line

Default user shell ending with dollar($) character: <br>
```bash
[user@host ~]$
```
But if you running as the superuser ending with hash(#) character: <br>
```bash
[root@host ~]#
```
To log in to a Remote System <br>
```bash
ssh remoteuser@remotehost
```
To log in to a remote system with key <br>
```bash
ssh -i <key.pem> remoteuser@remotehost
```
To log out from a Remote System <br>
```
exit
```
To type more than one command on single line, user semicolon (;) <br>
```
command1 ; command2
```
To display current date and time <br>
```
date
```
`date +%R` to show only time <br>
`date +%x` to show mm/dd/yyyy <br>

`passwd` command changes the current user's password <br>

To view the Contents of Files use `cat` command <br>
example <br>
```
cat /etc/passwd
```

Add file names to the `cat` commands to display multiple files <br>
```
cat file1 file2
```

To display the beginning or the end of file use `head` and `tail` commands <br>
By default these commands display 10 lines of the file. <br>
```
head /etc/passwd
tail /etc/passwd
```
To specify a different number of lines use -n option <br>
```
tail -n 3 /etc/passwd
```
To create users on the system use `useradd`command <br>

To display the command history use `history` <br>
and use `!number` to run command in the history <br>
```
history
...output omitted...
29 ls /etc
30 history

!29
...output omitted...
ls /etc
...output omitted...
```

___

## Linux File-system Hierarchy
The root directory `/` is at the top of the file-system hierarchy <br>
| Location | Purpose |
|:-----|:-----|
|/boot    | To start the boot process |
|/dev| Special devie files the system uses to access hardware|
|/etc| System specific configuration files.|
|/home| Home directory, users store their data and configuration files |
|/root| Home directory for administrative superuser, root|
|/run | Runtime data for processses that started since the last boot|
|/tmp| Space for temporary file. Files that are not accessed, changed or modified for 10 days are deleted|
|/usr| Installed software, shared libraries, etc.
||/usr/bin: user commands|
||/usr/sbin: System administration commands|
||/usr/local: Locally customized software|
|/var| System specific variable data should persist between boot|

___
## Navigating Paths in the File System
To displays the full path name of the current working use `pwd` command <br>
To lists directory contents use `ls` command <br>
with option `-l` (long listing format),`-a` (all files, including hidden files) <br>
to change shell's current working directory use `cd` command <br>
```
cd /home/user/Documents
cd Videos
cd
```
Create empty files by `touch` command <br>
```
touch Docemets/test1.txt
```
___

## Manage Files with command line
To create one or more directories. use the `mkdir` command <br>
```
mkdir ProjectA ProjectB ProjectC
```
-  If the directory exists, or a parent directory doesn't exist then the command failed <br>
- `-p` (parent) option creates any missing parent directories for the requested destination <br>
```
mkdir -p Test/chapter1 Test/chapter2 Test/chapter3
```
To copy file to a directory use `cp` command <br>
```
cp test1.txt test2.txt
```
To move files and directories from one location to another use `mv` command <br>
and also can rename by the same command <br>
```
mv test1.txt test3.txt
```
To remove files and directories use `rm` command
```
rm test2.txt
rmdir <directory_name>
```
- `rmdir` command to remove directories, `-r` option to remove non-empty directories. <br>

You can create multiple file names that point to the same file. These file names are called *links* <br>
- hard link
  -> when you create hard link to a file, you create another name that points to the same data. <br>
  -> Even if the original file is deleted, you can still access the contents of the file provided that at least one other hard link exists. <br> 
  -> You can use `ln` command to create hard link <br>
  ```
  ln newfile.txt /tmp/newfile-hardlink.txt
- soft link <br>
  -> You can create soft link by `ln` command with option `-s` <br>
  -> Can link 2 files on different file systems (hard link can't) <br>
  -> Can point to a directory or special file not just to a regular file like hard link <br>

Open file for editing by using the `vi` command <br>
```
vi filename
```
___

## Managing Local Users and Groups
User Types in Linux Systems <br>
1. Superuser: <br>
   The superuser name is `root` UID is 0. The superuser has full systemc access
2. System user: <br>
   Users do not interactively login with a system user account, only used by processes that provide supporting services.
3. Regular user: <br>
  For their day-to-day work. Have limited access to the system. <br>
  use `id` command to show information about the currently logged-in user. <br>

To view process information use `ps` command. By default only display processes that are running with the same UID as the current user. <br>

By default, systems use the `/etc/passwd` file to store information about local users. <br>
By default, systems use the `/etc/group` file to store information about local groups. <br>

To switch user accounts run `su` command: <br>
example switch from user1 to user2 <br>
```
su - user2
```
example switch to root <br>
```
su -
```

To configuring sudo <br>
`/etc/sudoers` file is the main configuration file for the `sudo` command <br>
example from `/etc/sudoers` file enables sudo access for `wheel` group members: <br>
```
%wheel  ALL=(ALL:ALL)  ALL
```
- %wheel is the user or group. `%` before the `wheel` word specifies a group. <br>

You can also setup `sudo` to allow a user to run command as another user without entering their password, by using the `NOPASSWD: ALL` command: <br>
```
test  ALL=(ALL) NOPASSWD: ALL
```

Creating Users <br>
```
useradd <username>
```

Deleting Users <br>
```
userdel <username>
```
`userdel` command removes the username from `/etc/passwd` file, but leaves the user's home directory <br>
to remove the user's home directory use `-r` option
|Warning|
|:----|
|When you remove a user without `-r` option an unassigend UID now owns the user's files. If you create a user and that user is assigned the deleted user's UID, then the new account owns those files|

To Setting passwords <br>
`passwd <username>`

To Creating group <br>
`groupadd` -g option to specifies a GID for the group to use.
```
groupadd -g 10000 group01
```

To deleting group <br>
use `groupdel` command <br>
```
groupdel <groupname>
```

To changing Group Membership from the Command Line <br>
use the `usermod -g` command to change a user's default primary group <br>
```
usermode -g <groupname> <username>
```

To configuring Password Aging <br>
use `change` command <br>
example
```
change -m 0 -M 90 -W 7 -I 14 sysadmin
```
- -m = minimum age ( 0 day)
- -M = maximum age (90 days)
- -W = warning period (7 days)
- -I = inactivity period (14 days)
- sysadmin = username

You also can change the default password aging configuration in the `/etc/login.defs` file. <br>
`Pass_MAX_DAYS`, `PASS_MIN_DAYS`, `PASS_WARN_AGE` sets the default maximum, minimum and warning period of password. <br>


___
## Controlling Access to Files

example when run command `ls` <br>
drwxr-xr-x <br>
first character: <br>
- `-` is a regular file.
- `d` is a directory.
- `l` is a symbolic link.
- `c` is a character device file.
- `b` is a block device file.
- `p` is a named pipe file.
- `s` is a local socket file.
The next 9 characters represent the file permissions. These characters are interpreted as 3 sets of 3 characters: <br>
- First set are permissions that apply to the file owner.
- Second set are for the file's group owner.
- The last set applies to all other (world) users.

|Permission|Effect on files|
|:----|:----|
|`r` (read)| File contents can be read|
|`w` (write) | File contents can be changed|
|`x` (execute) | File can be executed as commands|

To change file and directory permissions use `chmod` command <br>
```
chmod Who/What/Which file|directory
```

Who is the class of user <br>
|Who|User class|
|:---|:---|
|`u`| user|
|`g`|group|
|`o`|other|
|`a`|all|

What is the operator that modifies permissions <br>
|What|Operation|
|:---|:---|
|`+`|add|
|`-`|remove|
|`=`|set exactly|

Which is the mode and specifies which permissions to set for the files or directories <br>
|Which|Mode|
|:---|:---|
|`r`|read|
|`w`|write|
|`x`|execute|
|`X`|special execute|

example command <br>
```
chmod go-rw document.pdf
chmod a+x script.sh
chmod -R g+rwx /home/user/folder
```
`-R` option to recursively set permissions on the files in an entire directory tree <br>

You can also change permission with the octal method <br>
```
chmod #### file|directory
```


start with 0 <br>
to add read add 4 <br>
add write add 2 <br>
add execute add 1 <br>

example <br>
```
chmod 644 files.txt
chmod 750 sample.txt
```

Change file and directory user or group ownership
