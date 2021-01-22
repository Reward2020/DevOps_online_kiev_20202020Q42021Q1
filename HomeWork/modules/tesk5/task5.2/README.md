# Task 5.2

<h3 align="center">Linux tesk 5.2</h3>

### 1

<br>The _/etc/passwd_ file contains all user information except for the password. 
<br>One line from this file corresponds to the description of one user. 
<br>A string consists of several fields, each separated from the other by a colon.

<br>In / etc / group, information about groups is stored.
<br>
![group](screans/group.png "figure")


In pseudo-users who do not use the user's shell, 
<br>their user ID (UID) starts from "1" through "999".
<br>Themost used are:
<br>daemon, bin, adm, nobody, sshd.


### 2


Uid ranges are from 1000 to 65535 for regular users.
<br>The UID is the number assigned to every Linux user,
<br>used to identify the user on the system and to 
<br>determine which system resources the user can access. 
<br>
![passwd](screans/passwd.png "figure")

<br>ubuntu1:        _Login username_
<br>x:			    _Encrypted password_
<br>1001:1001:		_Numeric user identifier (UID):Numeric group identifier (GID)_
<br>Linux Admin: 	_Comment field_
<br>/home/ubuntu1:  _User's home directory_
<br>/bin/bash 		_User shell_.

### 3

GID (Group ID) - User groups are used to organize access for several users to 
<br>some resources. The group, like the user, has a name and identification number.

<br>You can see the group information in the / etc / group file

<br>ubuntu1:			_Name Group_
<br>x:					_Encrypted password_
<br>1001:               _ID Group_
<br>Vasia, Petia,Masha  _List of users in the group_

### 4

You can use this command groups <group name> so you can see who is in this group
<br>
![group_to_u](screans/group_to_u.png "figure")
<br>
Or you can use other commands for output
<br>grep '^_group_name_:' /etc/group
<br>getent group _<group_name>_
<br>groupsmems -g _<group_name>_ -l

![gr_testing](screans/gr_testing.png "figure")



### 5


You can add a user with the following commands:

<br>useradd _user_name_
<br>It is a low-level utility for creating users.
<br>
<br>adduser _user_name_
<br>After running this command, you must enter the password for the new user. 
Then you will be prompted to enter additional information about the user
<br>
![add_user](screans/add_user.png "figure")

<br>
The main parameters that are needed to create a user are creating a password, 
belonging to a group, when creating a user using _useradd_, 
create a home directory in advance, copied the default files for users from the 
_/etc/skel_ directory, and then create a user and assign it to the home directory 
<br>
_sudo cp - rT /etc/skel /users/name_
<br>It is possible to take an easier way using the -m key
 _sudo useradd -m pupkin_
<br>Thus, the home directory is created by default in the /home directory. 
The directory name is the same as the username.

### 6

To change the account name, use the following:
<br> usermod -l _<newName> <oldName>_

### 7


_skell_dir_ is a directory containing files to copy to a newly created custom directory.

<br>
Structure _skell_dir_:
<br>
![skel](screans/skel.png "figure")

### 8

To delete a user and his files, you can use the command:
<br>
userdel -r _userName_ 
<br>
Force deletion of files even if they do not belong to the user.
You use -f.


### 9


To lock out a user with command, you can use the -l / -L option as follows:

<br>
passwd -l user_name
<br>
Or 
usermod -L user_name
<br>
To unblock a user with a command, you can use the -u / -U option:
<br>
passwd -u user_name
<br>
Or 
usermod -U user_name
<br>

### 10

You can force the change user on next login with commands _chage_ or _passwd_
<br>
chage --lastday 0 user_name
<br>
Or 
<br>
passwd --expire user_name  


### 11


At the output of the _ls -la_ command we can see columns

![skel](screans/skel.png "figure")

First column is right for our user. 

The second column shows how many directories or files are in a specific directory. 

The third column shows the owner of the directory. 

The fourth column shows the group in which the directories are located. 
                                                 
The fifth column shows the size of the directory.

The sixth column shows the last date the directory or file was modified


### 12

Access rights are divided into three categories:
<br>
*User - rwx
*Group - rwx
*Other users - r-x

![ls-Rl](screans/ls-Rl.png "figure")

<br>
Example
<br>
drwxrwxr-x
<br>
d - directory
r - access to read
w - access to write
X - access to execute
<br>
If  you have so access _r-x_
<br>This means that there are no rights to modify or delete a file or directory.


### 13


<br>With the help of access rights, we can determine what a user or group can do with a directory or file. 
<br>We can also change access to one or several users or groups. 
<br>Allowing read or write with read.


### 14


![chown](screans/chown.png "figure")
<br>

Changing the owner of a file can be done with the chown _new-user_ _file_ command.
<br>To access a file or directory. You need to add the user to the group with 
<br>the command usermod -a -G group user.

![ad_u_to_g](screans/ad_u_to_g.png "figure")

### 15

Use octal designators instead of "r", "w" and "x". 
<br>Each octal designation can be used by any of the groups 'u', 'g', 'o'.

<br>
Octal designations for umask are as follows:
<br>
Octal value: resolution
<br>0: read, write and execute
<br>1: read and write
<br>2: read and follow
<br>3: read only
<br>4: write and execute
<br>5: write only
<br>6: execute only
<br>7: no permissions

![umask](screans/umask.png "figure")

<br>
Octal designations for are as follows:
<br>
<br>rwx	7 
<br>rw-	6 
<br>r-x	5 
<br>r--	4 
<br>-wx	3 
<br>-w-	2 
<br>--x	1 
<br>---	0 

<br>chmod ugo+rwx file_name
<br>chmod 777 file_name

<br>

![tekst_777](screans/tekst_777.png "figure")


### 16

<br>A Sticky bit is a permission bit that is set on a file or a directory that lets only 
the owner of the file/directory or the root user to delete or rename the file. 
<br>No other user is given privileges to delete the file created by some other user.
<br>
For to set the sticky bit:
<br>chmod +t my_dir
<br>
![sticky_bit](screans/sticky_bit.png "figure")
<br>
To check, run the command:
<br>
find . -perm /1000
<br>
![sticky_bit_check](screans/sticky_bit_check.png "figure")
<br>

### 17

<br>Each file and directory has access which is divided into three parts: 
<br>the first part _rw-_ responsible for the owner of the file or directory; 
<br>the second part _rw-_ responsible for the users who are in the group; 
<br>the third part _r--_ denotes everyone else.
<br>
![access_rights](screans/access_rights.png "figure")
