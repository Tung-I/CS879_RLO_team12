# The Command Line

A **command line** or **terminal**, is a text based interface to the system. You are able to enter commands by typing them on the keyboard and feedback will be given to you similarly as text. Within a terminal you have what is known as a **shell**. This is a part of the operating system that defines how the terminal will behave and looks after running (or executing) commands for you. There are various shells available but the most common one is called **bash**, which stands for Bourne again shell.

### Text Editor

There are numerous text editors available in Linux, and let's take `Vim` as an example here. Vim is a powerful and flexible text editor that is widely used by programmers and system administrators to edit code and text files. To use Vim, one can simply type the command, `vim your_text_file.txt`, on your terminal. In most cases, you might be able to open a file with GUI and edit it directly. However, many individual software's editing interfaces will actively call Vim. That's why we should know about how to use it before delving into the other topics. Briefly speaking, Vim has two modes:

* `command mode`: where you can execute commands like undo, redo, find and replace, quit, etc..
* `insert mode`: where you can type text in the file.

For example, to edit your text, we should first enter the `insert mode` by pressing `i` in the `command mode`; to save and quit Vim, we can use the `:wq` command. To obtain a basic sense of how to use Vim, one can refer to the introduction via the following link: 
- https://web.stanford.edu/class/cs107/resources/vim 


Vim also provides some advanced features including syntax highlighting, automatic indentation, auto-completion, macros, and support for multiple buffers and tabs. For those who are interested in can refer to this post:
- https://stackoverflow.com/questions/5169638/autocompletion-in-vim


### File manipulation
One of the most common mistake made by a first-time Linux user could be dumping everything directly at the base of their home directory. Develop the habit of organising your stuff into an elegant file structure is something you will thank yourself for years to come.

#### Creating and removing
First of all, one can use the `ls` command to list the files and directories in the current working directory. If you would like create a new folder or file, then the command you may need is called `mkdir` (short for Make Directory) and `touch`.
```sh
# List the folders and files in the working directory
ls
# Create a new folder
mkdir [options] <name_of_your_dir>
# Create a new file
touch <name of your file>
```
The options of `mkdir` include `-p` and `-v`, which tell `mkdir` to make parent directories as needed  tell us what it is doing. Similary, there is a `rm` command available for removing a file or a directory. It is also worth mentioning that one can append a `--help` option following your command to see its usage in detail.
```sh
mkdir --help

sage: mkdir [OPTION]... DIRECTORY...
Create the DIRECTORY(ies), if they do not already exist.

Mandatory arguments to long options are mandatory for short options too.
  -m, --mode=MODE   set file mode (as in chmod), not a=rwx - umask
  -p, --parents     no error if existing, make parent directories as needed
  -v, --verbose     print a message for each created directory
  -Z                   set SELinux security context of each created directory
                         to the default type
      --context[=CTX]  like -Z, or if CTX is specified then set the SELinux
                         or SMACK security context to CTX
      --help     display this help and exit
      --version  output version information and exit

```


#### Moving, Copying, and Renaming 
There are many reasons why we may want to make a duplicate of a file or directory, and it can be easily done on your terminal using a `cp` command.
```sh
cp [options] <source> <destination>
```


To move a file we use the command `mv` which is short for move. It operates in a similar way to `cp` by assigning the source and destination. As for renaming a file/directory, we can acheive it by using the command `mv` in a creative way:
```sh
mv <file_name> <new_file_name>
```

#### Premissions
 Permissions specify what a particular person may or may not do with respect to a file or directory. This is especially important when it comes to building a Linux server. It can also help you prevent important files from damage (either accidental or deliberate). Furthermore, sometimes a program or script downloaded from the Internet may not be directly executable, where the file permission must be changed. In that case, we have the following commands to use:

 * `ls -l`: View the permissions for a specific directory.
 * `chmod`: Change permissions on a file or directory.

 Setting the right permissions is important in the smooth running of certain tasks on Linux. One can refer the following link to get a basic sense of how the number system works and how to change your file permission.
 - https://ryanstutorials.net/linuxtutorial/permissions.php


 many processes can be running at the same time. As well as the processes we are running, there may be other users on the system also running stuff and the OS itself will usually also be running various processes which it uses to manage everything in general.

#### File Compression
In the Linux environment, compressed files are mostly identified by extensions such as "*.tar, *.tar.gz, *.tgz, *.gz, *.Z, *.bz2, *.xz". Why are there so many extensions? This is because Linux supports a wide range of compression commands, and different commands may use different compression techniques that may not be compatible with one another. Compressing/De-compressing files using Linux commands is actually quite easy. For instance, to zip or compress files, you can use the "tar" command with various options:
```sh
# To create a compressed file or zip archive
tar -czvf archive_name.tar.gz directory_or_file_names
# To extract or unzip a compressed file
tar -xzvf archive_name.tar.gz
# To extract a specific file or directory from the compressed file
tar -xzvf archive_name.tar.gz path/to/file_or_directory
```

### Install, update, and remove packages
To maintain the pacakges in you system, we need to keep track of all the installed packages and their dependencies. This can be done by the Advanced Packaging Tool (APT) in Linux, which simplifies the process of installing, upgrading, and removing software packages for Linux uers.

First of all, one can retrive the latest information about the available packages and downloads the latest version of the package lists to your local machine by a simple `apt update` command.
```sh
sudo apt update 
```
To install a new package:  
```sh
sudo apt install [package-name]
```

Similarly, to remove a package:
```sh
sudo apt remove [package-name]
```

>Note: The apt remove command leaves its configuration files on the system. If you want to completely remove a package, including any configuration files and dependencies that were automatically installed, you should use the apt purge command (see https://askubuntu.com/questions/231562/what-is-the-difference-between-apt-get-purge-and-apt-get-remove for more details).

### Process Management
Many processes can be running at the same time. To see what is currrently running and the information about the system's processes, such as the CPU usage, memory usage, we can use the commands `top` and `htop`,

 Sometimes the processes crash and becomes unresponsive, and we would like to kill a process manually. In that case, we can use `ps` to get a listing of process running on the system and find the target by specifying the keyword of the process:
```sh
 ps aux | grep [keyword-of-process]
```
Aftering figuring out the PID of the process, we can end that running process manually by using the `kill` command. For example, if one of your Python processes crashes and become unresponsive, you can first use `ps aux | grep python` to find the PID and then kill it by the `kill -9` command.
```sh
# Find the PID
ps aux | grep python

root        1167  0.0  0.0  48356 20672 ?        Ss   08:50   0:00 /usr/bin/python3 /usr/bin/networkd-dispatcher --run-startup-triggers
root        1267  0.0  0.1 141568 37248 ?        Ssl  08:50   0:00 /usr/bin/python3 /usr/sbin/firewalld --nofork --nopid
root        1379  0.0  0.0 126676 22576 ?        Ssl  08:50   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
user      20639  0.9  0.1 836064 63412 ?        Sl   16:09   0:01 /usr/bin/python3 /usr/bin/x-terminal-emulator
user      21241  2.6  0.0 192652 25548 pts/1    Sl+  16:11   0:00 python order.py --config_path ../config.yaml --id 3
user      21245  0.0  0.0  17672  2624 pts/2    S+   16:11   0:00 grep --color=auto python
```

```sh
# End that process
kill -9 21241
```





