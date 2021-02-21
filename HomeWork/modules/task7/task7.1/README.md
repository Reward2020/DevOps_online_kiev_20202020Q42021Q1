# Linux administration with bash


### A. Create a scrip

<br>![bash_file](screans/bash_file.png "figure")

<br> "--all - find ip who connect to you"
<br> "--target - find open ports"
<br> ![all_target](screans/all_target.png "figure")



### Created a script, using Apache log

<br> "--fipu - find ip uniq with count in file"
<br> "--url - most visitible url"
<br> "--erurl - feiled pages"
<br> "--tvis - show most visiteble time"
<br> "--bot - show bots in log file"

<br>
![log_get_script](screans/log_get_script.png "figure")
<br>

<br> "--fipu - find ip uniq with count in file"
<br> "--url - most visitible url"
<br>
![B_ip&url](screans/B_ip&url.png "figure")
<br>
<br> "--erurl - feiled pages"
<br>
![er_url](screans/er_url.png "figure")
<br>
<br> "--tvis - show most visiteble time"
<br> "--bot - show bots in log file"
<br>
![visit&bot](screans/visit&bot.png "figure")

### Create a data backup scrip

<br>When creating a script in this way, the script is executed in the background
<br>
![bash_backup1](screans/bash_backup1.png "figure")
<br>
<br>You can also slightly modify this script.
<br>
![bash_backup2](screans/bash_backup2.png "figure")
<br>
<br> Add our script to the crontab for the scheduled launch
<br>
![crontab](screans/crontab.png "figure")
<br>
<br>Check if the log is being written
<br>
![log_backup](screans/log_backup.png "figure")