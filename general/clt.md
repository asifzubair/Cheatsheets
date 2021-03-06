# Command Line Tools #

**awk**

```
awk '$2==4 {print $0}' winters-raleigh-lines.tab > winters-raleigh-lines.4.tab  
awk '$1==4 && $2>2279734 && $2<2333528{print $0}' RAL-100_INDELS.vcf.tab
```

**brew**

`brew doctor` error - `sudo chown -R $USER:admin /usr/local/share` - should set the correct ownership and group for all files and directories below and including `/usr/local/share`

`brew -v install --with-docs --with-python --without-python3 pyqt5`

Install pyqt5 without python3

**chmod**  

**grep**  

```
grep --color = auto <pattern> <filename>
export GREP_OPTIONS='--color=auto'
grep -i break-in auth.log | awk {'print $12'} # case-insensitive search
ping -c l example.com | grep 'bytes from' | cut -d = -f 4
```

**pbs**
```
#PBS -S /bin/bash 
#PBS -o /home/cmb-02/sn1/asifzuba/SOL_CHICKADEE/vcf/allelefrq  
#PBS -e /home/cmb-02/sn1/asifzuba/SOL_CHICKADEE/vcf/allelefrq 
#PBS -l walltime=24:00:00 
#PBS -l nodes=1:ppn=1 
#PBS -l mem=1900MB 
#PBS -q cmb
```

**qsub**

to kill jobs !

```
#!/bin/bash -xv 

export USER=asifzuba 

# to kill all the jobs 
qstat -u $USER | grep "$USER" | cut -d"." -f1 | xargs qdel 

# to kill all the running jobs 
qstat -u $USER | grep "R" | cut -d"." -f1 | xargs qdel 

# to kill all the queued jobs 
qstat -u $USER | grep "Q" | cut -d"." -f1 | xargs qdel 
```

interactive node:

`qsub -I -q cmb -l nodes=1:ppn=24 -l walltime=12:00:00 -l mem=48000mb -l vmem=48000mb -l pmem=2000mb`

**rpm**

```
rpm --initdb --root /home/cmb-02/sn1/asifzuba --dbpath /home/cmb-02/sn1/asifzuba/lib/rpm 
rpm --dbpath /home/cmb-02/sn1/asifzuba/chimera/lib/rpm/ --relocate /usr=/home/cmb-02/sn1/asifzuba/chimera/ --nodeps -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm  
  
CPPFLAGS=-I /usr/local/include -I /tmp-old/backup/usr/include/readline 
LDFLAGS=-L/usr/local/lib -L/home3/fa/faga001/vol/readline-5.1/lib 
  
CFLAGS= -I/tmp-old/backup/usr/include/readline -L/tmp-old/backup/usr/lib64 
  
rpm --dbpath /home/cmb-02/sn1/asifzuba/rpm --relocate /usr=/home/cmb-02/sn1/asifzuba/chimera/ --nodeps -ivh readline-6.0-4.el6.src.rpm
```

**sed**
* `head $filename.csv | sed 's/\$//g' | csvlook | less -S` 
* have white spaces at the end and want to remove trailing `,` 
  * `cat filename | sed 's/,[[:blank:]]*$//g' > tmp.tmp; mv tmp.tmp desired_filename`
* `sed -i '' -e '$ d' $f`  - remove last line - inplace

**ssh**

* `ssh-keygen -R [localhost]:2222` - to remove a particular hostkey from list of known hosts 

**vi**
* For global substitution, use something like this   
 * `:%s/foo/bar/g`  - for all occurrences of foo change to bar 
* go to line: 
 * `G` - go to eof 
 * `A` - go to eol and append 
* If you wanted to go to line 14, you could press `Esc` and then enter `:14` 
* to change behaviour of `tab` and have LINE NUMBERS, put this into your `.vimrc` - it will be in your `$HOME` directory 
 * `set number` 
 * `set tabstop=4 shiftwidth=4 expandtab` 
* to turn on syntax highlighting, do this: 
 * `filetype plugin indent on` 
 * `syntax on`

**wget**

this [SO](http://stackoverflow.com/questions/273743/using-wget-to-recursively-fetch-a-directory-with-arbitrary-files-in-it) gives some clarity on downloading all files from a website.

```
wget $URL
wget -r -np -nH –cut-dirs=3 -R 'index.html*' -A '*_xwalk.csv' http://lehd.ces.census.gov/data/lodes/LODES7

## Pass the --no-parent option, otherwise it will follow the link in the directory index 
## on the site to the parent directory. So the command would look like this:
wget -r --no-parent http://example.com/configs/.vim/

## To avoid downloading the index.html files, use this command:
wget -r --no-parent --reject "index.html*" http://example.com/configs/.vim/

## To avoid downloading the directory structure as well:
wget -r -nH -nd -np -R index.html* http://example.com/configs/.vim/
```

---
**.bashrc recommendation**

Most of the time you don’t want to maintain two separate config files for login and non-login shells — when you set a `PATH`, you want it to apply to both. You can fix this by sourcing `.bashrc` from your `.bash_profile` file, then putting `PATH` and common settings in `.bashrc`. 
 
To do this, add the following lines to `.bash_profile`: 
``` 
if [ -f ~/.bashrc ]; then  
source ~/.bashrc  
fi
```

Now when you login to your machine from a console `.bashrc` will be called.

**redirection**

```
cp -v * ../otherfolder 1> ../success.txt 2> ../error.txt
cp -v * ../otherfolder &> ../log.txt
ls > /dev/null
```
---

`mkdir -p some_dir/dir1 some_dir/dir2 some_dir/dir3`

`$ ps -p $$` // to find your shell particulars 
Or simply `echo $SHELL` 

`uname -a` # Linux version 
`cat /etc/*release` # what flavor of Linux

`gdb example core` // to examine core dump for seg fault etc.  

`setfacl -m u:msalomon:rwx SOL_CHICKADEE` // give particular user a permission

```
# for loop in cshell 
foreach i (`seq 1 5 20`) 
... body … 
end
```


```
Asifs-Mac-mini:~ asifzubair$ tldr nohup
nohup

Allows for a process to live when the terminal gets killed.

- Run process that can live beyond the terminal:
    nohup command options

Asifs-Mac-mini:~ asifzubair$ tldr nice
nice

Execute a program with a custom scheduling priority (niceness).
Niceness values range from -20 (the highest priority) to 19 (the lowest).

- Launch a program with altered priority:
    nice -n niceness_value command

Asifs-Mac-mini:~ asifzubair$ tldr tmux
tmux
Multiplex several virtual consoles.

- Start a new tmux session:
    tmux

- Start a new named tmux session:
    tmux new -s name

- List sessions:
    tmux ls

- Attach to a session:
    tmux a

- Attach to a named session:
    tmux a -t name

- Detach from session:
    ctrl+b d

- Kill session:
    tmux kill-session -t name
```
