# Listing Files
* `pwd`: print current work directory
* `ls`: listing files and directories
    * `-a`: list all files hidden and visible
    * `-F`: put a `/` at then end of listed directories or `@` for symbolic links and `*` for executables
    * `-l`: show long listing. show permissions, file size, ownership
    * `-r`: reverse sorting
    * `-t`: sort by time
    * `-h`: put size in a human readable format
    * `-d`: show info about the directory itself
    * `-i`: print the file's file serial number (inode number)

# File Types

### Linux have the following file types:
* Regurlar files
* Directories
* Symbolic links
* Block devices
* Character devices
* Named pipes
* Sockets

### Everything in linux is a file
* for example `ls -l $(tty)` will evaluate the output of tty command first then pass it to `ls`
* `lsblk`: list blocks. The blocks are the disks and partitions.
    * block devices starts with `b` for example: `brw-rw----. 1 root disk 8, 0 Aug 27 06:26 /dev/sda`
* `lsb_release -d`: returns the version of current os
* `rpm -qf $(which lsb_release)`: querying the package that has `lsb_release`

# Working with Files
* `cp`: copy file from one place to another. User must have the permissions to read from the source
and the write to the destination.
    * `cp /etc/hosts /Documents`
    * `-i`: interactive mode. will prompt only if user were about to overwrite a file
    * `cp * ../Desktop/`: copy all files in current directory to Desktop
* `mv`: move files from one place to another. Also used to rename files
    * `mv hosts localhosts`: rename hosts to localhosts
    * `mv localhosts ../Desktop/`: move file localhosts to Desktop
    * `-i`: interactive mode. will prompt only if user were about to overwrite a file
    * `mv * ../Desktop/`: move all files in current directory to Desktop
* `rm`: remove files
    * `-i`: interactive mode. will prompt to ensure user wants to remove the file

# Working with Directories
* `mkdir`: Create directory
    * `-p`: create parent directories. Example: `mkdir -p sales/test`
    * `-m`: set permissions while creating the directory. Example: `mkdir -m 777 test`
* `cp -R`: copy directory recursively from one place to another. User must have the permissions to read from the source
and the write to the destination.
    * example `cp -R /etc /Documents`
* `rm -rf`: remove directory recursively. **Must** if directory not empty

# Links
* **Hard Links:**
    * `ln f1 f2`: linking the two files f1 and f2
    * A file in the file system is basically a link to an inode. 
    A hard link then just creates another file with a link to the same underlying inode.
    When you delete a file it removes one link to the underlying inode. 
    The inode is only deleted (or deletable/over-writable) when all links to the inode have been deleted.
    * Once a hard link has been made the link is to the inode. 
    deleting renaming or moving the original file will not affect the hard link as it links to the underlying inode. 
    Any changes to the data on the inode is reflected in all files that refer to that inode.
    * Hard links are only valid within the same File System. Symbolic links can span file systems as they are simply the name of another file.

* **Soft Links:**
    * `ln -s f1 f2`: linking the two files f1 and f3
    * A symbolic link is a link to another name in the file system.
    * This can be anywhere in a system's file tree, and doesn't even have to exist when the link is created.
    * The target path can be relative or absolute.    

