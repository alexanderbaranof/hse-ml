# Interfaces I

## Command-line and text interfaces

Exercise: Give two examples of asynchronous communication. Give two examples of synchronous communication.

Asynchronous communication: email correspondence, ftp-server for file exchange

Synchronous communication: video streaming because all viewers have the same synchronous picture, voice group calls, such as ClubHouse

## Using a CLI

### Reading command specifications

#### Exercise: Compare the output of ls vs ls -l and ls -a; describe how they are similar, and how they are different.

"ls" - shows files and folders in the current directory

```
$ ls
alexanderbaranof@192 SCICOMP % ls
READIND1	READING3	READING5	testfile
READING2	READING4	READING6	testfile2
alexanderbaranof@192 SCICOMP % 

```

"ls -l" - shows files and folders in the current directory with detailed information and file permissions

```
alexanderbaranof@192 SCICOMP % ls -l
total 16
drwxr-xr-x  3 alexanderbaranof  staff  96 19 июн 13:44 READIND1
drwxr-xr-x  3 alexanderbaranof  staff  96 19 июн 16:00 READING2
drwxr-xr-x  3 alexanderbaranof  staff  96 19 июн 19:31 READING3
drwxr-xr-x  2 alexanderbaranof  staff  64 19 июн 13:43 READING4
drwxr-xr-x  3 alexanderbaranof  staff  96 19 июн 16:34 READING5
drwxr-xr-x  3 alexanderbaranof  staff  96 19 июн 16:34 READING6
-rw-r--r--  1 alexanderbaranof  staff   4 19 июн 18:46 testfile
-rw-r--r--  1 alexanderbaranof  staff   5 19 июн 18:46 testfile2
alexanderbaranof@192 SCICOMP % 
```

"ls -a" - shows files and folders in the current directory and hidden files

```
alexanderbaranof@192 SCICOMP % ls -a
.		READIND1	READING3	READING5	testfile
..		READING2	READING4	READING6	testfile2
```

### Navigating with the command-line

Exercise: Explain pushd and popd; what data structure represents your directory history? Give an example of using them to organise a folder with music.

Pushd is used to create a stack and save paths to folders there. This results in a folder stack. The popd command extracts the directory from the stack. That is, the last directory added becomes the working directory. This can be useful for organizing a playlist. When one folder runs out of tracks, you can remove it from the stack and move to another folder.

Exercise: Draw a partial tree of your filesystem, starting from the children of your home directory. Include ancestors of your home directory, and siblings of those ancestors. Exclude files, just show directories. Here is mine:

```
(root)/
    |
    | - Applications/
    | - Library/
    | - System/
    | - etc/
    | - Users/
    |     | - Shared
    |     | - alexanderbaranof/
    |     |      | - Applications/
    |     |      | - Desktop/
    |     |      | - Documents/
    |     |      | - Downloads/
    |     |      | - Library/
    |     |      | - Movies/
    |     |      | - Music/
    |     |      | - Pictures/
    |
    | - Volumes/
    | - bin/
    | - cores/
    | - dev/
    | - etc/
    | - home/
    | - opt/
    | - private/
    | - sbin/
    | - tmp/
    | - usr/
    | - var/
```

## Shell scripting

Exercise: Write a shell script that asks the user for their name, and greets them. Sample interaction:

Save script as "greeting" file
```
#!/bin/bash

while [[ $name = "" ]]
do
  echo -n "What's your name?"
  read name
done

echo "Hello, $name"
exit 0
```

Run script 
```
$ bash ./greeting
What's your name?
What's your name? Sasha
Hello, Sasha
```

Exercise: Write a shell script that performs "ROT13" (Caesar cipher with shift 13.) For English, encryption and decryption are the same! (Explain why!) Sample interaction:

```
#!/bin/bash

echo "Hello, I am Sasha" | tr '[A-Z]' '[X-ZA-W]'
```

Encoding and decoding is the same process because the alphabet contains 26 letters

Exercise: Write a shell function that prints "hidden" if the current directory starts with a dot ".", or if any parent starts with a dot. (Files and directories that start with dots are considered "hidden" on many UNIX-like systems.) Sample interaction:


```
#!/bin/bash

PWD=`pwd`
PATTERN='/.'

if [[ $PWD =~ $PATTERN ]]; then
	echo hidden
	exit 0
fi
exit 0
```
```
$ bash ./hidden
$ mkdir .somedir
$ cd ./.somedir
$ bash ../.hidden
hidden
```