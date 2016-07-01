# BBO-Bioinformatics-Bash-Oneliner
Hi bioinformaticans and bash learner, welcome to BBO, Bioinformatics Bash Oneliner learning station. I started studying bioinformatics data three years ago, and I was amazed by those single-word bash commands which are much faster than my dull scripts, so i started bash. Not all the code here is oneliner (if the ';' counts..), but i put effort on making them brief and fast. 

This blog will focus on bash commands for parsing biological data for dummies like me, most of which are tsv files (tab-separated values); some of them are for Ubuntu system maintaining (for dummies). I have been recording the bash commands on my notebook, but putting them on web will help others and myself to query. I apologize that there won't be any citation for the codes, coz i haven't make any record of it, but they are probably from dear Google and Stackoverflow.

English and bash are not my first language, so... correct me anytime, thank you

In case you would like to check up and like my stupid questions on Stackoverflow, here's my page:
http://stackoverflow.com/users/4290753/once

If you want to check out stylish BBO:
http://bbonut.blogspot.tw


##Handy Bash oneliner commands for tsv file editing

- [Grep](#grep)
- [Sed](#sed)
- [Awk](#awk)
- [Xargs](#xargs)
- [Find](#find)
- [Loops](#loops)
- [Download](#download)
- [Random](#random)
- [Others](#others)
- [System](#system)

##Grep
#####extract text bewteen words (e.g. w1,w2)
    
```bash
grep -o -P '(?<=w1).*(?=w2)'
```

#####grep lines without word (e.g. bbo)
     
```bash
grep -v bbo
```

#####grep and count (e.g. bbo)
    
```bash
grep -c bbo filename
```

#####insensitive grep (e.g. bbo/BBO/Bbo)
    
```bash
grep -i "bbo" filename 
```

#####count occurrence (e.g. three times a line count three times)
    
```bash
grep -o bbo filename 
```

#####COLOR the match (e.g. bbo)!
    
```bash
grep --color bbo filename 
```

#####grep search all files in a directory(e.g. bbo)
    
```bash
grep -R bbo /path/to/directory 
```

or
    
```bash
grep -r bbo /path/to/directory 
```
#####search all files in directory, only output file names with matches(e.g. bbo)
    
```bash
grep -Rh bbo /path/to/directory 
```
or
```bash    
grep -rh bbo /path/to/directory 
```

#####grep OR (e.g. A or B or C or D)
    
```
grep 'A\|B\|C\|D' 
```

#####grep AND (e.g. A and B)
    
```bash
grep 'A.*B' 
```

#####grep all content of a fileA from fileB
    
```bash
grep -f fileA fileB 
```

#####grep a tab
    
```bash
grep $'\t' 
```

##Sed
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]

#####remove lines with word (e.g. bbo)
    
```bash
sed "/bbo/d" filename
```

#####edit infile (edit and save)
    
```bash
sed -i "/bbo/d" filename
```
#####when using variable (e.g. $i), use double quotes " "
e.g. add >$i to the first line (to make a FASTA file)
    
```bash
sed "1i >$i"  
```
//notice the double quotes! in other examples, you can use a single quote, but here, no way! 
//'1i' means insert to first line


#####delete empty lines
    
```bash
sed '/^\s*$/d' 
```    
or
   
```bash
sed 's/^$/d' 
```
#####delete last line
   
```bash
sed '$d' 
```

#####add \n every nth character (e.g. every 4th character)
    
```bash
sed 's/.\{4\}/&\n/g' 
```

#####substitution (e.g. replace A by B)
    
```bash
sed 's/A/B/g' filename 
```
#####select lines start with string (e.g. bbo)
    
```bash
sed -n '/^@S/p' 
```
#####delete lines with string (e.g. bbo)
    
```bash
sed '/bbo/d' filename 
```
#####print every nth lines
    
```bash
sed -n '0~3p' filename
```
//catch 0: start; 3: step


#####print every odd # lines
    
```bash
sed -n '1~2p' 
```
#####print every third line including the first line
    
```bash
sed -n '1p;0~3p' 
```
#####remove leading whitespace and tabs
    
```bash
sed -e 's/^[ \t]*//'
```
//notice a whitespace before '\t'!!


#####remove only leading whitespace
    
```bash
sed 's/ *//'
```
//notice a whitespace before '*'!!


#####remove ending commas
    
```bash
sed 's/,$//g' 
```
#####add a column to the end
    
```bash
sed "s/$/\t$i/"
```
//$i is the valuable you want to add
e.g. add the filename to every last column of the file
    
```bash
for i in $(ls);do sed -i "s/$/\t$i/" $i;done
```

#####remove newline\ nextline
    
```bash
sed ':a;N;$!ba;s/\n//g'
```

#####print a number of lines (e.g. line 10th to line 33 rd)
    
```bash
sed -n '10,33p' <filename
```


#Awk
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]

#####set tab as field separator
    
```bash
awk -F $'\t'  
```

#####output as tab separated (also as field separator)
   
```bash
awk -v OFS='\t' 
```

#####pass variable

```bash
a=bbo;b=obb;
awk -v a="$a" -v b="$b" "$1==a && $10=b' filename 
```

#####print number of characters on each line
    
```bash
awk '{print length ($0);}' filename 
```

#####find number of columns
  
```bash
awk '{print NF}' 
```

#####reverse column order
    
```bash
awk '{print $2, $1}' 
```

#####check if there is a comma in a column (e.g. column $1)
    
```bash
awk '$1~/,/ {print}'  
```

#####split and do for loop
    
```bash
awk '{split($2, a,",");for (i in a) print $1"\t"a[i]} filename 
```

#####print all lines before nth occurence of a string (e.g stop print lines when bbo appears 7 times)
    
```bash
awk -v N=7 '{print}/bbo/&& --N<=0 {exit}'
```

#####add string to the beginning of a column (e.g add "chr" to column $3)
    
```bash
awk 'BEGIN{OFS="\t"}$3="chr"$3' 
```

#####remove lines with string (e.g. bbo)
    
```bash
awk '!/bbo/' file 
```

#####column subtraction
    
```bash
cat file| awk -F '\t' 'BEGIN {SUM=0}{SUM+=$3-$2}END{print SUM}'
```

#####usage and meaning of NR and FNR
e.g.
fileA:
a
b
c
fileB:
d
e
    
```bash
awk 'print FILENAME, NR,FNR,$0}' fileA fileB 
```

fileA    1    1    a
fileA    2    2    b
fileA    3    3    c
fileB    4    1    d
fileB    5    2    e

#####and gate

e.g.
fileA:
1    0

2    1

3    1

4    0

fileB:

1    0

2    1

3    0

4    1
    
```bash
awk -v OFS='\t' 'NR=FNR{a[$1]=$2;next} NF {print $1,((a[$1]=$2)? $2:"0")}' fileA fileB 
```

1    0

2    1

3    0

4    0

#####round all numbers of file (e.g. 2 significant figure)
    
```bash
awk '{while (match($0, /[0-9]+\[0-9]+/)){
    \printf "%s%.2f", substr($0,0,RSTART-1),substr($0,RSTART,RLENGTH)
    \$0=substr($0, RSTART+RLENGTH)
    \}
    \print
    \}'
```

#####give number/index to every row
    
```bash
awk '{printf("%s\t%s\n",NR,$0)}'
```

##Xargs
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]

set tab as delimiter (default:space)

```bash
xargs -d\t
```

#####display 3 items per line

```bash
echo 1 2 3 4 5 6| xargs -n 3
```

//1 2 3
  4 5 6


#####prompt before execution

```bash
echo a b c |xargs -p -n 3
```

#####print command along with output

```bash
xargs -t abcd
```

///bin/echo abcd
//abcd


#####with find and rm

```bash
find . -name "*.html"|xargs rm -rf
```

delete fiels with whitespace in filename (e.g. "hello 2001")

```bash
find . -name "*.c" -print0|xargs -0 rm -rf
```

#####show limits

```bash
xargs --show-limits
```

#####move files to folder

```bash
find . -name "*.bak" -print 0|xargs -0 -I {} mv {} ~/old
```

or

```bash
find . -name "*.bak" -print 0|xargs -0 -I file mv file ~/old
```

#####move first 100th files to a directory (e.g. d1)

```bash
ls |head -100|xargs -I {} mv {} d1
```

#####parallel

```bash
time echo {1..5} |xargs -n 1 -P 5 sleep
```
a lot faster than
```bash
time echo {1..5} |xargs -n1 sleep
```

#####copy all files from A to B

```bash
find /dir/to/A -type f -name "*.py" -print 0| xargs -0 -r -I file cp -v -p file --target-directory=/path/to/B
```

//v: verbose|
//p: keep detail (e.g. owner)


#####with sed

```bash
ls |xargs -n1 -I file sed -i '/^Pos/d' filename
```

#####add the file name to the first line of file

```bash
ls |sed 's/.txt//g'|xargs -n1 -I file sed -i -e '1 i\>file\' file.txt
```

#####count all files

```bash
ls |xargs -n1 wc -l
```

#####to filter txt to a single line

```bash
ls -l| xargs
```

#####count files within directories

```bash
echo mso{1..8}|xargs -n1 bash -c 'echo -n "$1:"; ls -la "$1"| grep -w 74 |wc -l' --
```
// "--" signals the end of options and display further option processing


#####download dependencies files and install (e.g. requirements.txt)
 
```bash
cat requirements.txt| xargs -n1 sudo pip install
```

#####count lines in all file, also count total lines

```bash
ls|xargs wc -l
```



##Find 
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
#####list all sub directory/file in the current directory
    
```bash
find .
```

#####list all files under the current directory
    
```bash
find . -type f
```

#####list all directories under the current directory
    
```bash
find . -type d
```

#####edit all files under current directory (e.g. replace 'www' with 'ww')
    
```bash
find . name '*.php' -exec sed -i 's/www/w/g' {} \;
```
if no subdirectory
    
```bash
replace "www" "w" -- *
```
//a space before *


#####find and output only filename (e.g. "mso")
    
```bash
find mso*/ -name M* -printf "%f\n"
```

#####find and delete file with size less than (e.g. 74 byte)
    
```bash
find . -name "*.mso" -size -74c -delete
```
//M for MB, etc


##Loops
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
#####while loop, column subtraction of a file (e.g. a 3 columns file)
    
```bash
while read a b c; do echo $(($c-$b));done < <(head filename)
```
//there is a space between the two '<'s

#####while loop, sum up column subtraction
    
```bash
i=0; while read a b c; do ((i+=$c-$b)); echo $i; done < <(head filename)
```

#####if loop
    
```bash
if (($j==$u+2))
```
//(( )) use for arithmetic operation
    
```bash
if [[$age >21]]
```
//[[ ]] use for comparison

#####for loop
    
```bash
for i in $(ls); do echo file $i;done
```


##Download
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
#####download all from a page
    
```bash
wget -r -l1 -H -t1 -nd -N -np -A mp3 -e robots=off http://example.com
```
//-r: recursive and download all links on page

//-l1: only one level link

//-H: span host, visit other hosts

//-t1: numbers of retries

//-nd: don't make new directories, download to here

//-N: turn on timestamp

//-nd: no parent

//-A: type (seperate by ,)

//-e robots=off: ignore the robots.txt file which stop wget from crashing the site, sorry example.com



##Random
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
#####random pick 100 lines from a file
    
```bash
shuf -n 100 filename
```

#####random order (lucky draw)
    
```bash
for i in a b c d e; do echo $i; done| shuf
```

#####echo series of random numbers between a range (e.g. generate 15 random numbers from 0-10)
    
```bash
shuf -i 0-10 -n 15
```

#####echo a random number
    
```bash
echo $RANDOM
```

#####random from 0-9
    
```bash
echo $((RANDOM % 10))
```

#####random from 1-10
    
```bash
echo $(((RANDOM %10)+1))
```



##Others
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
#####remove newline / nextline
    
```bash
tr --delete '\n' <input.txt >output.txt
```

#####replace newline
     
```bash
tr '\n' ' ' <filename
```

#####compare files (e.g. fileA, fileB)
    
```bash
diff fileA fileB
```
//a: added; d:delete; c:changed

or

```bash
sdiff fileA fileB
```
//side-to-side merge of file differences


#####number a file (e.g. fileA)

```bash
nl fileA
```
or

```bash
nl -nrz fileA
```
//add leading zeros


#####combine/ paste two files (e.g. fileA, fileB)
    
```bash
paste fileA fileB
```
//default tab seperated


#####reverse string
    
```bash
echo 12345| rev
```

#####read .gz file without extracting
    
```bash
zmore filename
```
or
    
```bash
zless filename
```

#####run in background, output error file
    
```bash
(command here) 2>log &
```

or

```bash
(command here) 2>&1| tee logfile
```

or

```bash
(command here) 2>&1 >>outfile
```
//0: standard input; 1: standard output; 2: standard error


#####send mail
    
```bash
echo 'heres the content'| mail -A 'file.txt' -s 'mail.subject' me@gmail.com
```
//use -a flag to set send from (-a "From: some@mail.tld")


#####.xls to csv
    
```bash
xls2csv filename
```
#####append to file (e.g. hihi)
    
```bash
echo 'hihi' >>filename
```

#####make BEEP sound
    
```bash
speaker-test -t sine -f 1000 -l1
```

#####set beep duration
    
```bash
(speaker-test -t sine -f 1000) & pid=$!;sleep 0.1s;kill -9 $pid
```

#####history edit/ delete
    
```bash
~/.bash_history
```
or

```bash
history -d [line_number]
```

#####get last history/record filename
    
```bash
head !$
```

#####clean screen
    
```bash
clear
```

or

```bash
Ctrl+l
```

#####send data to last edited file
    
```bash
cat /directory/to/file
echo 100>!$
```

#####run history number (e.g. 53)
    
```bash
!53
```

#####run last command
    
```bash
!!
```

#####run last command that began with (e.g. cat filename)
    
```bash
!cat
```

or

```bash
!c
```
//run cat filename again


#####extract .xf
    
    1.unxz filename.tar.xz
    2.tar -xf filename.tar

#####install python package
    
```bash
pip install packagename
```


#####Download file if necessary
    
```bash
data=file.txt
url=http://www.example.com/$data
if [! -s $data];then
    echo "downloading test data..."
    wget $url
fi
```

#####wget to a filename (when a long name)
    
```bash
wget -O filename "http://example.com"
```

#####wget files to a folder

```bash
wget -P /path/to/directory "http://example.com"
```

#####delete current bash command
    
```bash
Ctrl+U
```

or

```bash
Ctrl+C
```

or

```bash
Alt+Shift+#
```
//to make it to history


#####add things to history (e.g. "addmetohistory")
    
```bash
#addmetodistory
```
//just add a "#" before~~


#####sleep awhile or wait for a moment or schedule a job
    
```bash
sleep 5;echo hi
```

#####count the time for executing a command
    
```bash
time echo hi
```

#####backup with rsync
    
```bash
rsync -av filename filename.bak
rsync -av directory directory.bak
rsync -av --ignore_existing directory/ directory.bak
rsync -av --update directory directory.bak
```
//skip files that are newer on receiver (i prefer this one!)


#####make all directories at one time!
    
```bash
mkdir -p project/{lib/ext,bin,src,doc/{html,info,pdf},demo/stat}
```
//-p: make parent directory
//this will create project/doc/html/; project/doc/info; project/lib/ext ,etc


#####run command only if another command returns zero exit status (well done)
    
```bash
cd tmp/ && tar xvf ~/a.tar
```

#####run command only if another command returns non-zero exit status (not finish)
    
```bash
cd tmp/a/b/c ||mkdir -p tmp/a/b/c
```

#####extract to a path
    
```bash
tar xvf -C /path/to/directory filename.gz
```

#####use backslash "\" to break long command
    
```bash
cd tmp/a/b/c \
> || \
>mkdir -p tmp/a/b/c
```

#####get pwd
    
```bash
VAR=$PWD; cd ~; tar xvf -C $VAR file.tar
```
//PWD need to be capital letter

#####list file type of file (e.g. /tmp/)
    
```bash
file /tmp/
```
//tmp/: directory


#####bash script
    
```bash
#!/bin/bash
file=${1#*.}
```
//remove string before a "."

```bash
file=${1%.*}
```
//remove string after a "."

#####search from history
    
```bash
Ctrl+r
```

#####python simple HTTP Server
    
```bash
python -m SimpleHTTPServer
```

#####variables
    
```bash
{i/a/,}
```
e.g. replace all
```bash
{i//a/,}
```
//for variable i, replace all 'a' with a comma

#####read user input
    
```bash
read input
echo $input
```

#####generate sequence 1-10
    
```bash
seq 10
```

#####sum up input list (e.g. seq 10)
    
```bash
seq 10|paste -sd+|bc
```

#####find average of input list/file
    
```bash
i=`wc -l filename|cut -d ' ' -f1`; cat filename| echo "scale=2;(`paste -sd+`)/"$i|bc
```

#####generate all combination (e.g. 1,2)
    
```bash
echo {1,2}{1,2}
```
//1 1, 1 2, 2 1, 2 2

#####generate all combination (e.g. A,T,C,G)
    
```bash
set = {A,T,C,G}
group= 5
for ((i=0; i<$group; i++));do
    repetition=$set$repetition;done
    bash -c "echo "$repetition""
```

#####read file content to variable
```bash
foo=$(<test1)
```

#####echo size of variable

```bash
echo ${#foo}
```

#####array
```bash
declare -A array=()
```

#####send a directory

```bash
scp -r directoryname user@ip:/path/to/send
```




##System
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]

#####snapshot of the current processes

```bash
ps 
```

#####check graphics card

```bash
lspci
```

#####show IP address
    
```bash
$ip add show
```
or
    
```bash
ifconfig
```

#####check system version
    
```bash
cat /etc/*-release
```

#####Linux Programmer's Manuel: hier- description of the filesystem hierarchy
    
```bash
man hier
```

#####list job
    
```bash
jobs -l
```

#####export PATH
    
```bash
export PATH=$PATH:~/path/you/want
```

#####make file execuable
    
```bash
chmod +x filename
```
//you can now ./filename to execute it

#####list screen
    
```bash
screen -d -r
```

#####echo screen name
    
```bash
screen -ls
```

#####check system (x86-64)
    
```bash
uname -i
```

#####surf the net

```bash
links www.google.com
```

#####add user, set passwd
    
```bash
useradd username
passwd username
```

#####edit variable for bash, (e.g. displaying the whole path)
    
```bash
1. joe ~/.bash_profile 
2. export PS1='\u@\h:\w\$' 
```
//$PS1 is a variable that defines the makeup and style of the command prompt 
```bash
3. source ~/.bash_profile
```

#####edit environment setting (e.g. alias)
    
```bash
1. joe ~/.bash_profile
2. alias pd="pwd" //no more need to type that 'w'!
3. source ~/.bash_profile
```

#####list environment variables (e.g. PATH)
    
```bash
$echo $PATH
```
//list of directories separated by a colon

#####list all environment variables for current user
    
```bash
$env
```

#####show partition format
    
```bash
lsblk
```

#####soft link program to bin
    
```bash
ln -s /path/to/program /home/usr/bin
```
//must be the whole path to the program

#####show hexadecimal view of data
    
```bash
hexdump -C filename.class
```

#####jump to different node
    
```bash
rsh node_name
```

#####check port (active internet connection)
    
```bash
netstat -tulpn
```

#####find whick link to a file
    
```bash
readlink filename
```

#####check where a command link to (e.g. python)
    
```bash
which python
```

#####list total size of a directory
    
```bash
du -hs .
```
or
    
```bash
du -sb
```

#####copy directory with permission setting
    
```bash
cp -rp /path/to/directory
```

#####store current directory
    
```bash
pushd . $popd ;dirs -l 
```

#####show disk usage
    
```bash
df -h 
```
or
   
```bash
du -h 
```
or
    
```bash
du -sk /var/log/* |sort -rn |head -10
```

#####show current runlevel
    
```bash
runlevel
```

#####switch runlevel
    
```bash
init 3 
```
or
```bash
telinit 3 
```
#####permanently modify runlevel
    
```bash
1. edit /etc/init/rc-sysinit.conf 
2. env DEFAULT_RUNLEVEL=2 
```

#####become root
    
```bash
su
```

#####become somebody
    
```bash
su somebody
```

#####report user quotes on device
    
```bash
requota -auvs
```

#####get entries in a number of important databases
    
```bash
getent database_name
```
(e.g. the 'passwd' database)
    
```bash
getent passwd
```
//list all user account (all local and LDAP)
(e.g. fetch list of grop accounts)
    
```bash
getent group
```
//store in database 'group'

#####little xwindow tools
    
```bash
xclock
xeyes
```

#####change owner of file
    
```bash
chown user_name filename
chown -R user_name /path/to/directory/
```
//chown user:group filename

#####list current mount detail
    
```bash
df
```

#####list current usernames and user-numbers
    
```bash
cat /etc/passwd
```
#####get all username
    
```bash
getent passwd| awk '{FS="[:]"; print $1}'
```

#####show all users
    
```bash
compgen -u
```

#####show all groups
    
```bash
compgen -g
```

#####show group of user
    
```bash
group username
```

#####show uid, gid, group of user
    
```bash
id username
```

#####check if it's root
    
```bash
if [$(id -u) -ne 0];then
    echo "You are not root!"
    exit;
fi
```
//'id -u' output 0 if it's not root

#####find out CPU information
    
```bash
more /proc/cpuinfo
```
or
    
```bash
lscpu
```

#####set quota for user (e.g. disk soft limit: 120586240; hard limit: 125829120)
    
```bash
setquota username 120586240 125829120 0 0 /home
```

#####show quota for user
    
```bash
quota -v username
```

#####fork bomb
    
```bash
:(){:|:&};:
```
//dont try this at home

#####check user login
    
```bash
lastlog
```

#####edit path for all users
    
```bash
joe /etc/environment
```
//edit this file

#####show running processes
    
```bash
ps aux
```

#####find maximum number of processes
    
```bash
cat /proc/sys/kernal/pid_max
```

#####show and set user limit
    
```bash
ulimit -u
```


=-=-=-=-=-A lot more coming!! =-=-=-=-=-=-=-=-=-=waitwait-=-=-=-=-=-=-=-=-=-
