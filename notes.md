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
