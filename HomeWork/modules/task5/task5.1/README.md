# task_5.1

<h3 align="center">PART_1</h3>

Logged in to the system and switch as root.

![login_as_root](screans/login_as_root.png "figure")

Used the passwd command to change the password.

![change_passwd](screans/change_passwd.png "figure")

<br>The /etc/passwd file records your full name and the path name of the shell that you use. 
<br>To change your recorded name.
<br>If we chahged Password An x character indicates that encrypted password is stored 
in /etc/shadow file. 
Need to use the passwd command to computes the hash of a password typed at the CLI or 
to store/update the hash of the password in /etc/shadow file.


Determined the users registered in the system.

![determine_users](screans/determine_users.png "figure")
![determine_users_do](screans/determine_users_do.png "figure")

<br>who command is used to find information :
<br>1. Time of last system boot
<br>2. Current run level of the system
<br>3. List of logged in users.
<br>If w command is used we find information :
<br> List of users and their activities, tty, time login, PCPU What they doing.


Change personal information about yourself.

![change_info](screans/change_info.png "figure")

Linux system and the man and info commands.

Examples:

-v, --variable VAR=VALUE     assign VALUE to Info variable VAR
info -f ./foo.info           show file ./foo.info, not searching dir
![info](screans/info.png "figure")

info command reads documentation in the info format.
 It will give detailed information for a command when compared with the man page. 
The pages are made using the texinfo tools because of which it can link 
with other pages, create menus and easy navigation.


<br>
-I, --match-case           look for pages case-sensitively
<br>-w, --path, --location     print physical location of man page

![man_keys](screans/man_keys.png "figure")


<br>_more_ command is used to view the text files in the command prompt, 
<br>displaying one screen at a time in case the file is large (For example log files). 
<br>The _more_ command also allows the user do scroll up and down through the page. 
<br>The syntax along with options and command is as follows. 
<br>Another application of more is to use it with some other command after a pipe. 
<br>When the output is large, we can use more command to see output one by one.


_+num_ This option displays the text after the specified number of lines of the document.
![more_500](screans/more_500.png "figure")



<br>The _less_ command is also used to open the specified file for interactive reading, 
<br>allowing you to scroll and search. If the content of the file is too large, 
<br>it displays on the screen and therefore you can scroll page by page. 
<br>Unlike the _more_ command, it allows scrolling in both directions. 
<br>This means that you can scroll up and down the file.

<br>List the contents of the home directory using the ls command, define its files and directories.

![ls-R](screans/ls-R.png "figure")

<br>



<h3 align="center">PART_2</h3>

The tree is a tiny, cross-platform command-line program used to recursively list 
<br>or display the content of a directory in a tree-like format. 
<br>It outputs the directory paths and files in each sub-directory and 
<br>a summary of a total number of sub-directories and files.

The _-f_ list of the directory contents with the full path prefix 
for each sub-directory and file.

![tree1](screans/tree1.png "figure")

The _-c_ show Sort files by last status change time

![tree-c](screans/tree-c.png "figure")

For determine the type of file we can  used command _file_

![type_file](screans/type_file.png "figure")

Navigating the file system using relative and absolute paths.

![relative_and_absolute_paths](screans/relative_and_absolute_paths.png "figure")

Go back to my home directory from anywhere in the filesystem 

![home_dir](screans/home_dir.png "figure")

The various options for the ls command.


-a - with hidden
<br>-l - formatted one-column list 
<br>(displays file type, file access rights, number of hard links to the file, 
<br>owner name, group name, file size (in bytes), timestamp and file name.)

![ls_keys_a_l](screans/ls_keys_a_l.png "figure")

-R - list with sub-directories
<br>
![ls-R](screans/ls-R.png "figure")
<br>

-S - sort by size (large to small)
<br>
![ls_keys](screans/ls_keys.png "figure")

Created a subdirectory in the home directory and file containing information about directories
![dir_file](screans/dir_file.png "figure")

After moving the file, deleted the file with the directory
![rm-d_dir](screans/rm-d_dir.png "figure")
 
<br>Created a test subdirectory in the home directory.
<br>Copied the .bash_history file to this directory, changing its name to labwork2
<br>Created a hard and soft link to labwork2 file in the test sub-directory.

![link_hard_sim](screans/link_hard_sim.png "figure")


<br>Renamed the hard link file to hard_lnk_labwork2.
<br>Softlink file to symb_lnk_labwork2.
![mv_hard_sym_ln](screans/mv_hard_sym_ln.png "figure")

<br>Hard links are more flexible and stay linked even if the original or 
<br>linked files are moved around the file system
<br>
<br>Soft links can be linked on different file systems, although if the original file is
<br>deleted or moved, the programmatically linked file will not work correctly (this is called a hung link)

<br>After deleted the labwork2 my soft link didn't work, but hard links show me information


Using locate utility, I found all files containing squid and traceroute sequence.

![locate_utility](screans/locate_utility.png "figure")


<br>Determined which partitions are mounted on the system, as well as the types of these partitions.
<br>Counts the number of lines containing a given sequence of characters in the given file and the number of lines.

![lsblk_count](screans/lsblk_count.png "figure")

Using find command, found files in / etc directory containing host character sequence.

![find_host](screans/find_host.png "figure")


Found objects in / etc containing the character sequence ss. duplicated a similar command using grep.

![grep_ss](screans/grep_ss.png "figure")


Organized step-by-step printing of the directory contents / etc.

![screen-by-screen](screans/screen-by-screen.png "figure")

<br>Linux supports three types of hardware device: character, 
<br>block and network. Character devices are read and written directly without buffering, 
<br>for example the system's serial ports /dev/cua0 and /dev/cua1. 
<br>Block devices can only be written to and read from in multiples of the block size, 
<br>typically 512 or 1024 bytes. Block devices are accessed via the buffer cache and 
<br>may be randomly accessed, that is to say, any block can be read or 
<br>written no matter where it is on the device.

![type_dev](screans/type_dev.png "figure")

<br>In Linux there are basically three types of files:

<br>*Ordinary/Regular files
<br>*Special files
<br>*Directories
                      
<br>List of the first 5 directory files that were recently accessed in the / etc directory.

![list_dir_5_files](screans/list_dir_5_files.png "figure")




