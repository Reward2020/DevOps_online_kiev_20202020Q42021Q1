# EPAM_lectures
Courses of DevOps

### part 1

#### 1

_ps aux_ command

In the STAT column, you'll see lots of values. 
<br>A linux process can be in a number of different states. 
<br>The most common state codes you'll see are described below:

<br>R: running or runnable, it is just waiting for the CPU to process it
<br>S: Interruptible sleep, waiting for an event to complete, such as input from the terminal
<br>D: Uninterruptible sleep, processes that cannot be killed or interrupted with a signal, usually to make them go away you have to reboot or fix the issue
<br>Z: Zombie are terminated processes that are waiting to have their statuses collected
<br>T: Stopped, a process that has been suspended/stopped 
<br>s: a session leader
<br>l: multi-threaded
<br>

![ps_aux](screans/ps_aux.png "figure")


#### 2

_pstree_ is shows all running processes currently active on your logged-in system
<br>
![pstree_-t](screans/pstree_-t.png "figure")


<br> -t: Show full names for threads when available.
<br> -s: Show parent processes of the specified process
<br> -p: Show PIDs.  PIDs are shown as decimal numbers in parentheses after each process name.  -p implicitly disables compaction. 
<br>
![pstree_-p](screans/pstree_-p.png "figure")


#### 3


proc is a special filesystem used on UNIX-like systems. Allows you to access information from a system process.

<br>/proc/meminfo, this file is used to get current memory information from the kernel.
<br>
![proc](screans/proc.png "figure")
<br>
<br>The current values are populated from the kernel.
<br>We get the most current and accurate system status from files inside /proc.
<br>
![proc_diskstats](screans/proc_diskstats.png "figure")
<br>
<br>The /proc/diskstats file displays I/O statistics.
block devices. Each line contains the following 14
fields:

<br>1 main number
<br>2 junior member
<br>3 device name
<br>4 readings completed successfully
<br>5 reads combined
<br>6 sectors read
<br>7 time spent reading (ms)
<br>8 entries completed
<br>9 records merged
<br>10 sectors written
<br>11 time taken to write (ms)
<br>12 inputs/outputs in progress
<br>13 time spent on I/O (ms)
<br>14 weighted time spent on I/O (ms)
<br>
![ps_cpu](screans/ps_cpu.png "figure")
<br>

/proc/cpuinfo: Contains complete information about the processor.

#### 4
To find details about the cpu on your system
<br>The command can be:
<br>
_cat /proc/cpuinfo | grep -i mhz_ - print information about speed of the processor
<br>
![speed_cpu](screans/speed_cpu.png "figure")
<br>               
_cat /proc/cpuinfo_ or _lscpu_ - print full information about your CPU.
<br>
![ls_cpu](screans/ls_cpu.png "figure")


#### 5

 _-e_ shows every process on the system 
<br> _-o_ is to define the format we want the result
<br>_-A_ Select all processes. Identical to -e.
<br>We have specified the format as _user,uid,comm,pid,%cpu,%mem,tty_
<br>One important point to note here is that by default it sorts ascending. 
<br>Also _--sort_ needs the parameter to sort by which we provide.

_ps -Ao user,uid,comm,pid,%cpu,%mem,tty,cmd --sort=-pcpu | grep epam_
<br>
 ![ps_grep](screans/ps_grep.png "figure")
<br>
_ps -eo user,uid,comm,pid,%cpu,%mem,tty --sort=-%cpu | head -n 6_
<br>
![ps_-eo](screans/ps_-eo.png "figure")

#### 6

Each of the kernel processes starts with its own process number (PID). 
<br>When managing processes, it is easy to recognize kernel processes because their name 
<br>is enclosed in square brackets. Command executions: _ps aux | head_ where you can 
<br>see a couple of kernel threads. As an administrator, it is important to know that streams cannot be controlled, 
you cannot change their priority; 
they cannot be killed except to disable the entire machine.
  
![ps_kernel](screans/ps_kernel.png "figure")

Or you can write this _ps aux k-pcpu | head -6_ to fing kernel process


