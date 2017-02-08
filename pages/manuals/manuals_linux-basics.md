---
layout: page
title: Manuals
permalink: manuals_linux-basics.html
---
## Linux Basics

### Introduction
The scope of this manual is a brief introduction on how to get started using powerful Linux command-line utilities.

## How to Get Access?

* Install your preferred GNU/Linux distribution on your local machine (not required!!!)
* Users at UC Riverside can apply for an account on our Linux clusters by sending an account request to Rakesh Kaundal (rkaundal@ucr.edu).

## Logging-In

### Mac or Linux

* To log-in into the remote Linux shell, open terminal and type:

  `ssh -X <your_username>@<host_name>`

  `host_name` is the remote server's domain name (e.g. `biocluster.ucr.edu`)  
  You will be asked to enter your password. Simply type it and press enter.

* To copy files To the server run the following on your workstation or laptop:

  `scp -r <path_to_directory> <your_username>@<host_name>:`

* To copy files From the server run the following on your workstation or laptop:

  `scp -r <your_username>@<host_name>:<path_to_directory> .`

### Windows

1. Open PuTTY and select ssh. [Download PuTTY](http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html) if you do not have it.
2. Provide the host name (the remote server's domain name) and session name 

   hostname:  biocluster.ucr.edu

3. Enter your identity information

   username: your username  
   password: your password 

   **Nothing will show-up,**  
   **simply type the password and press enter.**

4. Setup for graphics emulation. [Download and install Xming](http://www.straightrunning.com/XmingNotes/#head-13) if you do not have it.

5. Use WinSCP or FileZilla for file exchange. [Download and install WinSCP](https://winscp.net/eng/download.php) or [FileZilla](https://filezilla-project.org/) if you do not have it.

## Change Password

1. Log-in to the cluster via SSH
2. Once you have logged in, type the following command:
   `passwd`
3. Enter your current password (the random characters that you were given as your initial password)
4. Enter your new password (you will be asked to type it twice for verification)

### Minimum password requirements

* Total length at least 8 characters long
* Must have at least 3 of the following:
  * Lowercase character
  * Uppercase character
  * Number
  * Punctuation charcter

## Why GNU/Linux?

* Software costs $0
* Advanced Multitasking 
* Remote tasking ("real networking")
* Multiuser 
* Easy access to programming languages, databases, open-source projects 
* Software freedoms
  1. Free to use for any purpose
  2. Free to study and modify the source code
  3. Free to share
  4. Free to share modified versions
* No dependence on vendors
* Better performance 
* More up-to-date
* Many more reasons...

### GNU/Linux Distributions

* [Ubuntu](https://www.ubuntu.com/) - A beginner-friendly Linux OS based on Debian. A good choice for most people.
* [OpenSuSE](https://www.opensuse.org/) - An alternative to Ubuntu for new users.
* [Debian](https://www.debian.org/) - A general-purpose Linux OS with a large software package repository and support community.
* [Red Hat Enterprise Linux (RHEL)](https://www.redhat.com/) - A general-purpose Linux OS supported by Red Hat, Inc. Requires purchase.
* [CentOS](https://www.centos.org/) - A community-supported version of RHEL that's free to download and use. The UCR HPCC cluster runs on CentOS 7.
* [Fedora](https://getfedora.org/) - A developer-oriented Linux OS sponsored by Red Hat.
* [Arch Linux](https://www.archlinux.org/) - A highly-customizable Linux OS for power users.
* [Slackware](http://www.slackware.com/) - ...

[Family tree of the GNU/Linux distributions](https://en.wikipedia.org/wiki/File:Linux_Distribution_Timeline.svg)

## Basics

### Command-Line Syntax for this Manual

* Remember the UNIX/Linux command line is case sensitive!
* All commands in this manual are printed in gray code boxes.
* ~~Commands given in red are considered more important for beginners than commands given in black.~~
* The hash (pound) sign "#" indicates end of a command and the start of a comment.
* The notation <...> refers to variables and file names that need to be specified by the user. The symbols < and > need to be excluded.

### Orientation

Viewing and changing the present working directory:

```
pwd               # Get full path of the present working directory (same as "echo $HOME")

ls                # Content of pwd
ls -l             # Similar as ls, but provides additional info on files and directories
ls -a             # Includes hidden files (.name) as well
ls -R             # Lists subdirectories recursively
ls -t             # Lists files in chronological order

cd <dir_name>     # Switches into specified directory.
cd                # Brings you to the highest level of your home directory.
cd ..             # Moves one directory up
cd ../../         # Moves two directories up (and so on)
cd -              # Go back to you were previously (before the last directory change)
```

The tilde symbol (~) gets interpreted as the path to your home directory:

```
echo ~            # View the full (complete) path of your home
find ~            # List all your files (including everything in sub-directories)
ls ~              # List the top level files of your home directory
du -sch ~/*       # Calculate the file sizes in your home
```

Viewing file info, user, and host:

```
stat <file-name>  # Last modification time stamps, permissions, and size of a file

whoami            # Shows your user name (same as "echo $USER")
hostname          # Shows on which machine you are (same as "echo $HOSTNAME")
```

### Files and directories

```
mkdir <dir_name>   # Creates specified directory
rmdir <dir_name>   # Removes empty directory
rm <file_name>     # Removes file_name
rm -r <dir_name>   # Removes directory including its contents, but asks for confirmation
rm -rf <dir_name>  # Same as above, but turns confirmation off. Use with caution
cp <name> <path>   # Copy file/directory as specified in path (-r to include content in directories)
mv <name1> <name2> # Renames directories or files
mv <name> <path>   # Moves file/directory as specified in path
```

### Copy and paste

The methods differ depending where you are.

* In a **command line** environment:

  Cut last word with keyboard only  
  `Ctrl+w`  
  Press multiple times to cut more than one word

  Paste with keyboard only  
  `Ctrl+y`

* In a non-command line **desktop** environment (e.g. Firefox):

  Copy  
  `Ctrl+c`

  Paste  
  `Ctrl+v`

* **Command line** <-> **desktop** exchange:

  Copy text out of the command line and into the desktop:  
  `Shift+Ctrl+c        or        Apple+c`

  Paste text from the desktop into the command line:  
  `Shift+Ctrl+v        or        Apple+v`

* On any Linux desktop!
  * Copy with mouse only
    * Simply select the text with the mouse 
  * Paste with mouse only
    * Click the middle mouse button or both left/right buttons simultaneously

### Handy shortcuts

* At the command prompt:
  * up(down)_key                 - scrolls through command history
  * `history   # shows all commands you have used recently`
* Auto Completion:
  * <something-incomplete> TAB   - completes program_path/file_name
* Taking control over the cursor (the pointer on the command line):

> ```
Ctrl+a    # cursor to beginning of command line
Ctrl+e    # cursor to end of command line
Ctrl-w    # Cut last word 
Ctrl+k    # cut to the end of the line
Ctrl+y    # paste content that was cut earlier (by Ctrl-w or Ctrl-k)
```

* When specifying file names:
  * "." (dot)            - refers to the present working directory
  * "~" (Tilda) or "~/"  - refers to user's home directory

## Unix Help

```
man <something> # general help (press the 'q' key to exit) 
man wc          # manual on program 'word count' wc
wc --help       # short help on wc

soap -h         # for less standard programs 
```

Online help: [Google](https://www.google.com/)

Universally available Linux commands, with detailed examples and explanations: https://www.linuxconfig.org/linux-commands

## Finding Things

### Finding files, directories and applications

```
find -name "*pattern*"            # searches for *pattern* in and below current directory
find /usr/local -name "*blast*"   # finds file names *blast* in specfied directory
find /usr/local -iname "*blast*"  # same as above, but case insensitive
```

* additional useful arguments: -user <user name>, -group <group name>, -ctime <number of days ago changed> 

```
find ~ -type f -mtime -2                # finds all files you have modified in the last two days
locate <pattern>                        # finds files and dirs that are written into update file
which <application_name>                # location of application
whereis <application_name>              # searches for executables in set of directories
yum list installed | grep <mypattern>   # find Debian packages and refine search with grep pattern
```

### Finding things in files

```
grep pattern file           # provides lines in 'file' where pattern 'appears',
                            # if pattern is shell function use single-quotes: '>'


grep -H pattern             # -H prints out file name in front of pattern
grep 'pattern' file | wc    # pipes lines with pattern into word count wc (see chapter 8)
                            # wc arguments: -c: show only bytes, -w: show only words,
                            # -l: show only lines; help on regular expressions:
                            # $ man 7 regex or man perlre


find /home/my_dir -name '*.txt' | xargs grep -c ^.*  # counts line numbers on many
                            # files and records each count along with individual file
                            # name; find and xargs are used to circumvent the Linux
                            # wildcard limit to apply this function on thousands of files.
```

## Permissions and Ownership

List directories and files

```
ls -la # shows something like this for each file/dir: drwxrwxrwx
       # d: directory
       # rwx: read write execute
       # first triplet: user permissions (u)
       # second triplet: group permissions (g)
       # third triplet: other permissions (o)
```

Assign write and execute permissions to user and group

`chmod ug+rx my_file`

To remove all permissions from all three user groups

```
chmod ugo-rwx my_file
            # '+' causes the permissions selected to be added
            # '-' causes them to be removed
            # '=' causes them to be the only permissions that the file has.

chmod +rx public_html/ or $ chmod 755 public_html/ # Example for number system:
```

Change ownership

```
chown <user> <file or dir>         # changes user ownership
chgrp <group> <file or dir>        # changes group ownership
chown <user>:<group> <file or dir> # changes user & group ownership
```

## Useful Unix Commands

```
df          # disk space
free -g     # memory info in Megabytes
uname -a    # shows tech info about machine
bc          # command-line calculator (to exit type 'quit')
wget ftp://ftp.ncbi.nih.... # file download from web
/sbin/ifconfig # give IP and other network info
ln -s <original_filename> <new_filename> # creates symbolic link to file or directory
du -sh      # displays disk space usage of current directory
du -sh *    # displays disk space usage of individual files/directories
du -s * | sort -nr # shows disk space used by different directories/files sorted by size
```

## Process Management

General

```
top               # view top consumers of memory and CPU (press 1 to see per-CPU statistics)
who               # Shows who is logged into system
w                 # Shows which users are logged into system and what they are doing
ps                # Shows processes running by user
ps -e             # Shows all processes on system; try also '-a' and '-x' arguments
ps aux | grep <user_name> # Shows all processes of one user
ps ax --tree      # Shows the child-parent hierarchy of all processes
ps -o %t -p <pid> # Shows how long a particular process was running.
                  # (E.g. 6-04:30:50 means 6 days 4 hours ...)
Ctrl z <enter>    # Suspend (put to sleep) a process
fg                # Resume (wake up) a suspended process and brings it into foreground
bg                # Resume (wake up) a suspended process but keeps it running
                  # in the background.
Ctrl c            # Kills the process that is currently running in the foreground
kill <process-ID> # Kills a specific process
kill -9 <process-ID> # NOTICE: "kill -9" is a very violent approach.
                     # It does not give the process any time to perform cleanup procedures.
kill -l           # List all of the signals that can be sent to a proccess
kill -s SIGSTOP <process-ID> # Suspend (put to sleep) a specific process
kill -s SIGCONT <process-ID> # Resume (wake up) a specific process
renice -n <priority_value> # Changes the priority value, which range from 1-19,
                           # the higher the value the lower the priority, default is 10.
```

More on Terminating Processes

~~Terminating a Running Process~~ (Broken link. Also, we have a wiki!?)

## Text Viewing

```
more <my_file>  # views text, use space bar to browse, hit 'q' to exit
less <my_file>  # a more versatile text viewer than 'more', 'q' exits, 'G' moves to end of text,
                # 'g' to beginning, '/' find forward, '?' find backwards
cat  <my_file>  # concatenates files and prints content to standard output
```

## Text Editors

* **Vi** and **Vim**
  * Non-graphical (terminal-based) editor. Vi is guaranteed to be available on any system. Vim is the improved version of vi.
* **Emacs**
  * Non-graphical or window-based editor. You still need to know keystroke commands to use it. Installed on all Linux distributions and on most other Unix systems.
* **XEmacs**
  * More sophisticated version of emacs, but usually not installed by default. All common commands are available from menus. Very powerful editor, with built-in syntax checking, Web-browsing, news-reading, manual-page browsing, etc.
* **Pico**
  * Simple terminal-based editor available on most versions of Unix. Uses keystroke commands, but they are listed in logical fashion at bottom of screen.
* **Nano**
  * A simple terminal-based editor which is default on modern Debian systems.

### Vim Manual

#### Basics

`vim <my_file_name> # open/create file with vim`

Once you are in Vim the most important commands are `i` ,  `:`  and `ESC`. The `i` key brings you into the insert mode for typing. `ESC` brings you out of there. And the `:` key starts the command mode at the bottom of the screen. In the following text, all commands starting with `:` need to be typed in the command mode. All other commands are typed in the normal mode after hitting the `ESC` key.

**Modifier Keys to Control Vim**

```
i   # INSERT MODE
ESC # NORMAL (NON-EDITING) MODE
:   # commands start with ':'
:w  # save command; if you are in editing mode you have to hit ESC first!!
:q  # quit file, don't save
:q! # exits WITHOUT saving any changes you have made
:wq # save and quit
R   # replace MODE
r   # replace only one character under cursor
q:  # history of commands (from NORMAL MODE!), to reexecute one of them, select and hit enter!
:w new_filename     # saves into new file
:#,#w new_filename  # saves specific lines (#,#) to new file
:#                  # go to specified line number
```

#### Help

* **Online Help**
  * Find help on the web. Google will find answers to most questions on **vi** and **vim** (try searching for both terms).
  * [Purdue University Vi Tutorial](https://engineering.purdue.edu/ECN/Support/KB/Docs/ViTextEditorTutorial)
  * Animated Vim Tutorial: https://linuxconfig.org/vim-tutorial
  * Useful list of vim commands:
    * [Vim Commands Cheat Sheet](http://www.fprintf.net/vimCheatSheet.html)
    * [VimCard](http://tnerual.eriogerg.free.fr/vimqrc.pdf)

* **Help from Command Line**
> `vimtutor # open vim tutorial from shell`

* **Help in Vim**
```
:help                # opens help within vim, hit :q to get back to your file
:help <topic>        # opens help on specified topic
:help_topic| CTRL-]  # when you are in help this command opens help topic specified between |...|,
                     # CTRL-t brings you back to last topic
:help <topic> CTRL-D # gives list of help topics that contain key word
: <up-down keys>     # like in shell you get recent commands!!!!
```

* **Moving Around in Files**

```
$        # moves cursor to end of line
A        # same as $, but switches to insert mode
0 (zero) # moves cursor to beginning of line
CTRL-g   # shows at status line filename and the line you are on
SHIFT-G  # brings you to bottom of file, type line number (isn't displayed) then SHIFT-G # brings you to specified line#
```

* **Line Wrapping and Line Numbers**

```
:set nowrap # no word wrapping, :set wrap # back to wrapping
:set number # shows line numbers, :set nonumber # back to no-number mode
```

* **Working with Many Files & Splitting Windows**

```
vim -o *.txt # opens many files at once and displays them with horizontal
             # split, '-O' does vertical split
vim *.txt    # opens many files at once; ':n' switches between files
```

```
:wall or :qall # write or quit all open files
:args *.txt    # places all the relevant files in the argument list
:all           # splits all files in the argument list (buffer) horizontally
CTRL-w         # switch between windows
:split         # shows same file in two windows
:split <file-to-open> # opens second file in new window
:vsplit        # splits windows vertically, very useful for tables, ":set scrollbind" let's you scroll all open windows simultaneously
:close         # closes current window
:only          # closes all windows except current one
```

* **Spell Checking & Dictionary**

```
:set spell # turns on spell checking
:set nospell # turns spell checking off
:! dict <word> # meaning of word
:! wn 'word' -over # synonyms of word
```

* **Enabling Syntax Highlighting**

```
:set filetype=perl # Turns on syntax coloring for a chosen programming language.
:set syntax on # Turns syntax highlighting on
:set syntax off # Turns syntax highlighting off
```

* **Undo and Redo**

```
u      # undo last command
U      # undo all changes on current line
CTRL-R # redo one change which was undone
```

* **Deleting Things**

```
x   # deletes what is under cursor
dw  # deletes from curser to end of word including the space
de  # deletes from curser to end of word NOT including the space
cw  # deletes rest of word and lets you then insert, hit ESC to continue with NORMAL mode
c$  # deletes rest of line and lets you then insert, hit ESC to continue with with NORMAL mode
d$  # deletes from cursor to the end of the line
dd  # deletes entire line
2dd # deletes next two lines, continues: 3dd, 4dd and so on.
```

* **Copy & Paste**

```
yy # copies line, for copying several lines do 2yy, 3yy and so on
p # pastes clipboard behind cursor
```

* **Search in Files**

```
/my_pattern # searches for my_pattern downwards, type n for next match
?my_pattern # seraches for my_pattern upwards, type n for next match
:set ic # switches to ignore case search (case insensitive)
:set hls # switches to highlight search (highlights search hits)
```

* **Replacements with Regular Expression Support**

Great intro: [A Tao of Regular Expressions](http://www.scootersoftware.com/RegEx.html)

```
:s/old_pat/new_pat/  # replaces first occurrence in a line
:s/old_pat/new_pat/g  # replaces all occurrence in a line
:s/old_pat/new_pat/gc  # add 'c' to ask for confirmation
:#,#s/old_pat/new_pat/g  # replaces all occurrence between line numbers: #,#
:%s/old_pat/new_pat/g  # replaces all occurrence in file
:%s/\(pattern1\)\(pattern2\)/\1test\2/g  # regular expression to insert, you need here '\' in front of parentheses (<# Perl)
:%s/\(pattern.*\)/\1 my_tag/g  # appends something to line containing pattern (<# .+ from Perl is .* in VIM)
:%s/\(pattern\)\(.*\)/\1/g  # removes everything in lines after pattern
:%s/\(At\dg\d\d\d\d\d\.\d\)\(.*\)/\1\t\2/g  # inserts tabs between At1g12345.1 and Description
:%s/\n/new_pattern/g  # replaces return signs
:%s/pattern/\r/g  # replace pattern with return signs!!
:%s/\(\n\)/\1\1/g  # insert additional return signs
:%s/\(^At\dg\d\d\d\d\d.\d\t.\{-}\t.\{-}\t.\{-}\t.\{-}\t\).\{-}\t/\1/g  # replaces content between 5th and 6th tab (5th column), '{-}' turns off 'greedy' behavior
:#,#s/\( \{-} \|\.\|\n\)/\1/g  # performs simple word count in specified range of text
:%s/\(E\{6,\}\)/<font color="green">\1<\/font>/g  # highlight pattern in html colors, here highlighting of >= 6 occurences of Es
:%s/\([A-Z]\)/\l\1/g  # change uppercase to lowercase, '%s/\([A-Z]\)/\u\1/g' does the opposite
:g/my_pattern/ s/\([A-Z]\)/\l\1/g | copy $  # uses 'global' command to apply replace function only on those lines that match a certain pattern. The 'copy $' command after the pipe '|' prints all matching lines at the end of the file.
:args *.txt | all | argdo %s/\old_pat/new_pat/ge | update  # command 'args' places all relevant files in the argument list (buffer); 'all' displays each file in separate split window; command 'argdo' applies replacement to all files in argument list (buffer); flag 'e' is necessary to avoid stop at error messages for files with no matches; command 'update' saves all changes to files that were updated.
```

* **Useful Utilities in Vim**

  * Matching Parentheses
    * Place cursor on (, [ or { and type % # cursor moves to matching parentheses

  * Printing and Inserting Files
    * `:ha  # prints entire file`
    * `:#,#ha  # prints specified lines: #,#`
    * `:r <filename>  # inserts content of specified file after cursor`

  * Convert Text File to HTML Format
    * `:runtime! syntax/2html.vim  # run this command with open file in Vim`

  * Shell Commands in Vim
    * `:!<SHELL_COMMAND> <ENTER>  # executes any shell command, hit <enter> to return`
    * `:sh  # switches window to shell, 'exit' switches back to vim`

  * Using Vim as Table Editor
    * `v` starts visual mode for selecting characters
    * `V` starts visual mode for selecting lines`
    * `CTRL-V` starts visual mode for selecting blocks (use CTRL-q in gVim under Windows). This allows column-wise selections and operations like inserting and deleting columns. To restrict substitute commands to a column, one can select it and switch to the command-line by typing `:`. After this the substitution syntax for a selected block looks like this: `'<,'>s///.`
    * `:set scrollbind` starts simultaneous scrolling of 'vsplitted' files. To set to horizontal binding of files, use command `:set scrollopt=hor` (after first one). Run all these commands before the `:split` command.
    * `:AlignCtrl I= \t then :%Align` This allows to align tables by column separators (here '\t') when the [Align utility from Charles Campbell's](http://vim.sourceforge.net/scripts/script.php?script_id=294) is installed. To sort table rows by selected lines or block, perform the visual select and then hit F3 key. The rest is interactive. To enable this function, one has to include in the `.vimrc` file the [Vim sort script](http://biocluster.ucr.edu/%7Etgirke/Documents/UNIX/vim/vim_sort_fct.txt) from Gerald Lai.

* **Modify Vim Settings**

The default settings in Vim are controlled by the `.vimrc` file in your home directory.

  * see last chapter of vimtutor (start from shell)
  * useful [.vimrc sample](http://phuzz.org/vimrc.html)
  * when vim starts to respond very slowly then one may need to delete the `.viminf*` files in home directory

## The Unix Shell
When you log into UNIX/LINUX system, then is starts a program called the Shell. It provides you with a working environment and interface to the operating system. Usually there are several different shell programs installed. The shell program bash is one of the most common ones.

```
finger <user_name> # shows which shell you are using
chsh -l # gives list of shell programs available on your system (does not work on all UNIX variants)
<shell_name> # switches to different shell
```

### STDIN, STDOUT, STDERR, Redirections, and Wildcards

See [LINUX HOWTOs](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)


By default, UNIX commands read from standard input (STDIN) and send their output to standard out (STDOUT).

You can redirect them by using the following commands:

```
<beginning-of-filename>*         # * is wildcard to specify many files
ls > file                        # prints ls output into specified file
command < my_file                # uses file after '<' as STDIN
command >> my_file               # appends output of one command to file
command | tee my_file            # writes STDOUT to file and prints it to screen
command > my_file; cat my_file   # writes STDOUT to file and prints it to screen
command > /dev/null              # turns off progress info of applications by redirecting
                                 # their output to /dev/null
grep my_pattern my_file | wc     # Pipes (|) output of 'grep' into 'wc'
grep my_pattern my_non_existing_file 2 > my_stderr # prints STDERR to file
```

### Useful shell commands

```
cat <file1> <file2> > <cat.out>      # concatenate files in output file 'cat.out'
paste <file1> <file2> > <paste.out>  # merges lines of files and separates them by tabs (useful for tables)
cmp <file1> <file2>                  # tells you whether two files are identical
diff <fileA> <fileB>                 # finds differences between two files
head -<number> <file>                # prints first lines of a file
tail -<number> <file>                # prints last lines of a file
split -l <number> <file>             # splits lines of file into many smaller ones
csplit -f out fasta_batch "%^>%" "/^>/" "{*}" # splits fasta batch file into many files
                                     # at '>'
sort <file>                          # sorts single file, many files and can merge (-m)
                                     # them, -b ignores leading white space, ...
sort -k 2,2 -k 3,3n input_file > output_file # sorts in table column 2 alphabetically and
                                     # column 3 numerically, '-k' for column, '-n' for
                                     # numeric
sort input_file | uniq > output_file # uniq command removes duplicates and creates file/table
                                     # with unique lines/fields
join -1 1 -2 1 <table1> <table2>     # joins two tables based on specified column numbers
                                     # (-1 file1, 1: col1; -2: file2, col2). It assumes
                                     # that join fields are sorted. If that is not the case,
                                     # use the next command:
sort table1 > table1a; sort table2 > table2a; join -a 1 -t "$(echo -e '\t')" table1a table2a > table3                               # '-a <table>' prints all lines of specified table!
                                     # Default prints only all lines the two tables have in
                                     # common. '-t "$(echo -e '\t')" ->' forces join to
                                     # use tabs as field separator in its output. Default is
                                     # space(s)!!!
cat my_table | cut -d , -f1-3        # cut command prints only specified sections of a table,
                                     # -d specifies here comma as column separator (tab is
                                     # default), -f specifies column numbers.
grep                                 # see chapter 4
egrep                                # see chapter 4
```

## Screen

A Visual Introduction to Screen
1. http://blogamundo.net/code/screen/
+  http://fosswire.com/post/2008/08/video-tutorial-getting-started-with-gnu-screen/

### Starting a New Screen Session

```
screen                 # Start a new session
screen -S <some-name>  # Start a new session and gives it a name
```

Commands to Control Screen

```
Ctrl-a d #  Detach from the screen session
Ctrl-a c # Create a new window inside the screen session
Ctrl-a Space # Switch to the next window
Ctrl-a a # Switch to the window that you were previously on
Ctrl-a " # List all open windows. Double-quotes " are typed with the Shift key
Ctrl-d or type exit # Exit out of the current window. Exiting form the last window will end the screen session
Ctrl-a [ # Enters the scrolling mode. Use Page Up and Page Down keys to scroll through the window. Hit the Enter key twice to return to normal mode. 
```

### Attaching to Screen Sessions

From any computer, you can attach to a screen session after SSH-ing into a server.

```
screen -r              # Attaches to an existing session, if there is only one
screen -r              # Lists available sessions and their names, if there are more then one session running
screen -r <some-name>  # Attaches to a specific session
screen -r <first-few-letters-of-name> # Type just the first few letters of the name
                       # and you will be attached to the session you need
```

### Destroying Screen Sessions

1. Terminate all programs that are running in the screen session. The standard way to do that is: `Ctrl-c`
2. Exit out of your shell: `exit`
3. Repeat steps 1 and 2 until you see the message: `[screen is terminating]`

There may be programs running in different windows of the same screen session. That's why you may need to terminate programs and exit shells multiple time.

### Tabs and a Reasonably Large History Buffer

For a better experience with screen, run

```
cp ~/.screenrc ~/.screenrc.backup 2> /dev/null
echo 'startup_message off
defscrollback 10240
caption always "%{=b dy}{ %{= dm}%H %{=b dy}}%={ %?%{= dc}%-Lw%?%{+b dy}(%{-b r}%n:%t%{+b dy})%?(%u)%?%{-dc}%?%{= dc}%+Lw%? %{=b dy}}"
' > ~/.screenrc
```

### More on Terminating Processes

[Terminating a Running Process](https://www.digitalocean.com/community/tutorials/how-to-use-ps-kill-and-nice-to-manage-processes-in-linux)


## Simple One-Liner Shell Scripts

Web page for [script download](http://linuxcommand.org/script_library.php).

Renames many files *.old to *.new. To test things first, replace 'do mv' with 'do echo mv':

```
for i in *.input; do mv $i ${i/\.old/\.new}; done
for i in *\ *; do mv "$i" "${i// /_}"; done # Replaces spaces in files by underscores
```

Run an application in loops on many input files:

```
for i in *.input; do ./application $i; done
```

Run fastacmd from BLAST program in loops on many *.input files and create corresponding *.out files:

```
for i in *.input; do fastacmd -d /data/../database_name -i $i > $i.out; done
```

Run SAM's target99 on many input files:

```
for i in *.pep; do target99 -db /usr/../database_name -seed $i -out $i; done
Search in many files for a pattern and print occurrences together with file names.
for j in 0 1 2 3 4 5 6 7 8 9; do grep -iH <my_pattern> *$j.seq; done
```

Example of how to run an interactive application (tmpred) that asks for file name input/output:

```
for i in *.pep; do echo -e "$i\n\n17\n33\n\n\n" | ./tmpred $i > $i.out; done
```

Run BLAST2 for all *.fasa1/*.fasta2 file pairs in the order specified by file names and write results into one file:

```
for i in *.fasta1; do blast2 -p blastp -i $i -j ${i/_*fasta1/_*fasta2} >> my_out_file; done
```
    This example uses two variables in a for loop. The content of the second variable gets specified in each loop by a replace function.

Runs BLAST2 in all-against-all mode and writes results into one file ('-F F' turns low-complexity filter off):

```
for i in *.fasta; do for j in *.fasta; do blast2 -p blastp -F F -i $i -j $j >> my_out_file; done; done;
```

### How to write a real shell script

1. Create file which contains an interpreter as the first line:
    ```
    #!/bin/bash
    ```
+ Place shell commands in file below the interpreter line using a text editor.
+ Make file executable:
    ```
    chmod +x my_shell_script
    ```
+ Run shell script like this:
    ```
    ./my_shell_script
    ```
+ Place it into your /rhome/<username>/bin directory
    ```
    mkdir -p ~/bin
    mv my_shell_script ~/bin/
    ```
+ Add the bin path to your shell permanently:
    ```
    echo 'export PATH=~/bin:$PATH' >> ~/.bashrc
    source ~/.bashrc
    ```

## Simple One-Liner Perl Scripts

*Small collection of useful one-liners:*
```
perl -p -i -w -e 's/pattern1/pattern2/g' my_input_file
            # Replaces a pattern in a file by a another pattern using regular expressions.
            # $1 or \1: back-references to pattern placed in parentheses
            # -p: lets perl know to write program
            # -i.bak: creates backup file *.bak, only -i doesn't
            # -w: turns on warnings
            # -e: executable code follows
```

*Parse lines based on patterns:*
```
perl -ne 'print if (/my_pattern1/ ? ($c=1) : (--$c > 0)); print if (/my_pattern2/ ? ($d = 1) : (--$d > 0))' my_infile > my_outfile
            # Parses lines that contain pattern1 and pattern2.
            # The following lines after the pattern can be specified in '$c=1' and '$d=1'.
            # For logical OR use this syntax: '/(pattern1|pattern2)/'.
```

## Remote Copy: wget, scp, ncftp

### Wget

Use wget to download a file from the web:
```
wget ftp://ftp.ncbi.nih.... # file download from www; add option '-r' to download entire directories
```

### SCP

Use scp to copy files between machines (ie. laptop to server):
```
scp source target # Use form 'userid@machine_name' if your local and remote user ids are different.
                  # If they are the same you can use only 'machine_name'.
```

Here are more scp examples:
```
scp user@remote_host:file.name . # Copies file from server to local machine (type from local
                                 # machine prompt). The '.' copies to pwd, you can specify                                              # here any directory, use wildcards to copy many files.

scp file.name user@remote_host:~/dir/newfile.name
                                                                       # Copies file from local machine to server.
                              
scp -r user@remote_host:directory/ ~/dir
                                 # Copies entire directory from server to local machine.
```

### Nice FTP

From the linux command line run ncftp and use it to get files:
```
ncftp
ncftp> open ftp.ncbi.nih.gov
ncftp> cd /blast/executables
ncftp> get blast.linux.tar.Z (skip extension: @)
ncftp> bye
```

## Archiving and Compressing

### Creating Archives

```
tar -cvf my_file.tar mydir/    # Builds tar archive of files or directories. For directories, execute command in parent directory. Don't use absolute path.    
tar -czvf my_file.tgz mydir/   # Builds tar archive with compression of files or directories. For
                               # directories, execute command in parent directory. Don't use absolute path.
zip -r mydir.zip mydir/        # Command to archive a directory (here mydir) with zip.
tar -jcvf mydir.tar.bz2 mydir/ # Creates *.tar.bz2 archive
```

### Viewing Archives

```
tar -tvf my_file.tar
tar -tzvf my_file.tgz
```

### Extracting Archives

```
tar -xvf my_file.tar
tar -xzvf my_file.tgz
gunzip my_file.tar.gz # or unzip my_file.zip, uncompress my_file.Z,
                      # or bunzip2 for file.tar.bz2
find -name '*.zip' | xargs -n 1 unzip # this command usually works for unzipping
                      # many files that were compressed under Windows
tar -jxvf mydir.tar.bz2 # Extracts *.tar.bz2 archive
```

Try also:
```
tar zxf blast.linux.tar.Z
tar xvzf file.tgz
```

Important options:
```
f: use archive file
p: preserve permissions
v: list files processed
x: exclude files listed in FILE
z: filter the archive through gzip 
```

## Simple Installs

### Systems-wide installations

### Applications in user accounts

### Installation of RPMs

## Environment Variables

```
xhost user@host                # adds X permissions for user on server.
echo $DISPLAY                  # shows current display settings
export DISPLAY=<local_IP>:0    # change environment variable
unsetenv DISPLAY               # removes display variable
env                            # prints all environment variables
```

List of directories that the shell will search when you type a command:
```
echo $PATH
```
You can edit your default DISPLAY setting for your account by adding it to file .bash_profile

## Exercises

Exercise 1
1. Download proteome of Halobacterium spec. with wget and look at it:
module load ncbi-blast/2.2.26 # Loads legacy blastall
wget ftp://ftp.ncbi.nlm.nih.gov/genomes/genbank/archaea/Halobacterium_salinarum/representative/GCA_000069025.1_ASM6902v1/GCA_000069025.1_ASM6902v1_protein.faa.gz
gunzip GCA_000069025.1_ASM6902v1_protein.faa.gz
mv GCA_000069025.1_ASM6902v1_protein.faa AE004437.faa

less AE004437.faa  # press q to quit

2. Simple Analysis:

a) How many predicted proteins are there?
grep '^>' AE004437.faa --count

b) How many proteins contain the pattern "WxHxxH" or "WxHxxHH"?
egrep 'W.H..H{1,2}' AE004437.faa --count

c) Use the find function (/) in 'less' to fish out the protein IDs containing the pattern or more elegantly do it with awk:
awk --posix -v RS='>' '/W.H..(H){1,2}/ { print ">" $0;}' AE004437.faa | less # press q to quit

3. Create a BLASTable database with formatdb:

    ls # before

    formatdb -i AE004437.faa -p T -o T

    ls # after
    '-p F' for nucleotide and '-p T' for protein database; '-o T' parse SeqId and create indexes 

4. Generate myseq.fasta

a) Generate list of sequence IDs for the above pattern match result (i.e. retrieve my_IDs from step 2c). Alternatively, download the pre-generated file with wget.

b) Retrieve the corresponding sequences for these IDs with the fastacmd command from the blastable database:

    wget http://biocluster.ucr.edu/~tgirke/Documents/UNIX/my_IDs

    fastacmd -d AE004437.faa -i my_IDs > myseq.fasta

    less myseq.fasta # press q to quit


5. (Optional) Looking at several different patterns:

a) Generate several lists of sequence IDs from various pattern match results (i.e. retrieve a.my_ids, b.my_ids, and  c.my_ids from step 2c).

b) Retrieve the sequences in one step using the fastacmd in a for-loop:
for i in *.my_ids; do fastacmd -d AE004437.faa -i $i > $i.fasta; done


6. Run blastall with a few proteins in myseq.fasta against your newly created Halobacterium proteome database.
Create first a complete blast output file  including alignments. In a second step use the 'm -8' option to obtain a tabular output (i.e. tab separated values).

    blastall -p blastp -i myseq.fasta -d AE004437.faa -o blastp.out -e 1e-6 -v 10 -b 10
    blastall -p blastp -i myseq.fasta -d AE004437.faa -m 8 -e 1e-6 > blastp.tab

    less blastp.out # press q to quit
    less -S blastp.tab # -S disables line wrapping, press q to quit

The filed descriptions of the Blast tabular output (from the "-m 8" option) are available here.
1  Query (The query sequence id)
2  Subject (The matching subject sequence id)
3  % id
4  alignment length
5  mismatches
6  gap openings
7  q.start
8  q.end
9  s.start
10 s.end
11 e-value
12 bit score

Is your blastp.out file equivalent to this one?

7. Parse blastall output into Excel spread sheet

    a) Using biocore parser

blastParse -i blastp.out -o blast.xls -c 5

    b) Using BioPerl parser
    bioblastParse.pl blastp.out > blastparse.txt     

Table of Contents

Exercise 2

    Split sample fasta batch file with csplit (use sequence file myseq.fasta from Exercise 1). 
    csplit -z myseq.fasta '/>/' '{*}'
    Delete some of the files generated by csplit
    Concatenate single fasta files from (step 1) into to one file with cat (e.g. "cat file1 file2 file3 > bigfile") .
    BLAST two related sequences, retrieve the result in tabular format and use "comm" to identify common hit IDs in the two tables.

Exercise 3

    Run HMMPFAM search with proteins from Exercise 1 against Pfam database (will take ~3 minutes)

        hmmscan -E 0.1 --acc /srv/projects/db/pfam/2011-12-09-Pfam26.0/Pfam-A.hmm myseq.fasta > output.pfam

        Easier to parse/process tabular output
        hmmscan -E 0.1 --acc --tblout output.pfam /srv/projects/db/pfam/2011-12-09-Pfam26.0/Pfam-A.hmm myseq.fasta # also try --domtblout

Which query got the most hits? How many hits were found that query?

Exercise 4

    Create multiple alignment with ClustalW (e.g. use sequences with 'W.H..HH' pattern)

        clustalw myseq.fasta

        mv myseq.aln myalign.aln

Exercise 5

    Reformat alignment into PHYILIP format using 'seqret' from EMBOSS

        seqret clustal::myalign.aln phylip::myalign.phylip

Exercise 6

    Create neighbor-joining tree with PHYLIP

        cp myalign.phylip infile
        protdist     # creates distance matrix (you may need to press 'R' and then 'Y')
        cp outfile infile

        neighbor     # use default settings (press 'Y')
        cp outtree intree

        retree # displays tree and can use midpoint method for defining root of tree, my typical command sequence is: 'N' (until you see PHYLIP) 'Y' 'M' 'W' 'R' 'R' 'X'
        cp outtree tree.dnd
        View your tree in TreeBrowse or open it in TreeView 
