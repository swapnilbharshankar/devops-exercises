# Linux

## Linux Master Application

A completely free application for testing your knowledge on Linux.
Disclaimer: developed by repository owner

<a href="https://play.google.com/store/apps/details?id=com.codingshell.linuxmaster"><img src="../../images/linux_master.jpeg"/></a>

- [Linux](#linux)
  - [Linux Master Application](#linux-master-application)
  - [Linux Exercises](#linux-exercises)
    - [Basics](#basics)
  - [Linux Questions](#linux-questions)
    - [Linux 101](#linux-101)
    - [I/O Redirection](#io-redirection)
    - [Filesystem Hierarchy Standard](#filesystem-hierarchy-standard)
    - [Permissions](#permissions)
    - [Scenarios](#scenarios)
    - [Systemd](#systemd)
    - [Troubleshooting and Debugging](#troubleshooting-and-debugging)
      - [Scenarios](#scenarios-1)
    - [Kernel](#kernel)
    - [SSH](#ssh)
    - [Globbing & Wildcards](#globbing--wildcards)
    - [Boot Process](#boot-process)
    - [Disk and Filesystem](#disk-and-filesystem)
    - [Performance Analysis](#performance-analysis)
    - [Processes](#processes)
    - [Security](#security)
    - [Networking](#networking)
    - [DNS](#dns)
    - [Packaging](#packaging)
    - [DNF](#dnf)
    - [Applications and Services](#applications-and-services)
    - [Users and Groups](#users-and-groups)
    - [Hardware](#hardware)
    - [Namespaces](#namespaces)
    - [Virtualization](#virtualization)
    - [AWK](#awk)
    - [System Calls](#system-calls)
    - [Filesystem & Files](#filesystem--files)
    - [Advanced Networking](#advanced-networking)
    - [Memory](#memory)
    - [Distributions](#distributions)
    - [Sed](#sed)
    - [Misc](#misc-1)

## Linux Exercises

### Basics

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| Navigation | cd, pwd | [Exercise](exercises/navigation/README.md) | [Solution](exercises/navigation/solution.md)
| Create and Destroy | touch, rm, mkdir | [Exercise](exercises/create_remove/README.md) | [Solution](exercises/create_remove/solution.md)
| Copy Time | touch, cp, ls | [Exercise](exercises/copy/README.md) | [Solution](exercises/copy/solution.md)

## Linux Questions

### Linux 101

<details>
<summary>What is Linux?</summary><br><b>

[Wikipedia](https://en.wikipedia.org/wiki/Linux): "Linux is a family of open-source Unix-like operating systems based on the Linux kernel, an operating system kernel first released on September 17, 1991, by Linus Torvalds. Linux is typically packaged in a Linux distribution."

[Red Hat](https://www.redhat.com/en/topics/linux/what-is-linux): "Linux® is an open source operating system (OS). An operating system is the software that directly manages a system’s hardware and resources, like CPU, memory, and storage. The OS sits between applications and hardware and makes the connections between all of your software and the physical resources that do the work."

</b></details>

<details>
<summary>Explain what each of the following commands does and give an example on how to use it:

  * touch
  * ls
  * rm
  * cat
  * cp
  * mkdir
  * pwd
  * cd
</summary><br><b>

  * touch - update file's timestamp. More commonly used for creating files
  * ls - listing files and directories
  * rm - remove files and directories
  * cat - create, view and concatenate files
  * cp - copy files and directories
  * mkdir - create directories
  * pwd - print current working directory (= at what path the user currently located)
  * cd - change directory
</b></details>

<details>
<summary>What each of the following commands does?

  * cd /
  * cd ~
  * cd
  * cd ..
  * cd .
  * cd -
</summary><br><b>

  * cd / -> change to the root directory
  * cd ~ -> change to your home directory
  * cd -> change to your home directory
  * cd .. -> change to the directory above your current i.e parent directory
  * cd . -> change to the directory you currently in
  * cd - -> change to the last visited path
</b></details>

<details>
<summary>Explain each field in the output of `ls -l` command</summary><br><b>
It shows a detailed list of files in a long format. From the left:

* file permissions, number of links, owner name, owner group, file size, timestamp of last modification and directory/file name
</b></details>

<details>
<summary>What are hidden files/directories? How to list them?</summary><br><b>

These are files directly not displayed after performing a standard ls direct listing. An example of these files are .bashrc which are used to execute some scripts. Some also store configuration about services on your host like .KUBECONFIG. The command used to list them is, `ls -a`
</b></details>

<details>
<summary>What do > and < do in terms of input and output for programs?</summary><br><b>
They take in input (<) and output for a given file (>) using stdin and stdout.

`myProgram < input.txt > executionOutput.txt`
</b></details>

<details>
<summary>Explain what each of the following commands does and give an example on how to use it:

  * sed
  * grep
  * cut
  * awk
</summary><br><b>

  - sed: a stream editor. Can be used for various purposes like replacing a word in a file: `sed -i s/salad/burger/g`
  - grep: a search tool. Used to search, count or match a text in a file:
    - searching for any line that contains a word in a file: `grep 'word' file.md`
    - or displaying the total number of times a string appears in a file: `grep -c 'This is a string' file.md`
  - cut: a tool for cutting out selected portions of each line of a file:
    - syntax: `cut OPTION [FILE]`
      - cutting first two bytes from a word in a file: `cut -b 1-2 file.md`, output: `wo`
  - awk: a programming language that is mainly used for text processing and data extraction. It can be used to manipulate and modify text in a file:
    - syntax: awk [OPTIONS] [FILTER] [FILE]
extracting a specific field from a CSV file: awk -F ',' '{print $1}' file.csv, output: first field of each line in the file
</b></details>

<details>
<summary>How to rename the name of a file or a directory?</summary><br><b>

Using the `mv` command.
</b></details>

<details>
<summary>Specify which command would you use (and how) for each of the following scenarios 

  * Remove a directory with files
  * Display the content of a file
  * Provides access to the file /tmp/x for everyone
  * Change working directory to user home directory
  * Replace every occurrence of the word "good" with "great" in the file /tmp/y</summary><br><b>

  - `rm -rf dir`
  - `cat or less`
  - `chmod 777 /tmp/x`
  - `cd ~`
  - `sed -i s/good/great/g /tmp/y`
</b></details>

<details>
<summary>How can you check what is the path of a certain command?</summary><br><b>

  * whereis
  * which
</b></details>

<details>
<summary>What is the difference between these two commands? Will it result in the same output?

```
echo hello world
echo "hello world"
```
</summary><br><b>

The echo command receives two separate arguments in the first execution and in the second execution it gets one argument which is the string "hello world". The output will be the same.
</b></details>

<details>
<summary>Explain piping. How do you perform piping?</summary><br><b>

Using a pipe in Linux, allows you to send the output of one command to the input of another command. For example: `cat /etc/services | wc -l`
</b></details>

<details>
<summary>Fix the following commands:

  * sed "s/1/2/g' /tmp/myFile
  * find . -iname \*.yaml -exec sed -i "s/1/2/g" {} ;
</summary><br><b>

```
sed 's/1/2/g' /tmp/myFile  # sed "s/1/2/g" is also fine
find . -iname "*.yaml" -exec sed -i "s/1/2/g" {} \;
```
</b></details>

<details>
<summary>How to check which commands you executed in the past?</summary><br><b>

history command or .bash_history file 
  * also can use up arrow key to access or to show the recent commands you type
</b></details>

<details>
<summary>How do you schedule tasks periodically?</summary><br><b>

You can use the commands <code>cron</code> and <code>at</code>.
With cron, tasks are scheduled using the following format:

<code>*/30 * * * * bash myscript.sh</code> Executes the script every 30 minutes.

<minute> <hour> <day of month> <month> <day of week> <command to execute>

The tasks are stored in a cron file, you can write in it using <code>crontab -e</code>

Alternatively if you are using a distro with systemd it's recommended to use systemd timers.
</b></details>

<a name="questions-linux-redirection"></a>
### I/O Redirection

<details>
<summary>Explain Linux I/O redirection</summary><br><b>
  In Linux, IO redirection is a way of changing the default input/output behavior of a command or program. It allows you to redirect input and output from/to different sources/destinations, such as files, devices, and other commands.

Here are some common examples of IO redirection:
 * Redirecting Standard Output (stdout):
  <code>ls > filelist.txt</code>
* Redirecting Standard Error (stderr):
  <code>ls /some/nonexistent/directory 2> error.txt</code>
* Appending to a file:
  <code>echo "hello" >> myfile.txt</code>
* Redirecting Input (stdin):
  <code>sort < unsorted.txt</code>
* Using Pipes: Pipes ("|"):
  <code>ls | grep "\.txt$"</code>         
</b></details>

<details>
<summary>Demonstrate Linux output redirection</summary><br><b>

<code>ls > ls_output.txt</code>
</b></details>

<details>
<summary>Demonstrate Linux stderr output redirection</summary><br><b>

<code>yippiekaiyay 2> ls_output.txt</code>
</b></details>

<details>
<summary>Demonstrate Linux stderr to stdout redirection</summary><br><b>

<code>yippiekaiyay &> file</code>
</b></details>

<a name="questions-linux-fhs"></a>
### Filesystem Hierarchy Standard

<details>
<summary>In Linux FHS (Filesystem Hierarchy Standard) what is the <code>/</code>?</summary><br><b>

The root of the filesystem. The beginning of the tree.
</b></details>

<details>
<summary>What is stored in each of the following paths?

  - /bin, /sbin, /usr/bin and /usr/sbin
  - /etc
  - /home
  - /var
  - /tmp</summary><br><b>

  * binaries
  * configuration files
  * home directories of the different users
  * files that tend to change and be modified like logs
  * temporary files
</b></details>

<details>
<summary>What is special about the /tmp directory when compared to other directories?</summary><br><b>

`/tmp` folder is cleaned automatically, usually upon reboot.
</b></details>

<details>
<summary>What kind of information one can find in /proc?</summary><br><b>
 
It contains useful information about the processes that are currently running, it is regarded as control and information center for kernel.
</b></details>

<details>
<summary>What makes /proc different from other filesystems?</summary><br><b>
/proc is a special virtual filesystem in Unix-like operating systems, including Linux, that provides information about processes and system resources.
</b></details>

<details>
<summary>True or False? only root can create files in /proc</summary><br><b>

False. No one can create file in /proc directly (certain operations can lead to files being created in /proc by the kernel).
</b></details>

<details>
<summary>What can be found in /proc/cmdline?</summary><br><b>

The command passed to the boot loader to run the kernel
</b></details>

<details>
<summary>In which path can you find the system devices (e.g. block storage)?</summary><br><b>
  /dev
</b></details>

<a name="questions-linux-permissions"></a>
### Permissions

<details>
<summary>How to change the permissions of a file?</summary><br><b>

Using the `chmod` command.
</b></details>

<details>
<summary>What does the following permissions mean?:

  * 777
  * 644
  * 750</summary><br><b>

<pre>
777 - You give the owner, group and other: Execute (1), Write (2) and Read (4); 4+2+1 = 7.
644 - Owner has Read (4), Write (2), 4+2 = 6; Group and Other have Read (4).
750 - Owner has x+r+w, Group has Read (4) and Execute (1); 4+1 = 5. Other have no permissions.
</pre>
</b></details>

<details>
<summary>What this command does? <code>chmod +x some_file</code></summary><br><b>
It adds execute permissions to all sets i.e user, group and others
</b></details>

<details>
<summary>Explain what is setgid and setuid</summary><br><b>

* setuid is a linux file permission that permits a user to run a file or program with the permissions of the owner of that file. This is possible by elevation of current user privileges.
* setgid is a process when executed will run as the group that owns the file.
</b></details>

<details>
<summary>What is the purpose of sticky bit?</summary><br><b>
Its a bit that only allows the owner or the root user to delete or modify the file.
</b></details>

<details>
<summary>What the following commands do?

  - chmod
  - chown
  - chgrp</summary><br><b>

  * chmod - changes access permissions to files system objects
  * chown - changes the owner of file system files and directories
  * chgrp - changes the group associated with a file system object
</b></details>

<details>
<summary>What is sudo? How do you set it up?</summary><br><b>
sudo is a command-line utility in Unix-like operating systems that allows users to run programs with the privileges of another user, usually the superuser (root). It stands for "superuser do.

The sudo program is installed by default in almost all Linux distributions. If you need to install sudo in Debian/Ubuntu, use the command apt-get install sudo

</b></details>

<details>
<summary>True or False? In order to install packages on the system one must be the root user or use the sudo command</summary><br><b>

True
</b></details>

<details>
<summary>Explain what are ACLs. For what use cases would you recommend to use them?</summary><br><b>
</b></details>

<details>
<summary>You try to create a file but it fails. Name at least three different reason as to why it could happen</summary><br><b>

* No more disk space
* No more inodes
* No permissions
</b></details>

<a name="questions-linux-scenarios"></a>
### Scenarios

<details>
<summary>You would like to copy a file to a remote Linux host. How would you do?</summary><br><b>

There are multiple ways to transfer files between hosts. Personal opinion: use `rsync`
</b></details>


<a name="questions-linux-systemd"></a>
### Systemd

<details>
<summary>What is systemd?</summary><br>
<b>
Systemd is a daemon (System 'd', d stands for daemon).

A daemon is a program that runs in the background without direct control of the user, although the user can at any time
talk to the daemon.

systemd has many features such as user processes control/tracking, snapshot support, inhibitor locks..

If we visualize the unix/linux system in layers, systemd would fall directly after the linux kernel.<br>
Hardware -> Kernel -> <u>Daemons</u>, System Libraries, Server Display.
</b>
</details>

<details>
<summary>How to start or stop a service?</summary><br><b>

To start a service: `systemctl start <service name>`
To stop a service: `systemctl stop <service name>`
</b></details>

<details>
<summary>How to check the status of a service?</summary><br><b>

`systemctl status <service name>`
</b></details>


### Troubleshooting and Debugging

<details>
<summary>Where system logs are located?</summary><br><b>

/var/log
</b></details>

<details>
<summary>How to follow file's content as it being appended without opening the file every time?</summary><br><b>

tail -f <file_name>
</b></details>

<details>
<summary>What are you using for debugging CPU related issues?</summary><br><b>

<code>top</code> will show you how much CPU percentage each process consumes
</b></details>

#### Scenarios


### Kernel

<details>
<summary>What is a kernel, and what does it do?</summary><br><b>

The kernel is part of the operating system and is responsible for tasks like:

  * Allocating memory
  * Schedule processes
  * Control CPU
</b></details>

<details>
<summary>How do you find out which Kernel version your system is using?</summary><br><b>

`uname -a` command
</b></details>

<a name="questions-linux-ssh"></a>
### SSH

<details>
<summary>What is SSH? How to check if a Linux server is running SSH?</summary><br><b>

[Wikipedia Definition](https://en.wikipedia.org/wiki/SSH_(Secure_Shell)): "SSH or Secure Shell is a cryptographic network protocol for operating network services securely over an unsecured network."

[Hostinger.com Definition](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work): "SSH, or Secure Shell, is a remote administration protocol that allows users to control and modify their remote servers over the Internet."

An SSH server will have SSH daemon running. Depends on the distribution, you should be able to check whether the service is running (e.g. systemctl status sshd).
</b></details>

<details>
<summary>Why SSH is considered better than telnet?</summary><br><b>

Telnet also allows you to connect to a remote host but as opposed to SSH where the communication is encrypted, in telnet, the data is sent in clear text, so it doesn't considered to be secured because anyone on the network can see what exactly is sent, including passwords.
</b></details>

<details>
<summary>What is stored in <code>~/.ssh/known_hosts</code>?</summary><br><b>

The file stores the key fingerprints for the clients connecting to the SSH server. This fingerprint creates a trust between the client and the server for future SSH connections.
</b></details>

<details>
<summary>You try to ssh to a server and you get "Host key verification failed". What does it mean?</summary><br><b>

It means that the key of the remote host was changed and doesn't match the one that stored on the machine (in ~/.ssh/known_hosts).
</b></details>

<details>
<summary>What <code>ssh-keygen</code> is used for?</summary><br><b>

<code>ssh-keygen</code> is a tool to generate an authentication key pair for SSH, that consists of a private and a public key. It supports a number of algorithms to generate authentication keys : 
- dsa
- ecdsa
- ecdsa-sk
- ed25519
- ed25519-sk
- rsa (default)

One can also specify number of bits in key. Command below generates an SSH key pair with RSA 4096-bits :
```
$ ssh-keygen -t rsa -b 4096
```

The output looks like this:
```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/user/.ssh/id_rsa
Your public key has been saved in /home/user/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:f5MOGnhzYfC0ZCHvbSXXiRiNVYETjxpHcXD5xSojx+M user@mac-book-pro
The key's randomart image is:
+---[RSA 4096]----+
|        . ..+***o|
|         o o++*o+|
|        . =+.++++|
|         B.oX+. .|
|        S *=o+   |
|       . o oE.   |
|      . + + +    |
|       . = + .   |
|        .   .    |
+----[SHA256]-----+
```

One can check how many bits an SSH key has with :
```
$ ssh-keygen -l -f /home/user/.ssh/id_rsa
```

Output should look like this :
```
4096 SHA256:f5MOGnhzYfC0ZCHvbSXXiRiNVYETjxpHcXD5xSojx+M user@mac-book-pro (RSA)
```
It shows the key is RSA 4096-bits.

`-l` and `-f` parameters usage explanation :
```
-l          Show the fingerprint of the key file.
-f filename Filename of the key file.
```

Learn more : [How can I tell how many bits my ssh key is? - Superuser](https://superuser.com/a/139311)
</b></details>


<a name="questions-linux-wildcards"></a>
### Globbing & Wildcards


<details>
<summary>What is an exit code? What exit codes are you familiar with?</summary><br><b>

An exit code (or return code) represents the code returned by a child process to its
parent process.

0 is an exit code which represents success while anything higher than 1 represents error.
Each number has different meaning, based on how the application was developed.

I consider this as a good blog post to read more about it: https://shapeshed.com/unix-exit-codes
</b></details>

<a name="questions-linux-boot"></a>
### Boot Process

<details>
<summary>Tell me everything you know about the Linux boot process</summary><br><b>

Another way to ask this: what happens from the moment you turned on the server until you get a prompt
</b></details>

<details>
<summary>What is GRUB2?</summary><br><b>
</b></details>

<details>
<summary>What is Secure Boot?</summary><br><b>
</b></details>

<details>
<summary>What can you find in /boot?</summary><br><b>
</b></details>

<a name="questions-linux-disk-fs"></a>
### Disk and Filesystem

<details>
<summary>What is the difference between a soft link and hard link?</summary><br><b>

Hard link is the same file, using the same inode.
Soft link is a shortcut to another file, using a different inode.
</b></details>

<details>
<summary>True or False? You can create an hard link for a directory</summary><br><b>

False
</b></details>

<details>
<summary>True or False? You can create a soft link between different filesystems</summary><br><b>

True
</b></details>

<details>
<summary>True or False? Directories always have by minimum 2 links</summary><br><b>

True.
</b></details>

<details>
<summary>What happens when you delete the original file in case of soft link and hard link?</summary><br><b>
</b></details>


<details>
<summary>How would you check what is the size of a certain directory?</summary><br><b>

`du -sh`
</b></details>


<a name="questions-linux-performance-analysis"></a>
### Performance Analysis

<details>
<summary>How to check what is the current load average?</summary><br><b>

One can use `uptime` or `top`
</b></details>

<details>
<summary>You know how to see the load average, great. but what each part of it means? for example 1.43, 2.34, 2.78</summary><br><b>

[This article](http://www.brendangregg.com/blog/2017-08-08/linux-load-averages.html) summarizes the load average topic in a great way
</b></details>

<details>
<summary>How to check how much free memory a system has? How to check memory consumption by each process?</summary><br><b>

You can use the commands <code>top</code> and <code>free</code>
</b></details>


<a name="questions-linux-processes"></a>
### Processes

<details>
<summary>how to list all the processes running in your system?</summary><br><b>

The "ps" command can be used to list all the processes running in a system. The "ps aux" command provides a detailed list of all the processes, including the ones running in the background.
</b></details>

<a name="questions-linux-security"></a>
### Security



<a name="questions-linux-networking"></a>
### Networking


<a name="questions-linux-dns"></a>
### DNS

<details>
<summary>How to check what is the hostname of the system?</summary><br><b>

`cat /etc/hostname`

You can also run `hostnamectl` or `hostname` but that might print only a temporary hostname. The one in the file is the permanent one.
</b></details>

<details>
<summary>What the file <code>/etc/resolv.conf</code> is used for? What does it include?</summary><br><b>
</b></details>

<details>
<summary>What commands are you using for performing DNS queries (or troubleshoot DNS related issues)?</summary><br><b>

You can specify one or more of the following:

 * <code>dig</code>
 * <code>host</code>
 * <code>nslookup</code>
</b></details>


 
<a name="questions-linux-packaging"></a>
### Packaging

<details>
<summary>Why do we need package managers? Why not simply creating archives and publish them?</summary><br><b>

Package managers allow you to manage packages lifecycle as in installing, removing and updating the packages.<br>
In addition, you can specify in a spec how a certain package will be installed - where to copy the files, which commands to run prior to the installation, post the installation, etc.
</b></details>

<a name="questions-linux-dnf"></a>
### DNF

<details>
<summary>What is DNF?</summary><br><b>

From the [repo](https://github.com/rpm-software-management/dnf):

"Dandified YUM (DNF) is the next upcoming major version of YUM. It does package management using RPM, libsolv and hawkey libraries."

Official [docs](https://dnf.readthedocs.io/en/latest/)

</b></details>

<details>
<summary>How to look for a package that provides the command /usr/bin/git? (the package isn't necessarily installed)</summary><br><b>

dnf provides /usr/bin/git
</b></details>

<a name="questions-linux-apps-and-services"></a>
### Applications and Services

<details>
<summary>What types of web servers are you familiar with?</summary><br><b>

Nginx, Apache httpd.
</b></details>

<a name="questions-linux-users-and-groups"></a>
### Users and Groups

<details>
<summary>How do you create users? Where user information is stored?</summary><br>

Command to create users is `useradd` 

Syntax:
`useradd [options] Username`

There are 2 configuration files, which stores users information

1. `/etc/passwd` - Users information like, username, shell etc is stored in this file 

2. `/etc/shadow` - Users password is stored in encrypted format 
</details>

<details>
<summary>Which file stores information about groups?</summary><br>

`/etc/groups` file stores the group name, group ID, usernames which are in secondary group.
</details>

<details>
<summary>How do you change/set the password of a user?</summary><br>

`passwd <username>` is the command to set/change password of a user.
</details>

<details>
<summary>Which file stores users passwords? Is it visible for everyone?</summary><br>

`/etc/shadow` file holds the passwords of the users in encrypted format. NO, it is only visible to the `root` user
</details>


<details>
<summary>What information is stored in /etc/passwd? explain each field</summary><br>

`/etc/passwd` is a configuration file, which contains users information. Each entry in this file has, 7 fields,

`username:password:UID:GID:Comment:home directory:shell`

`username` - The name of the user.

`password` - This field is actually a placeholder of the password field. Due to security concerns, this field does not contain the password, just a placeholder (x) to the encrypted password stored in `/etc/shadow` file.

`UID` - User ID of the user.

`GID` - Group ID 

`Comment` - This field is to provide description about the user.

`home directory` - Abousulte path of the user's home directory. This directory gets created once the user is added.

`shell` - This field contains the absolute path of the shell that will be used by the respective user.
</details>

<details>
<summary>How to add a new user to the system without providing him the ability to log-in into the system?</summary><br><b>

`adduser user_name --shell=/bin/false --no-create-home`
You can also add a user and then edit /etc/passwd.
</b></details>

<details>
<summary>How to switch to another user? How to switch to the root user?</summary><br><b>

su command.
Use su - to switch to root
</b></details>

<details>
<summary>What is the UID the root user? What about a regular user?</summary><br>

UID of root user is 0

Default values of UID_MIN and UID_MAX in `/etc/login.defs`
`UID_MIN` is `1000`
`UID_MAX` is `60000`

Actually, we can change this value. But UID < 1000 are reserved for system accounts.
Therefore, as per the default configuration, for regular user UID starts from `1000`. 
</details>

<details>
<summary>Explain what each of the following commands does:

  * useradd
  * usermod
  * whoami
  * id</summary><br><b>

  `useradd` - Command for creating new users 
  `usermod` - Modify the users setting
  `whoami`  - Outputs, the username that we are currently logged in
  `id`      - Prints the  
</b></details>


<a name="questions-linux-hardware"></a>
### Hardware

<details>
<summary>Where can you find information on the processor (like number of CPUs)?</summary><br><b>

/proc/cpuinfo

You can also use `nproc` for number of processors
</b></details>


<a name="questions-linux-namespaces"></a>
### Namespaces


<a name="questions-linux-virtualization"></a>
### Virtualization


<a name="questions-linux-system-calls"></a>
### System Calls


<a name="questions-linux-fs-files"></a>
### Filesystem & Files


<a name="questions-linux-advanced-networking"></a>
### Advanced Networking

</b></details>

<a name="questions-linux-memory"></a>
### Memory


<a name="questions-linux-distributions"></a>
### Distributions


<a name="questions-linux-sed"></a>
### Sed

<a name="questions-linux-misc"></a>
### Misc

<details>
<summary>List three ways to print all the files in the current directory</summary><br><b>

* ls
* find .
* echo *
</b></details>

<details>
<summary>How to count the number of lines in a file? What about words?</summary><br><b>

For these we can use `wc` command.

1. To count the number of lines in file
```wc -l```

2. To count the number of words in file
```wc -w```
</b></details>

<details>
<summary>What is the difference between man and info?</summary><br><b>

A good answer can be found [here](https://askubuntu.com/questions/9325/what-is-the-difference-between-man-and-info-documentation)
</b></details>

<details>
<summary>How to create your own environment variables?</summary><br><b>

`X=2` for example. But this will persist to new shells. To have it in new shells as well, use `export X=2`
</b></details>
