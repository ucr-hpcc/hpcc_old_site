---
layout: page
title: Linux Cluster - Sharing Data
permalink: manuals_linux-cluster_sharing.html
---

## Permissions
It is useful to share data and results with other users on the cluster, and we encourage collaboration  The easiest way to share a file is to place it in a location that both users can access. Then the second user can simply copy it to a location of their choice. However, this requires that the file permissions permit the second user to read the file.
Basic file permissions on Linux and other Unix like systems are composed of three groups: owner, group, and other. Each one of these represents the permissions for different groups of people: the user who owns the file, all the group members of the group owner, and everyone else, respectively  Each group has 3 permissions: read, write, and execute, represented as r,w, and x. For example the following file is owned by the user 'jhayes' (with read, write, and execute), owned by the group 'operations' (with read and execute), and everyone else cannot access it.

```bash
jhayes@pigeon:~$ ls -l myFile
-rwxr-x---   1 jhayes bioinfo 1.6K Nov 19 12:32 myFile
```

If you wanted to share this file with someone outside the 'bioinfo' group, read permissions must be added to the file for 'other':

```bash
jhayes@pigeon:~$ chmod o+r myFile
```

To learn more about ownership, permissions, and groups please visit [Linux Basics Permissions](manuals_linux-basics_permissions).

## Set Default Permissions

In Linux, it is possible to set the default file permission for new files. This is useful if you are collaborating on a project, or frequently share files and  you do not want to be constantly adjusting permissions  The command responsible for this is called 'umask'. You should first check what your default permissions currently are by running 'umask -S'.

```bash
jhayes@pigeon:~$ umask -S
u=rwx,g=rx,o=rx
```

To set your default permissions, simply run umask with the correct options. Please note, that this does not change permissions on any existing files, only new files created after you update the default permissions. For instance, if you wanted to set your default permissions to you having full control, your group being able to read and execute your files, and no one else to have access, you would run:

```bash
jhayes@pigeon:~$ umask u=rwx,g=rx,o=
```

It is also important to note that these settings only affect your current session.
If you log out and log back in, these settings will be reset.
To make your changes permanent you need to add them to your `.bashrc` file, which is a hidden file in your home directory (if you do not have a `.bashrc` file, you will need to create an empty file called `.bashrc` in your home directory).
Adding umask to your `.bashrc` file is as simple as adding your umask command (such as `umask u=rwx,g=rx,o=r`) to the end of the file.
Then simply log out and back in for the changes to take affect. You can double check that the settings have taken affect by running `umask -S`.

## Futher Reading

* [UNIX File Permissions Tutorial](http://manuals.bioinformatics.ucr.edu/home/linux-basics#TOC-Permissions-and-Ownership)
* [What is Umask and How To Setup Default umask Under Linux?](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

## Copying bigdata

Rsync can:

* Copy (transfer) directories between different locations
* Perform transfers over the network via SSH
* Compare large data sets (`-n, --dry-run` option)
* Resume interrupted transfers

Rsync Notes:
* Rsync can be used on Windows, but you must install [Cygwin](https://cygwin.com). Most Mac and Linux systems already have rsync install by default.
* Always put the / after both folder names, e.g: `FOLDER_A/` Failing to do so will result in the nesting folders every time you try to resume. If you don't put / you will get a second folder_B inside folder_B `FOLDER_A/FOLDER_A/`
* Rsync only copies by default.
* Once the rsync command is done, run it again. The second run will be shorter and can be used as a double check. If there was no output from the second run then nothing changed.
* To learn more try `man rsync`

If you are transfering to, or from, your laptop/workstation it is required that you run the rsync command locally from your laptop/workstation.

To transfer to the cluster:

```bash
rsync -av --progress FOLDER_A/ biocluster.ucr.edu:FOLDER_A/
```

To transfer from the cluster:

```bash
rsync -av --progress biocluster.ucr.edu:FOLDER_A/ FOLDER_A/
```

Rsync will use SSH and will ask you for your cluster password, the same way SSH or SCP does.

If your rsync transer was interrupted, rsync can continue where it left off. Simply run the same command again to resume.


## Copying large folders on the cluster between Directories

If you want to syncronize the contents from one directory to another, then use the following:

```bash
rsync -av --progress PATH_A/FOLDER_A/ PATH_B/FOLDER_A/
```

Rsync does not move but only copies. Thus you would need to delete the original once you confirm that everything has been transfered.


## Copying large folders between the cluster and other servers

If you want to copy data from the cluster to your own server, or another remote system, use the following:

```bash
rsync -ai FOLDER_A/ sever2.xyz.edu:FOLDER_A/
```

The sever2.xyz.edu machine must be a server that accepts Rsync connections via SSH.