#### 7
<br>
![ps_7](screans/ps_7.png "figure")
<br>
<br>_User_ The username of task owner
<br>_PID_ The process ID of each task
<br>_%CPU_ % of CPU time
<br>_%MEM_ Physical memory used
<br>_VSZ_ Process virtual memory size in KiB 
<br>_RSS_ The actual size of the process in memory 
<br>_TTY_ Terminal type that the user is logged into
<br>_STAT_ Process status code, which can be Z (zombie), S (sleeping), R (running)
<br>_START_ The time the command started
<br>_TIME_ Amount of CPU in minutes and seconds that the process has been running
<br>_COMMAND_ Command name
<br>
<br>
### STAT indicates are:
<br>
<br>_D_ Uninterruptible sleep (usually IO)
<br>_R_ Running or runnable (on run queue)
<br>_S_ Interruptible sleep (waiting for an event to complete)
<br>_T_ Stopped, either by a job control signal or because it is being traced.
<br>_W_ paging (not valid since the 2.6.xx kernel)
<br>_X_ dead (should never be seen)
<br>_Z_ Defunct ("zombie") process, terminated but not reaped by its parent. 
<br>
### The additional characters are:
<br>
<br>_<_ high-priority (not nice to other users)
<br>_N_ low-priority (nice to other users)
<br>_L_ has pages locked into memory (for real-time and custom IO)
<br>_s_ is a session leader
<br>_l_ is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)
<br>_+_ is in the foreground process group


#### 8

To display only a specific user, we can use several commands
<br>
<br>_ps -fu userName_
<br>_-f_ Do full-format listing.
<br>_-u_ Selection by effective user ID (EUID) or name
![ps_-fu](screans/ps_-fu.png "figure")
<br>
<br>
You can use command _ps -u userName_
<br>
![ps_-u](screans/ps_-u.png "figure")
<br>
Or this command _top -U userName_
<br>
![top_-U](screans/top_-U.png "figure")


#### 9

To analyze ranning tass you can used several utilities
<br>_top_
<br>_pgrep_ - The pgrep command is used to determine the PID of a running program based on various criteria.
![pgrep_l](screans/pgrep_l.png "figure")
<br>_pstree_ - Shows running processes in a tree view, displays process hierarchies and makes the output more visually appealing
![pstree_-p1](screans/pstree_-p1.png "figure")
<br>_proc_ - This virtual file system contains process data and other system information. It appears in / proc and is mounted at boot time.
![proc_mounts](screans/proc_mounts.png "figure")
<br>


#### 10

<br>_top_ command used to demonstrate Linux processes. 
<br>It provides a dynamic, real-time view of a running system. 
<br>Shows a summary of the system and a list of processes or threads that are 
<br>currently managed by the Linux kernel.
<br>
![top_](screans/top_.png "figure")
<br>


#### 11 
To display only a specific user with  _top_ command, you mast write next:
<br>_top -U name_
<br>
![top_-U](screans/top_-U.png "figure")
<br>


#### 12

 INTERACTIVE Commands
<br> a. GLOBAL Commands
<br> b. SUMMARY AREA Commands
<br> c. TASK AREA Commands
<br>    1. Appearance
<br>    2. Content
<br>    3. Size
<br>    4. Sorting
<br> d. COLOR Mapping
<br>
Sorting by user and refreshing every three seconds
<br>
![top_-d_3](screans/top_-d_3.png "figure")
<br>
Run top then press the _z_ key to toggle the color mode
<br>
![top_color](screans/top_color.png "figure")
<br>


#### 13

<br>
To sort the contents of the process used next commands
<br>
_ps --sort=-pcpu | head -n 6_
<br>
![ps_sort](screans/sort.png "figure")
<br>
Or you can specify columns without interfering with sorting
<br>
_ps -Ao user,uid,comm,pid,pcpu,tty --sort=-pcpu | head -n 6_
<br>
![ps_sort_u](screans/ps_sort_u.png "figure")
<br>

Or sort by user
<br>
![sort_u](screans/sort_u.png "figure")
<br>

#### 14

Change the  Priority of a Process
<br>
You can change the priority of a process using the nice and renice commands
<br>_renice_ value (from -20 to +19)
<br>_Nice_ value range (NI): -20 to 19
![htop](screans/htop.png "figure")
<br>_ renice -n -2 -p 1374_
![renice](screans/renice.png "figure")
<br>
_sudo renice -n 4 -p 1374_
<br>
![htop_re](screans/htop_re.png "figure")
<br>

#### 15
<br>
With the command top you can change the priority of the process
<br>
After receiving the top command, press r.
<br>
![top_re](screans/top_re.png "figure") 
<br>Set the PID value of the process whose value you want to change. 
<br>Specify renice value
<br>
![top_re_after](screans/top_re_after.png "figure")
<br>


#### 16

<br>
You can view all signals with the command:
<br>
_kill -l_
<br>
When you execute the _kill_ command, you are effectively signaling the system to force it to terminate the misbehaving application.
<br>
The default signal (if not set) is SIGTERM.
<br>
If it doesn't help, you can use the following options to force the process to terminate:
<br>
![kill_p1](screans/kill_p1.png "figure")
<br>_kill SIGKILL PID_ 
<br>or
<br>_kill -9 PID_
<br>where the "-9" flag refers to the SIGKILL signal.
<br>_SIGKILL_ - This signal causes the process to terminate immediately. The program cannot ignore this signal. Unsaved results will be lost.
<br>
![kill_p2](screans/kill_p2.png "figure")



