* `cat`: concatenate command
    * `cat filename`: shows content of the file
    * `cat file1 file2`: Shows both of the files as one

* `wc`: word count
    * `wc -l file`: returns line count of the file

* `less`: you can be page through big file with `less`
    * use `pageup` and `pagedown`
    * use `/` to search for word, hit `n` to go through the next matches
    * use `?` to search for word backward, hit `n` to go through the next matches
    * use `q` to quit less.

* `head`: shows the top of the file
    * `head filename`
    * `head -n 3 filename`: shows the first 3 lines of the file

* `tail`: shows the bottom of the file
    * `tail filename`
    * `tail -n 3 filename`: shows the last 3 lines of the file

* `sed`: to edit files
    * `sed -i`: edit files in place 
        * Example: `sed -i '/^#/d;/^$/d' filename`: remove (d) comments and empty lines from file
        * clean_file function takes the first arugment as the file name`function clean_file { sed -i '/^#/d;/^$/d' $1}`

* Comparing Files:
    * `diff`: Compare two files
        * Example: `diff file1 file2`, show the difference between `file1` and `file2`
        * You can't compare binary files with `diff`
    * We can compare binary files using `checksums`

* Finding Files:
    * `find`: used to fine files
        * Example: `find /usr/share/doc/  -name '*.pdf'` search recursively for `pdf` files
        * We can execute a commands on found files
            * `find /usr/share/doc/  -name '*.pdf' -exec cp {} . \;`, copies `pdf` file found to current dir
            * `find -name '*.pdf' -delete`: delete all found files in the current directory (default dir). 
        * We can search by file type:
            * `find /etc/ -type l`: Searches for files of type symbolic link
        * We can specify level of the search with `-maxdepth`
            * `find /etc/ -maxdepth 1 -type l`
        * We can search by size
            * `find /boot -size +10000k -type f -exec du -h {} \;`: find files bigger than `10mb` of regular type and show disk usage in human readable format