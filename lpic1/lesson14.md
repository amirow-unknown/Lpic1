---
name: lpic
lesson: "14"
topic: files management
---
```
wild cards
cp -r 
cp -v
mv -f
mv -i
rm 
rm -r -f -i
mkdir -p
rmdir
```
#ls -> to list the files
	-l -> list
	-r -> reverse
	-t -> shows the time of creation of files
	-h -> human readable for files spaces
	-1 -> shows the each file in 1 line
#cp -> to copy the files and directories
	-r -> recursively(used for copying directory too)
	-v -> verbose(show the process)
#mv -> to move files or directories or raname them
	-f -> force and don't ask
	-i -> ask for valuale process
#rm -> removing files and directories
	-f --> force
	-i --> ask 
	-r --> recursively(when you wanna remove directories too) ->> `rm -r directory1`
#mkdir -> creating directory
	-p ----> to create newdirectory in newdirectory in .... ->>> `mkdir -p amir/aml/ak/sk`
#rmdir -> removes the directory but not directories which are not empty, so use `rm -rf`
#touch -> used to create file. also if you touch an existed file, the file's creation time changed to current time.
#file -> shows the format of files
#dd --> to copy,format,bootable --> `dd if=/path of=/path bs=int` -> if=file to cop, of= where to past, bs---> number of data to copy from A to b.
#find => to find and crowling
	-type --> f(file),d(directory)
	-name --> name of the file
	-iname -->like -name but insensitive
	-empty --> empty files or directories
	-exec --> `find ........ -exec command {} \;` , `find ..... -exec mv '{}' '{}.txt' \;` 
	***Some Switch's:***
	- newer ---> `find ..... -newer file2` ---> find files which are newer than file2
	- mmin ---> `find ..... -mmin NUMBER` ---> find files which modified *NUMBER *ago.
	- amin
	***Some tricks:***
	-ls --> `find . -ls` ---> runs ls command too
	
# wild cards
`*` -> all files and directories
?
[a,2,f,...] -> files which as a or 2 or f or ....
[a-g] -> files which has words from a to g(small letters)
[A-G] -> like above but for captal words
[a-gA-G] -> all files wich have small or captal a to g words
`*-[a,2][a-m]*` -> files which has `-` or a or 2 or from a to m
[!x] -> all files which don't contains x word

### Compressing and extracting files:
- There are 2 terms which we must learn at first:
	#archiving ----> to create a archive of files
	#compressing -----> create a compressed file which contains some files or file and has less byte.

- #### #gzip ---> compress files by .gz prefix
	***compressing*** ==> `gzip filename` ----> filename.gz
	***decompressing ==> ***`gunzip filename.gz` ---> filename

- #### #bzip2 ---> compress files by .bz2 prefix
	***compressing*** ==> `bzip2 filename ---> filename.bz2`
	***decompressing ***==> `bunzip2 filename.bz2 ---> filename`

- #### #xz ----> compress file by .xz prefix
	***compressing*** ==> `xz filename ---> filename.xz`
	***decompressing***==> `unxz filename.xz` ----> filename

### *Tar*:
- #tar is a powerful tool to *archive* and *compress* files.
- #archiving ---> `tar -cf filenametobe files files file` 
- #extracting ---> `tar -xf filename.tar`
- ***how to archive and also compress?*** by switches #-z for #gzip and #-b for #bzip2:
	`tar cf forlearning.tar file file` --->  forlearning.tar
	`tar xf forlearning.tar` ----> file file .....
	`tar cfz forlearning.tar.gz file file file` -----> forlearning.tar.gz
	`tar -cfb forlearmomg.tar.bz2 file file file` ----> forlearning.tar.bz2
	- to extract we use #tar #xf, it doesn't different for compress files.
	- #-v ----> verbose
	- #-r ----> append new files to archive or compress

