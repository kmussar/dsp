# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* pwd   -  show current working directory path
* cd    -  switches to a new director - that you specify following 'cd' 
* mkdir -  creating a directory
* rm-r  -  deleting a directory
* touch -  creating a file using `touch` command
* rm    -  deleting a file
* mv    -  renaming a file  ('mv filename1.txt filename2.txt' renanmes filename1 to filename2)
* ls-a  -  listing hidden files
* ls-l  -  lists files/contents in long format
* ls-t  -  orders files and directories by the time they were last modified 
* cp    -  copying a file from one directory to another 
* sort  -  sorts lines of text alphabetically
* uniq  -  filters duplicate, adjacent lines of text 
* grep  -  searches for a text pattern and outputs it
* sed   -  searches for a text pattern, modifies it, and outputs it 

---

### Q2.  List Files in Unix   
What do the following commands do:  

* `ls`      -  lists all files and directories in the working directory (not hidden files)

Below are options for the ls command which modify the commmand in the following ways:
* `ls -a`   -  includes hidden files 
* `ls -l`   -  displays long format 
* `ls -lh`  -  displays long format with sizes of files in human readable format (bytes to KB, MB, or GB) 
* `ls -lah` -  shows all files (including hidden files) in long format, with sizes in human readable format 
* `ls -t`   -  displays newest files first (based on timestamp)
* `ls -Glp` -  displays long format, but does not include group directory names before files. Also appends '/' to directories.  

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

* 'ls -m'   -  displays names as a comman-separated list 
* 'ls -p'   -  displays directories with /
* 'ls -q'   -  displays all nonprinting characters as ?
* 'ls -r'   -  displays files in reverse order.
* 's -R'    -  displays subdirectories as well.

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

'xargs' is a command line tool that is used to allow other commands to be applied to stanard input. This is neccessary since some commands cannot read stdin and thus require this extra translation. Some examples of commands that do not take in stdin are: rm, mkdir, and find.   It also allows users to run the commands multiple times if desired. 
 
An example of xargs is: 
    
    xargs find -name "*.txt"
This command instructs the terminal to find all the files that end in .txt.  
    
