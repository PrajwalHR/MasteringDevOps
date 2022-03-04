# RHCSE
```
Ch1 - basics, fles, mounting,links,terminal redirectory, man
Ch2 - file system, partions
Ch3 - kernel, modprobe, /proc
Ch4 - Booting , Modifying Grub2 Persistent Parameters, 
      
```
# Chap1
#


# CD
How to go into the command
```
cd Desktop/
```
How to go back
```
cd ..
```

# Environment Variable 

name value pares that is stored that our programs can store 
```
env = It gives out all the "variables" set 
 How to use this varibales ?? eg:HOME
 => echo $HOME [the $ sign is imp][echo = it echos the vale of the varibale]


export = 

```
# move 


```
mv = move
or 
mv eg1.txt eg2.txt = it moves the file or rename it 
changing the entry
" mv 'what we need to move' 'where we need to move/' "
```

# Creat File 
```
touch eg1.txt

#touch ______ it creat a empty file 
```
File inside dir
```
touch eg1/newfile.txt
```
# Creat  and remove Directory
mkdir helps in creating a dir
```
mkdir eg1

rmdir eg1
```
To see all of the dir in the system
```
ls -l /
```

# Delete
```
rm = it can remove anything #delete

ulink eg1.txt= delete

rmdir = can only remove dir
```
# Basic
```
pwd = present working directory

cat = to display the contant of file 

echo _________

vim = to creat a file 
#to exit from the file = esc:q! or esc:wq! ( to save and exit )

ls = list files

ls -l = list files with property

ls -al = all the files with the hidden files 
 
cp /ext/hosts . = it copys the hosts file to the server

""""Always creat a backup files """

cp -r /ext/hosts . = here "r" is recoursive 

```
# How to find files 
grep ______ file name will help in finding a file 
```
grep eg1 *
```
locate , which , find 
```
locate ____________  = it gives out all the file that start with _____________

which _____________

find / -name "________"
or 
find / -typr f -size +100M = here f is the specified as file 

-somethig can be trated a varible that we need to find 

find /etc: -exec grep -l ___________ {} \;

```
# How to edit a file 

nano helps in going inside  a file 
```
nano eg1.txt
```

How to come out of a file 
```
ctrl x
y
enter
```

# Mounting

It is the process of connecting a device to a directory so that we can access it.


# Links 
A link is the pointer to the file that is in different location ( path )

Linux has two typr of link 


Hard links are eentry in the dir files where the contant of the files are 
```
1)hard link = ln
```
symbolic link are like short cut , they just tell the path to the file 
```
2)symbolic link = ln -s
```
Example Hard Link
```
touch newfile.txt
ln newfile.txt newfile2.txt

=> it created nw file of the same link as the first file #new entry
```

Example Symbolic Link
```
ln -s newfile.txt newfile3.txt

=> creats a newfile3.txt with the newfile.txt entry symbolicay
```
Now 1,2,3 files are linked, 
To send them a text
```
echo hello >> newfile.txt

>> = append 
```



To Describe the I Note number 
```
ls -il /etc/hosts

 #to creat a link the /etc/hots
   =>  ln /etc/hosts /root/hardhosts

 ls -il /etc/hosts /root/hardhosts
#Now it gives 2 I notes but with the same number 
```
To incase the weight I Note 
```
vim /etc/hosts
#write something in there 

and run this command back
ls -il /etc/hosts /root/hardhosts
```
To creat a link
```
 ln -s /etc/hosts symhosts
```

# Terminal Redirection
 ```
 time = it gives out the time 
 date = it gives out the date
```
How to save this time and date 
```
date > saved_date.txt   # saved_date is teh file name 
 or 
date >> saved_date.txt  # save different amount of time 

cat saved_date = it reads out the file 

If i run the same " date > saved_date.txt " command it will over write and save it in the file 
```
How to save a perticular date 
```
date +%d 
 => 9
 9 because it gives the day of the month

date > 'date +%d'.txt  #tosave in txt file 
```
# Manual Pages 
man = it gives information about any command 

to get out of it  PRESS ' q '
```
eg: date command 

man date
```

# Chap2
# 
# Files System

A files system helps us organise the files
```
```

# Partitions 
To give out all the partions in that server
```
fdisk -l

THEN

fdisk /dev/xvda
m
p   #to check what are the partitions present table in there
```
To add new partitions 
```
n  #new partions
p #primary partitions
1 #partition number

first sectour : +200m
l #listv out all the possible file sys
```
#
# Ch3
#
# Kernel 

Linux kernel is the hart of the Linux operating system

Linux drivers are implimented as kernel modules

Most kernel modules are loded automatically through 1)initramfs 2)systemd.udevd
```
To list kernal moduless

lsmod
or
lsmod | grep _______

```
# Modprobe

To load the module if it is not there
```
modprobe  _______
```
To remove 
```
modprobe -r _______
```
To find out the information about module
```
modinfo ___________
```
To load or specify kernel module
```
edit /etc/modprobe.conf
or
cd /etc/modprobe.d/
```

# /proc

/proc is the file system that provides access to kernel information
```
PID directories

Status files

Tunable in /proc/sys
```
Write the parameters to 

To enable pakage forwarding 
```
vim /etc/sysctl.conf
```
To get proc
```
mount | grep proc
```
to lock in proc
```
cd /proc
```
# To update the kernel
```
yum update kernel
or
yuminstall kernel
```

# To add a value to the file that has no value
echo

dash is the file name 
```
echo 1 > ___________________
```
***
# Ch4 Booting
***
# Boot Procedure
Grub2 boot module

if we need grub2 boot module first we need to reeboot
```
reboot
```
next press "e" to see the com prom
```
e
```
we can make anty specific editing
```
ctrl x
```
# Modifying Grub2 Persistent Parameters

To edit the configuration file is 
```
/etc/default/grub
```
After writing changes we should compile the changes in grub.cfg
***
For BIOS SYSTEM
```
grub2-mkconfig -o /boot/grub2/grub.cfg
```
EFI system
```
grub2-mkconfig -o /boot/efi/EFI/redhat/grub.cfg
```







