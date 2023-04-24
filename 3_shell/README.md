# Bash Script

A bash script is a series of commands written in a file. These are read and executed by the bash program instead of being called by the user. By defining a series of actions, a bash script enables the computer to execute tasks without the need for manual input, which is particularly useful for repetitive tasks.

Bash scripts are used everywhere. For example, when you first launch the shell, it uses a startup script located in the `.bashrc` or `.bash_profile` file which allows you to customize the behavior of the shell. In the next chapter, we will learn how to use `conda` to create and maintain virtual environemnt, and we would need to modify `.bashrc` so that the base environment can be automatically activated whenever you launch a new shell.

> Note: Anything you can run on the command line you may place into a script and they will behave exactly the same. Vice versa, anything you can put into a script, you may run on the command line and again it will perform exactly the same.

### Writing a bash script
To create a bash script, we may call our script whatever we like, yet the file name of script usually ends with `.sh` as its extension for convenience. Note that the first line of your scripts should be started with a `shebang`, which is a combination of `bash #` and `bang !`. It tells the shell to execute it via bash shell by indicating the absolute path to the bash interpreter.
```sh
# Create and open your script to edit it
vim myscript.sh
# Find the path to your bash shell
which bash
# The path is /usr/bin/bash in my case
```
Now, in your script you can write something like this:
```sh
#! /usr/bin/bash
echo "Hello World"
```
### Runing a bash script

To run your script, you can simply run `./myscript.sh` if the script is in your currently working directory. `./` tells the system to look in our current directory to find the script. Or, we could have used an absolute path such as `/home/ryan/linuxtutorialwork/myscript.sh`. A relative path like `../linuxtutorialwork/myscript.sh` is also acceptable, which will work exactly the same.

However, if you try to run the script you just created, there could be a "Permission denied" message showing up on your terminal. This is because we have to modify the file permission to allow execution of the script. Recall the `chmod` command we introduce in the Chapter 2:
```sh
chmod 755 myscript.sh
```
Now, run the script by `./myscript.sh` then you should be able to see the message on your terminal.

### Using variables and operators
In shell script, we can also leverage variables as what we usually do in a program. The variables in scripts are assigned by `variable_name=value` and can be called by adding `$` before the variable name. For example:
```sh
#!/bin/bash
# A simple variable example
greeting=Hello
name=Tux
echo $greeting $name
```

Bash also supports several operators we are familiar with, such as `+`, `-`, `*`, `/`, `**`, `%`, whcih allow you to perform logical actions on your variables. Bash also provides comparison logical operators, including `-eq` (equal to), `-ge` (greater than equal to), `-gt` (greater than), `-le` (less than equal to), and `-lt` (less than). Furthermore, if you need the user to input some sepcific variables, the `read` command allows you to gather user input in your script. For instance:

```sh
#! /usr/bin/bash
read x
read y

if [ $x -gt $y ]
then
echo X is greater than Y
elif [ $x -lt $y ]
then
echo X is less than Y
elif [ $x -eq $y ]
then
echo X is equal to Y
fi
```

In addition, bash also supports the if...else condition, for/while loop, and case statements. More example code can be found in 
- https://www.freecodecamp.org/news/shell-scripting-crash-course-how-to-write-bash-scripts-in-linux/


### Using commands and args
To use Linux commands and arguments in a Bash script, you can simply include the commands in the script and use variables to store the arguments. If you need to include the output of a Linux command in your script, you can write the statement inside back ticks; if you would like to give arguments to the script, the syntax `$@` can be used. For instance:
```sh
#! /usr/bin/bash

var=`df -h | grep tmpfs`
echo $var

for x in $@
do
    echo "Entered arg is $x"
done
```

In this example, the output of `df -h | grep tmpfs` will be printed on the terminal. Then, the script takes an argument in a sequential order and assigns it to the variable x within the for loop.

### Scheduling cron jobs
Cron is a job scheduling utility in linux that allows users to schedule tasks or scripts to run automatically at specified times or intervals. Cron allows users to schedule tasks based on specific times and dates, as well as recurring intervals such as hourly, daily, weekly, or monthly.

Let's say you have a Bash shell script called backup_script.sh that you want to run every day at 2:30am. Here's how you can use Cron to schedule it:

1. Open your crontab file by running the following command in your terminal.
```sh
crontab -e
```

2. Add the following line to the crontab file and then save it.
```sh
30 2 * * * /path/to/backup_script.sh
```
This line tells Cron to run the backup_script.sh script at 2:30am every day. The * characters represent wildcards for the day of the week and the month, meaning that the script will run every day of every month.