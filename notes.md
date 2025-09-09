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
