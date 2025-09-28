---
layout: page
title: Linux
permalink: /notes/command-library/linux/
---

## Table of Contents

### File System Operations
- [Navigate the file system](#navigate-the-file-system)
- [View and Change the file system](#view-and-change-the-file-system)
- [View the content of text files](#view-the-content-of-text-files)
- [Redirect input and output](#redirect-input-and-output)
- [Symlink](#symlink)
- [Search](#search)

### Text Processing
- [Text info extraction](#text-info-extraction)
  - [`wc`, `uniq`, and `sort`](#wc-uniq-and-sort)
  - [`grep`](#grep)
  - [`sed`](#sed)
  - [`awk`](#awk)

### System Administration
- [File protection with chmod](#file-protection-with-chmod)
- [Access control](#access-control)
- [User & group management](#user--group-management)
- [Check the Linux server performance](#check-the-linux-server-performance)
- [Monitor running processes](#monitor-running-processes)
- [Get available ports on machine](#get-available-ports-on-machine)

### Data Management
- [Synchronize data (from local to remote, from remote to local)](#synchronize-data-from-local-to-remote-from-remote-to-local)
- [Compress / Decompress](#compress--decompress)
- [Scan file system (disk usage)](#scan-file-system-disk-usage)
- [Check the disk usage information on a machine](#check-the-disk-usage-information-on-a-machine)

### Network & Remote Access
- [Access remote server](#access-remote-server)
- [Check host of workstation](#check-host-of-workstation)
- [Look for machine IP recorded in .ssh/config](#look-for-machine-ip-recorded-in-sshconfig)
- [Wake up machines in sleep](#wake-up-machines-in-sleep)

### Automation & Scheduling
- [Crontab](#crontab)
- [monit](#monit)

### Utilities & Tools
- [Check whether the machine has a user's id registered](#check-whether-the-machine-has-a-users-id-registered)
- [Check the modification time of a folder or a file](#check-the-modification-time-of-a-folder-or-a-file)
- [Create title for a Terminal window](#create-title-for-a-terminal-window)
- [Rename files recursively in directory and subdirectories](#rename-files-recursively-in-directory-and-subdirectories)
- [Compare differences under two directories exclusive of certain terms](#compare-differences-under-two-directories-exclusive-of-certain-terms)
- [View the modified dates of listed files in different timezone](#view-the-modified-dates-of-listed-files-in-different-timezone)
- [View the hardware configuration of a machine](#view-the-hardware-configuration-of-a-machine)
- [Convert millionsecond to readable time (with function in bashrc file)](#convert-millionsecond-to-readable-time-with-function-in-bashrc-file)
- [Send email with content from a file](#send-email-with-content-from-a-file)
- [Check if a specific directory exists](#check-if-a-specific-directory-exists)
- [Loop through lines in a text file](#loop-through-lines-in-a-text-file)
- [Generate sequence from 03 to 25](#generate-sequence-from-03-to-25)
- [Run bash file](#run-bash-file)

### Security & Development
- [GPG](#gpg)
- [Search for libraries installed on machine](#search-for-libraries-installed-on-machine)
- [Search for processes which last more than 24 hrs.](#search-for-processes-which-last-more-than-24-hrs)
- [LFTP](#lftp)
- [Create symlink for Hyper on Mac](#create-symlink-for-hyper-on-mac)

### Special Characters & Formatting
- [Delimiter of the binary character in fixlog](#delimiter-of-the-binary-character-in-fixlog)

---

## Navigate the file system

- `pwd` - outputs the name of the current working directory
- `cd` - switches into specified directory
- `cd <Enter>` - redirect to home directory (~)
- `cd -` - redirect to the previous directory
- `mkdir` - creates a new directory in the working directory
- `mkdir -p directory/subdirectory/` - create directories recursively

## View and Change the file system

- `ls` - lists all files and directories of a directory
- `ls -a` - lists all contents of a directory, including hidden files and directories
- `ls -l` - lists all contents in long format
- `ll` - same as `ls - l`
- `ls -t` - orders files and directories by the time they were last modified
- `ls -alt` - use multiple options together
- `ll | grep -v ^l` - list contents of a directory except soft links
- `cp` - copies files
- `mv` - moves and renames files
- `rm` - remove files (`-f`: forcefully remove the file, `-r`: remove the contents of directories recursively, `-i`: verify removal)
- symlink can be removed by `rm -i`.
- `rm -r` - removes directories
- `rm -r /` - remove all directories without touching any file
- `touch` - creates a new file inside the working directory

- Example: Copy the files starting with the letter 'f' from the current working directory to another directory. List the files and directories.
```bash
$ cp f*.txt ../paint/
$ cp file file.bak
$ ls ../paint/
```

- Remove '.bak' from the name of files under the current path
```bash
$ for filename in ./*; do mv "./$filename" "./$(echo "$filename" | sed -e 's/.bak//g')"; done
```

## View the content of text files

- Print all the content of a text file
```bash
$ cat <file-name>
```

- Preview a text file
```bash
$ less <file-name>
```

- Scroll down during searching
	- Press `N`

- View the top / bottom few rows of a file
```
$ head file.txt
$ tail file.txt
$ tail -f file.txt # keeps getting updated
```

## Redirect input and output

- Concepts
	- standard input (stdin): information inputted into the terminal through the keyboard or input device.
	- standard output (stdout): information outputted after a process is run
	- standard error (stderr): error message outputted by a failed process

- `echo` - enter something as standard input
- `>` - redirects standard output of a command to a file, overwriting previous content
- `>>` - redirects standard output of a command to a file, appending new content to old content
- `<`  - redirect standard input to a command
- `|` - serves as a "pipe", which takes the standard output of the command on the left, and pipes it as standard input to the command on the right.

- Example
```bash
$ echo "Hello" > hello.txt
$ cat hello.txt
```

-  Take the output of the command on the left, and redirects it to the file on the right
```bash
$ cat ocean.txt > continents.txt
```

- Take the standard input from the file and inputs it into the program on the left
```bash
$ cat < lakes.txt
```

## Text info extraction

- `wc` - counts the number of lines, words, characters in a text file
- `sort` - sort lines of text alphabetically
- `uniq` - filters duplicate, adjacent lines of text
- `grep` - (global regular expression print) searches for a text pattern and outputs it.
- `sed` - (stream editor) searches for a text pattern, modifies it, and outputs it

### `wc`, `uniq`, and `sort`

- Count number of files under a directory
```bash
$ ls -l | wc -l
```

- Examples
```bash
$ cat volcanoes.txt | wc
$ cat volcanoes.txt | wc | cat > islands.txt
```

- The uniq command removes duplicates only if they are adjacent.
```bash
$ cat lakes.txt | sort > sorted-lakes.txt
$ sort deserts.txt | uniq > uniq-deserts.txt
```

- Remove duplicated entries in a file
```bash
$ sort myfile.txt | uniq > unique.txt
```

### `grep`
- `grep` searches files for lines that match a pattern and returns the results. `-i` triggers case insensitive.
```bash
$ grep Mount mountains.txt
$ grep -r term    # Recursively search subdirectories listed
$ grep -i Mount mountains.txt
$ grep -R Arctic /home/ccuser/workspace/geography
$ grep -Rl Arctic /home/ccuser/workspace/geography
$ grep term file_path > file_name
$ grep term file_path | wc -l    # Count number of appearances
$ grep -a binary_file
```

- e.g. Search for .txt from the output of "ls -l"
```bash
$ ls -l | grep "\.txt$"
```

### `sed`
- sed accepts standard input and modifies it based on an expression, before displaying it as output data. It's similar to "find and replace".

- e.g. Search for the word "snow" in forests.txt and replaces it with "rain". The updated file after replacement will be displayed. Only replace the first instance of "snow" on a line.
```bash
$ sed 's/snow/rain/' forests.txt
```

- `g` means globally. i.e. All instances of "snow" will be replaced.
```bash
$ sed 's/snow/rain/g' forests.txt
```

- Replace string in files recursively
```bash
$ cd /path/to/your/folder
$ sed -i 's/foo/bar/g' *    # will fail when there is folder
$ sed -i 's/home\/trd_oper/local\/disk2/g' $(find . -type f)
$ sed -i 's/export\/scratch/disk1/g' $(find . -type f)
```

- Remove Ctrl-M (^M) character from file
```bash
$ sed -e "s/\r//g" file > newfile
```

- e.g. Pipe the output of a command with another function, `-e` represents edit. The following command replaces 'aeio' with 'u'.
```bash
$ ls -l | sed -e "s/[aeio]/u/g"
```

### `awk`

- Search for field by condition

```bash
$ awk -F ',' '$4 == "8411" {print $1}' /export/scratch/DATA/hk/sima/raw_prc/2019/02/raw_price.20190214
```

```bash
$ awk -F '|' '{print $1,$3-$4+$5}' OFS=' ' eod_20190626 > /export/scratch/trd_oper/cnsod/2019/06/cn_ms_hksc_sod.20190627
```

```bash
$ grep KALU /local/disk2/nomura/us/trade_data/data_prod/*/2019/07/30/eod20190730_*.txt | awk -F ' ' '{sum+=$2} END {print sum}'
```

- Extract last element of a string

```bash
$ echo "/home/data_oper/git/dat_px.ob2/dat_px.4.1.3b/us.report.%Y%m%d.txt" | awk '{n=split($1,A,"/")}; {print A[n]}'
```

- Display unique values of a column in a file
```bash
$ cut -d ' ' -f 4 tar_pos.20190304 | sort | uniq    # -f:column number, start from 1 -d: separator
```

## Access remote server

- e.g. access r15 with the data_oper role
```bash
$ ssh data_oper@r15
```
- `$ exit`: Exit remote server
- access remote server with ssh key
```bash
$ ssh shenghao.wang@g-growth-test-app-demand-c-00 -i ~/.ssh/id_rsa
```

## File protection with chmod

- `chmod +x program_name.sh` - Give execute permission to bash file
- `chmod u+x program_name.sh`
- `chmod 400 file` - To protect a file against accidental overwriting.
- `chmod 500 directory` - To protect yourself from accidentally removing, renaming or moving files from this directory.
- `chmod 600 file` - A private fi le only changeable by the user who entered this command.
- `chmod 644 file` - A publicly readable file that can only be changed by the issuing user.
- `chmod 660 file` - Users belonging to your group can change this file, others don't have any access to it at all.
- `chmod 700 file` - Protects a file against any access from other users, while the issuing user still has full access.
- `chmod 750 directory` - Grant permission to base_role group (PMs)
- `chmod 755 directory` - For files that should be readable and executable by others, but only changeable by the issuing user.
- `chmod 775 file` - Standard file sharing mode for a group.
- `chmod 777 file` - Everybody can do everything to this file.
- `chmod 755 *` - change permission for all sub-directories under current directory
- `chmod 755 */*` - change permission of access to the child directories
- `chmod 644 */*/*` - change permission of access to the files in the child directories
- `chgrp base_role <folder-name>` - Change the access perssion of a particular path

## Synchronize data (from local to remote, from remote to local)

- Examples
```bash
$ rsync -aqz --exclude bak swang:/export/scratch/data/cn/cvbd ./
$ rsync -aqz data_oper@dtlprod4:/disk1/DATA/in/sfd/logs/main.log ./
$ rsync -aqz shenghao.wang@g-growth-test-app-demand-c-00:/home/shenghao.wang/projects/butterscotch/outputs/2023-03-01/02-47-05 ./
```
- Options
	- `q` - quiet (no standard output)
	- `v` - vocal (with standard output)
	- `z` - file gets compressed during syncing
	- `L` - sync the data with symlink
	- `--exclude` - exclude folder from syncing
	- `--no-perms` - without changing permission
	- `--no-owner` - without changing owner
	- `--no-group` - without changing group access

- rsync error: failed to set times on ... Operation not permitted
- Adding `-O / --omit-dir-times` option will avoid it trying to set modification times on directories.

## Symlink

- Create symlink from Path A to Path B
```bash
$ ln -s <actual path> <symbolic path>
$ ln -s dat_insfd.0.0.3 dat_insfd
```

- Scan links in the current directory
```bash
$ find . -type l -ls
$ for l in $(find -type l); do newl=$(readlink -f $l); dir=$(dirname $l); cd $dir; ln -sf $newl; cd -; done;
```

- Remove symlink from Path A to Path B
```bash
$ rm A
```

## Search

- Search for a file or folder under current working directory
```bash
$ find /where/to/look/up criteria action
```

- Search for a file in a specific directory with its file name
```bash
$ find directory -name <file-name>
$ find /dir/path/look/up -name <dir-name-here>
```

- Delete all files with a given name in all subdirectories
```bash
$ find . -name <file-name> -delete
```

## Crontab

- Crontab (CRON TABle) is a file which contains the schedule of cron entries to be run at specified times.
	- `crontab -e`  - Edit crontab file, or create one if it doesn't exist
	- `crontab -l`  - crontab list of cronjobs, display crontab file contents
	- `crontab -r`  - Remove contab file
	- `crontab -v`  - Display the last modification time of the crontab file

- Check the size of files/sub-directories under the current path
```bash
$ du -sh <file-path>
$ md5sum <file-path>
$ du -sh <file-path> | sort -rh | head -n 5
```

## Check the disk usage information on a machine

```bash
$ df -h
```

## Check host of workstation

```bash
$ ping swang-pc.dtl
```

## Check whether the machine has a user's id registered

- e.g. on dtlprod4
```bash
$ id htao
```

## Access control

- Check the access of a directory. "facl" => get file access control list.
```bash
$ getfacl folder
```

- Grant access of a directory to a user
```bash
$ setfacl -m u:userid:x folder    # user can only access the folder
$ setfacl -m u:userid:rx folder    # user can access and list the files in the folder
$ setfacl -m g:base_role:rx folder    # base_role group can access and list the files in the folder
$ setfacl -m user:userid folder    # remove access permission of a user
$ setfacl -m g::r-x folder    # set access for group
$ setfacl -x user:userid folder    # remove access of a user
```
- `u`=> user, `g`=> group, `m` => modify, `x` => access

- Change mask status if directory
```bash
$ umask 022
```

## Compress / Decompress

- Decompress .xz file
```bash
$ xz -d file.xz
```

- Compress a file in .gz format
```bash
$ gzip <file-path>
$ gzip <file-path> <file-path>.gz
$ gzip -k <file-path>    # Keep original file
```

- Unpack compressed file
```bash
$ zless file.gz
$ gzip -d file.gz
$ gunzip file.gz
$ unzip file.zip
$ tar -xvf file.tar
$ tar -xzvf file.tar.gz
$ tar -xjvf file.tar.gz2
```

- Unpack command options
	- `-x`  - Extract a tar ball.
	- `-v`  - Verbose output or show progress while extracting files.
	- `-f`  - Specify an archive or a tarball filename.
	- `-j`  - Decompress and extract the contents of the compressed archive created by bzip2 program (tar.bz2 extension).
	- `-z`  - Decompress and extract the contents of the compressed archive created by gzip program (tar.gz extension).

## Check the modification time of a folder or a file
```bash
$ stat file
```

## Check the Linux server performance

- View CPU, memory usage
	- `$ top`
	- Press `Shift + F`
	- Press direction keys to select the metric, e.g. VIRT
	- Press `s` (Sort) followed by `ESC`
	- Press `c` to view the full command
	- Press `f` to select sort by which metric (CPU, Memory, etc).

- Launch Linux server performance analysis for a particular day
```bash
$ atop -r 20181012 -m
```

- atop options
	- Press `t` to scroll backward timestamps
	- Press `T` to scroll forward timestamps
	- Press `b` to enter a specific timestamp in the format of hh:mm
	- Press `m` to switch to the memory page
	- Press `c` to view the commands

## Create title for a Terminal window

```bash
$ set-title <Window Name>
```


## Rename files recursively in directory and subdirectories

- Test first (Replace 'til' with 'tl')
```bash
$ for f in us/2018/06/til.hist.201806*; do echo ${f/til/tl}; done;
```

- Execute under the parent directory
```bash
$ for f in */*/*/til.hi*; do mv $f ${f/til/tl}; done;
```

## Compare differences under two directories exclusive of certain terms

- To be used when comparing two versions of source code.
```bash
$ diff -r dir1 dir2 | grep -v term1 | grep -v term2
```

## Get available ports on machine

```bash
$ netstat -naputeo | grep tcp | grep LISTEN
```

## Monitor running processes

- Check which process occupies a particular socket
```bash
$ lsof -i: <port-number>
```

- Kill a process

```bash
$ kill -9 <process-id>
$ pkill -f <process-keyword>    # The entire command will be used to match the keyword pattern.

$ for pid in $(ps aux | grep sim | grep Jul | awk '{print $2}'); do kill $pid; done;
```

- Search for running session of a process

```bash
$ ps aux | grep <search-term 1>.*<search-term 2>

# example
$ ps aux | grep xx_worker.py
```


## View the modified dates of listed files in different timezone

- Example
```bash
$ TZ=America/New_York ll -t
```

## Wake up machines in sleep

```bash
$ machines wake -m <machine>    # e.g. machines wake -m r6
```

## View the hardware configuration of a machine

```bash
$ lscpu
```

## User & group management

- Switch user on a machine
```bash
$ su - <user-name>
```

- View all groups and group members on a machine
```bash
$ getent group
$ getent group <group-name>
$ grep <group-name> /etc/group
```

- Create new group
```bash
$ groupadd <group-name>
```

## Convert millionsecond to readable time (with function in bashrc file)

```bash
$ time_readable 57213835
```

## Send email with content from a file

```bash
$ mail -s 'SA import in jhan libs' swang@dytechlab.com < jhan-libs-sa.txt
```

## Check if a specific directory exists

```bash
if [ -d "$DIRECTORY" ]; then
  # Control will enter here if $DIRECTORY exists.
fi
```

## Loop through lines in a text file

```bash
while read p; do
  echo "$p"
done <peptides.txt
```

## Delimiter of the binary character in fixlog
`\x01`

## Look for machine IP recorded in .ssh/config

```bash
$ nslookup <machine-name>
$ nslookup platinum.dtl
```

## Search for processes which last more than 24 hrs.

```bash
$ ps -eo pid,pcpu,pmem,user,args,etime,start_time,cmd --sort=start_time | awk 'substr($0,54,2)>=24'| grep sim
```

## GPG

- gpg encryption/decryption
```bash
$ gpg -e -r <KEY_ID> file    # encryption
```

- Edit trust level
```bash
$ gpg --edit-key <KEY_ID>
gpg> trust
gpg> quit
```

## Search for libraries installed on machine

```bash
$ rpm -qa | grep <search_term>
```

## monit

```bash
$ monit reload    # To reload the configuration file (run under the file path)
$ monit start <process-name>    # Start the new monit process
```

## LFTP

```bash
$ lftp  -e  "set sftp:protocol-version 5"  -u 'dynamftp,password' sftp://sftp.globeop.com
```

## Scan file system (disk usage)

```bash
$ cd <directory-to-scan>; ncdu
$ ncdu -o <file-name>
$ ncdu -f <file-name>
```

## Generate sequence from 03 to 25

```bash
$ for i in $(seq -w 03 25); do echo $i; done
```

## Run bash file

```bash
$ ./path/to/file_name.sh
```

## Create symlink for Hyper on Mac
```bash
$ sudo ln -s "/Applications/Hyper.app/Contents/Resources/bin/hyper" /usr/local/bin/hyper
```