#### 17


<br>The bg command is designed to restore the operation of stopped processes (tasks) in the background.
![bg](screans/bg.png "figure")
<br>
The fg command without a parameter will resume the work of the last process stopped by the combination ctrl + z, and if there are none, it will bring the last task to the fore.
![fg](screans/fg.png "figure")

<br>Also, you will not find help for fg and bg commands (man fg, man bg). Because these commands are part of bash. And you will find a mention of them in man bash.
![nohup_1](screans/nohup_1.png "figure")

<br>
_nohup_. This command allows you to start processes that will be disconnected from the terminal if the terminal is closed.

<br>
Despite the fact that we exited the shell, the process with PID 13010 remained in the system and adopted as the parent, the process with PID equal to 1, that is, the init process. Process 13010 will continue to exist as long as the init process exists, or until we terminate it ourselves with the kill command.
<br>
![nohup_2](screans/nohup_2.png "figure")



### part 2


To connect via Windows, you must activate the open ssh settings. after which in the shell went or through the command line write _ssh logname @ ip / host_
<br>
![ssh_1](screans/ssh_1.png "figure")

<br>
Port 22 is the standard port for SSH connections. If you use a different port, it adds a little bit of security through obscurity to your system. 
<br>
To configure a non-standard port, need edit your SSH configuration file:
<br>_/etc/ssh/sshd_config_
<br>
![ssh_port](screans/ssh_port.png "figure")
<br>
Set an Idle Timeout Value
<br>
We’ve used 300 seconds, which is 5 minutes. 
The SSH connection will be dropped if the inactive period matches the time limit. 
<br>
![ssh_time](screans/ssh_time.png "figure")
<br>
It is bad practice to log in as root. You need to disable root log Ins
<br>
![ssh_d_root](screans/ssh_d_root.png "figure")                
<br>
<br>
SSH key pair can be generated using the ssh-keygen command:
<br>

ECDSA (the Elliptic Curve Digital Signature Algorithm) keys provide smaller keys and faster operations 
or DSA (2048 bits).
<br>
_ssh-keygen -t ecdsa -b 521_
<br>
_ssh-keygen -t dsa -b 521_
<br>
FOrmat ssh key pair: dsa | ecdsa | ecdsa-sk | ed25519 | ed25519-sk | rsa
<br>

If you want to create an RSA key pair (2048-16384 bits):
<br>
_ssh-keygen -t dsa -b 2048_ or another bits.
<br>
![ssh_key](screans/ssh_key.png "figure")
<br>
To default your key pair store in home directory /.ssh
<br>
If you want connect whithout password have to do next step in _sshd_config_ file:
<br>
![pass_off](screans/pass_off.png "figure")
<br>
Before these actions copy private and public ssh key on your local machine
<br>
![rsa_key](screans/rsa_key.png "figure")
<br>
After this actions try to connect to your remove machine by first connecting your key to the terminal.
<br>
![ssh_conn_pass](screans/ssh_conn_pass.png "figure")


<br>To enable port forwarding, open the settings for your Virtual Machine 
you'll need to change its network type or forward ports through the virtual NAT
<br>Open VirtualBox and select the VM you want to alter. Click Settings and then click on the Network tab. 
In the Network window expand the Advanced section and click Port Forwarding

![port_switch](screans/port_switch.png "figure")


<br>Tcpdump is a CLI tool this means you can run it remotely in an ssh session, it accepts a many filters and allows you to display data about packets going in and out of an interface. You can also filter syntax which is very powerful.

<br>Wireshark is a gui tool, you have a nice interface, and like tcpdump, it lets you to capture (or look at recorded captures) packets coming in and out of an interface. You can apply filters to collapse fields you don’t care about while examining a packet. Moreover, wireshark allows you to isolate streams such as a whole TCP session.
<br>
![tcp_listen](screans/tcp_listen.png "figure")
<br>
_tcpdump_ is a tool for interacting with traffic,
protocol analyzer.
<br>![tcp_any](screans/tcp_any.png "figure")
<br>-i enp0s8: listen on a specific interface (enp0s8).
<br>-i any: listen on all interfaces to see if there is any traffic.
<br>-tttt: Sets the default timestamp format for each line.
<br>-nn: display IP addresses and port numbers instead of hostnames and protocol names.

![wshark](screans/wshark.png "figure")
