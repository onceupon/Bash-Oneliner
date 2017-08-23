# Bash-Oneliner
Hi bash learners and bioinformaticans, welcome to Bash Oneliner. I started studying bioinformatics data three years ago, and was amazed by those single-word bash commands which are much faster than my dull scripts, so i started bash. Not all the code here is oneliner (if the ';' counts..), but i put effort on making them brief and fast. 

This blog will focus on simple bash commands for parsing biological data, most of which are for tsv files (tab-separated values); some of them are for Ubuntu system maintaining. I have been recording the bash commands on my notebook, but putting them on web will help others and myself to query. I apologize that there won't be any citation for the codes, but they are probably from dear Google and Stackoverflow.

English and bash are not my first language, so... correct me anytime, thank you

In case you would like to check and vote up my questions on Stackoverflow, here's my page:
http://stackoverflow.com/users/4290753/once

Here's a more stylish version~
http://onceupon.github.io/Bash-Oneliner/

## Handy Bash oneliner commands for tsv file editing

- [Grep](#grep)
- [Sed](#sed)
- [Awk](#awk)
- [Xargs](#xargs)
- [Find](#find)
- [Loops](#loops)
- [Download](#download)
- [Random](#random)
- [Xwindow](#xwindow)
- [Others](#others)
- [System](#system)

## Grep
#####  Extract text bewteen words (e.g. w1,w2)
    
```bash
grep -o -P '(?<=w1).*(?=w2)'
```

##### Grep lines without word (e.g. bbo)
     
```bash
grep -v bbo filename
```

##### Grep only one/first match (e.g. bbo)

```bash
grep -m 1 bbo filename
```

##### Grep and count (e.g. bbo)
    
```bash
grep -c bbo filename
```

##### Insensitive grep (e.g. bbo/BBO/Bbo)
    
```bash
grep -i "bbo" filename 
```

##### Count occurrence (e.g. three times a line count three times)
    
```bash
grep -o bbo filename 
```

##### COLOR the match (e.g. bbo)!
    
```bash
grep --color bbo filename 
```

##### Grep search all files in a directory(e.g. bbo)
    
```bash
grep -R bbo /path/to/directory 
```

or
    
```bash
grep -r bbo /path/to/directory 
```
##### Search all files in directory, only output file names with matches(e.g. bbo)
    
```bash
grep -Rh bbo /path/to/directory 
```
or
```bash    
grep -rh bbo /path/to/directory 
```

##### Grep OR (e.g. A or B or C or D)
    
```
grep 'A\|B\|C\|D' 
```

##### Grep AND (e.g. A and B)
    
```bash
grep 'A.*B' 
```

##### Grep all content of a fileA from fileB
    
```bash
grep -f fileA fileB 
```

##### Grep a tab
    
```bash
grep $'\t' 
```

##### Grep variable from variable
```bash
$echo "$long_str"|grep -q "$short_str"
if [ $? -eq 0 ]; then echo 'found'; fi
```
//grep -q will output 0 if match found  
//remember to add space between []!

##### Grep strings between a bracket()
```bash
grep -oP '\(\K[^\)]+'
```

##### Grep number of characters with known strings in between(e.g. AAEL000001-RA)
```bash
grep -o -w "\w\{10\}\-R\w\{1\}"
```  
// \w word character [0-9a-zA-Z_] \W not word character 


##### A lot examples here
http://www.cyberciti.biz/faq/grep-regular-expressions/



## Sed
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]

##### Remove lines with word (e.g. bbo)
    
```bash
sed "/bbo/d" filename
```

##### Edit infile (edit and save)
    
```bash
sed -i "/bbo/d" filename
```
##### When using variable (e.g. $i), use double quotes " "
e.g. add >$i to the first line (to make a FASTA file)  
    
```bash
sed "1i >$i"  
```
//notice the double quotes! in other examples, you can use a single quote, but here, no way!   
//'1i' means insert to first line


##### Delete empty lines
    
```bash
sed '/^\s*$/d' 
```    
or
   
```bash
sed 's/^$/d' 
```
##### Delete last line
   
```bash
sed '$d' 
```

##### Delete last character from end of file
```bash
sed -i '$ s/.$//' filename
```

##### Add string to end of file (e.g. "]")

```bash
sed '$s/$/]/' filename
```
##### Add newline to the end

```bash
sed '$a\'
```

##### Add string to beginning of every line (e.g. bbo)

```bash
sed -e 's/^/bbo/' file
```

##### Add string to end of each line (e.g. "}")
```bash
sed -e 's/$/\}\]/' filename
```

##### Add \n every nth character (e.g. every 4th character)
    
```bash
sed 's/.\{4\}/&\n/g' 
```

##### Concatenate/combine/join files with a seperator and next line (e.g seperate by ",")

```bash
sed -s '$a,' *.json > all.json
```

##### Substitution (e.g. replace A by B)
    
```bash
sed 's/A/B/g' filename 
```
##### Select lines start with string (e.g. bbo)
    
```bash
sed -n '/^@S/p' 
```
##### Delete lines with string (e.g. bbo)
    
```bash
sed '/bbo/d' filename 
```
##### Print every nth lines
    
```bash
sed -n '0~3p' filename
```
//catch 0: start; 3: step


##### Print every odd # lines
    
```bash
sed -n '1~2p' 
```
##### Print every third line including the first line
    
```bash
sed -n '1p;0~3p' 
```
##### Remove leading whitespace and tabs
    
```bash
sed -e 's/^[ \t]*//'
```
//notice a whitespace before '\t'!!


##### Remove only leading whitespace
    
```bash
sed 's/ *//'
```
//notice a whitespace before '*'!!


##### Remove ending commas
    
```bash
sed 's/,$//g' 
```
##### Add a column to the end
    
```bash
sed "s/$/\t$i/"
```
//$i is the valuable you want to add  
e.g. add the filename to every last column of the file  
    
```bash
for i in $(ls);do sed -i "s/$/\t$i/" $i;done
```
##### Add extension of filename to last column

```bash
for i in T000086_1.02.n T000086_1.02.p;do sed "s/$/\t${i/*./}/" $i;done >T000086_1.02.np
```

##### Remove newline\ nextline
    
```bash
sed ':a;N;$!ba;s/\n//g'
```

##### Print a number of lines (e.g. line 10th to line 33 rd)
    
```bash
sed -n '10,33p' <filename
```

##### Change delimiter 
```bash
sed 's=/=\\/=g'
```

##### Replace with wildcard (e.g A-1-e or A-2-e or A-3-e....)
```bash
sed 's/A-.*-e//g' filename
```
##### Remove last character of file
```bash``
sed '$ s/.$//'
```

##### Insert character at specified position of file (e.g. AAAAAA --> AAA#AAA)
```bash``
sed -r -e 's/^.{3}/&#/' file
```


## Awk
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]

##### Set tab as field separator
    
```bash
awk -F $'\t'  
```

##### Output as tab separated (also as field separator)
   
```bash
awk -v OFS='\t' 
```

##### Pass variable

```bash
a=bbo;b=obb;
awk -v a="$a" -v b="$b" "$1==a && $10=b' filename 
```

##### Print line number and number of characters on each line
    
```bash
awk '{print NR,length($0);}' filename 
```

##### Find number of columns
  
```bash
awk '{print NF}' 
```

##### Reverse column order
    
```bash
awk '{print $2, $1}' 
```

##### Check if there is a comma in a column (e.g. column $1)
    
```bash
awk '$1~/,/ {print}'  
```

##### Split and do for loop
    
```bash
awk '{split($2, a,",");for (i in a) print $1"\t"a[i]} filename 
```

##### Print all lines before nth occurence of a string (e.g stop print lines when bbo appears 7 times)
    
```bash
awk -v N=7 '{print}/bbo/&& --N<=0 {exit}'
```

##### Print filename and last line of all files in directory
```bash
ls|xargs -n1 -I file awk '{s=$0};END{print FILENAME,s}' file'
```

##### Add string to the beginning of a column (e.g add "chr" to column $3)
    
```bash
awk 'BEGIN{OFS="\t"}$3="chr"$3' 
```

##### Remove lines with string (e.g. bbo)
    
```bash
awk '!/bbo/' file 
```

##### Column subtraction
    
```bash
cat file| awk -F '\t' 'BEGIN {SUM=0}{SUM+=$3-$2}END{print SUM}'
```

##### Usage and meaning of NR and FNR
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

##### AND gate

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

##### Round all numbers of file (e.g. 2 significant figure)
    
```bash
awk '{while (match($0, /[0-9]+\[0-9]+/)){
    \printf "%s%.2f", substr($0,0,RSTART-1),substr($0,RSTART,RLENGTH)
    \$0=substr($0, RSTART+RLENGTH)
    \}
    \print
    \}'
```

##### Give number/index to every row
    
```bash
awk '{printf("%s\t%s\n",NR,$0)}'
```
##### Break combine column data into rows

e.g.  
seperate  

David    cat,dog  
into  
David    cat  
David    dog  

detail here:　http://stackoverflow.com/questions/33408762/bash-turning-single-comma-separated-column-into-multi-line-string
```bash
awk '{split($2,a,",");for(i in a)print $1"\t"a[i]}' file
```

##### Sum up a file (each line in file contains only one number)

```bash
awk '{s+=$1} END {print s}' filename
```

##### Average a file (each line in file contains only one number)
```bash
awk '{s+=$1}END{print s/NR}'
```

##### Print field start with string (e.g Linux)

```bash
awk '$1 ~ /^Linux/'
```

##### Sort a row (e.g. 1 40  35  12  23  --> 1 12    23  35  40)

```bash
awk ' {split( $0, a, "\t" ); asort( a ); for( i = 1; i <= length(a); i++ ) printf( "%s\t", a[i] ); printf( "\n" ); }'
```

##### Subtract previous row values (add column6 which equal to column4 minus last column5) 
```bash
awk '{$6 = $4 - prev5; prev5 = $5; print;}'
```



## Xargs
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]

##### Set tab as delimiter (default:space)

```bash
xargs -d\t
```

##### Display 3 items per line

```bash
echo 1 2 3 4 5 6| xargs -n 3
```

//1 2 3  
  4 5 6


##### Prompt before execution

```bash
echo a b c |xargs -p -n 3
```

##### Print command along with output

```bash
xargs -t abcd
```

///bin/echo abcd  
//abcd


##### With find and rm

```bash
find . -name "*.html"|xargs rm -rf
```

##### Delete fiels with whitespace in filename (e.g. "hello 2001")

```bash
find . -name "*.c" -print0|xargs -0 rm -rf
```

##### Show limits

```bash
xargs --show-limits
```

##### Move files to folder

```bash
find . -name "*.bak" -print 0|xargs -0 -I {} mv {} ~/old
```

or

```bash
find . -name "*.bak" -print 0|xargs -0 -I file mv file ~/old
```

##### Move first 100th files to a directory (e.g. d1)

```bash
ls |head -100|xargs -I {} mv {} d1
```

##### Parallel

```bash
time echo {1..5} |xargs -n 1 -P 5 sleep
```
a lot faster than
```bash
time echo {1..5} |xargs -n1 sleep
```

##### Copy all files from A to B

```bash
find /dir/to/A -type f -name "*.py" -print 0| xargs -0 -r -I file cp -v -p file --target-directory=/path/to/B
```

//v: verbose|  
//p: keep detail (e.g. owner)


##### With sed

```bash
ls |xargs -n1 -I file sed -i '/^Pos/d' filename
```

##### Add the file name to the first line of file

```bash
ls |sed 's/.txt//g'|xargs -n1 -I file sed -i -e '1 i\>file\' file.txt
```

##### Count all files

```bash
ls |xargs -n1 wc -l
```

##### Turn output into a single line

```bash
ls -l| xargs
```

##### Count files within directories

```bash
echo mso{1..8}|xargs -n1 bash -c 'echo -n "$1:"; ls -la "$1"| grep -w 74 |wc -l' --
```
// "--" signals the end of options and display further option processing


##### Download dependencies files and install (e.g. requirements.txt)
 
```bash
cat requirements.txt| xargs -n1 sudo pip install
```

##### Count lines in all file, also count total lines

```bash
ls|xargs wc -l
```
##### Xargs and grep

```bash
cat grep_list |xargs -I{} grep {} filename
```

## Find 
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
##### List all sub directory/file in the current directory
    
```bash
find .
```

##### List all files under the current directory
    
```bash
find . -type f
```

##### List all directories under the current directory
    
```bash
find . -type d
```

##### Edit all files under current directory (e.g. replace 'www' with 'ww')
    
```bash
find . name '*.php' -exec sed -i 's/www/w/g' {} \;
```
if no subdirectory
    
```bash
replace "www" "w" -- *
```
//a space before *


##### Find and output only filename (e.g. "mso")
    
```bash
find mso*/ -name M* -printf "%f\n"
```

##### Find and delete file with size less than (e.g. 74 byte)
    
```bash
find . -name "*.mso" -size -74c -delete
```
//M for MB, etc


## Loops
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
##### While loop, column subtraction of a file (e.g. a 3 columns file)
    
```bash
while read a b c; do echo $(($c-$b));done < <(head filename)
```
//there is a space between the two '<'s

##### While loop, sum up column subtraction
    
```bash
i=0; while read a b c; do ((i+=$c-$b)); echo $i; done < <(head filename)
```

##### If loop
    
```bash
if (($j==$u+2))
```
//(( )) use for arithmetic operation
    
```bash
if [[$age >21]]
```
//[[ ]] use for comparison


##### Test if file exist
```bash
if [ -e 'filename' ]
then
  echo -e "file exists!"
fi
```


##### For loop
    
```bash
for i in $(ls); do echo file $i;done
```


## Download
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
##### Download all from a page
    
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

##### Upload a file to web and download (https://transfer.sh/)
--> upload:
```bash
curl --upload-file ./filename.txt https://transfer.sh/filename.txt
```
(the above command will return a URL, e.g: https://transfer.sh/tG8rM/filename.txt)  
--> download:
```bash
curl https://transfer.sh/tG8rM/filename.txt -o filename.txt
```


##### Download file if necessary
    
```bash
data=file.txt
url=http://www.example.com/$data
if [! -s $data];then
    echo "downloading test data..."
    wget $url
fi
```

##### Wget to a filename (when a long name)
    
```bash
wget -O filename "http://example.com"
```

##### Wget files to a folder

```bash
wget -P /path/to/directory "http://example.com"
```


## Random
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
##### Random pick 100 lines from a file
    
```bash
shuf -n 100 filename
```

##### Random order (lucky draw)
    
```bash
for i in a b c d e; do echo $i; done| shuf
```

##### Echo series of random numbers between a range (e.g. shuffle numbers from 0-100, then pick 15 of them randomly)
    
```bash
shuf -i 0-100 -n 15
```

##### Echo a random number
    
```bash
echo $RANDOM
```

##### Random from 0-9
    
```bash
echo $((RANDOM % 10))
```

##### Random from 1-10
    
```bash
echo $(((RANDOM %10)+1))
```

## Xwindow
X11 GUI applications! Here are some GUI tools for you if you get bored by the text-only environment.  


##### Enable X11 forwarding,in order to use graphical application on servers
```bash
ssh -X user_name@ip_address
```
or setting through xhost

--> Install the following for Centos:  
xorg-x11-xauth  
xorg-x11-fonts-*  
xorg-x11-utils  

##### Little xwindow tools
    
```bash
xclock
xeyes
```

##### Open pictures/images from ssh server
```bash
1. ssh -X user_name@ip_address
2. apt-get install eog
3. eog picture.png
```

##### Use gedit on server (GUI editor) 
```bash
1. ssh -X user_name@ip_address
2. apt-get install gedit
3. gedit filename.txt
```
##### Open PDF file from ssh server 
```bash
1. ssh -X user_name@ip_address
2. apt-get install evince
3. evince filename.pdf
```
##### Use google-chrome browser from ssh server 
```bash
1. ssh -X user_name@ip_address
2. apt-get install libxss1 libappindicator1 libindicator7
3. wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
4. sudo apt-get install -f
5. dpkg -i google-chrome*.deb
6. google-chrome
 ```



[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]



## Others
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]
##### Remove newline / nextline
    
```bash
tr --delete '\n' <input.txt >output.txt
```

##### Replace newline
     
```bash
tr '\n' ' ' <filename
```

##### To uppercase/lowercase
     
```bash
tr /a-z/ /A-Z/
```

##### Compare files (e.g. fileA, fileB)
    
```bash
diff fileA fileB
```
//a: added; d:delete; c:changed

or

```bash
sdiff fileA fileB
```
//side-to-side merge of file differences


##### Number a file (e.g. fileA)

```bash
nl fileA
```
or

```bash
nl -nrz fileA
```
//add leading zeros


##### Combine/ paste two files (e.g. fileA, fileB)
    
```bash
paste fileA fileB
```
//default tab seperated


##### Reverse string
    
```bash
echo 12345| rev
```

##### Read .gz file without extracting
    
```bash
zmore filename
```
or
    
```bash
zless filename
```

##### Run in background, output error file
    
```bash
some_commands  &>log &
```

or


```bash
some_commands 2>log &
```

or

```bash
some_commands 2>&1| tee logfile
```

or

```bash
some_commands 2>&1 >>outfile
```
//0: standard input; 1: standard output; 2: standard error


##### Send mail
    
```bash
echo 'heres the content'| mail -A 'file.txt' -s 'mail.subject' me@gmail.com
```
//use -a flag to set send from (-a "From: some@mail.tld")


##### .xls to csv
    
```bash
xls2csv filename
```
##### Append to file (e.g. hihi)
    
```bash
echo 'hihi' >>filename
```

##### Make BEEP sound
    
```bash
speaker-test -t sine -f 1000 -l1
```

##### Set beep duration
    
```bash
(speaker-test -t sine -f 1000) & pid=$!;sleep 0.1s;kill -9 $pid
```

##### History edit/ delete
    
```bash
~/.bash_history
```
or

```bash
history -d [line_number]
```

##### Get last history/record filename
    
```bash
head !$
```

##### Clean screen
    
```bash
clear
```

or

```bash
Ctrl+l
```

##### Send data to last edited file
    
```bash
cat /directory/to/file
echo 100>!$
```

##### Run history number (e.g. 53)
    
```bash
!53
```

##### Run last command
    
```bash
!!
```

##### Run last command that began with (e.g. cat filename)
    
```bash
!cat
```

or

```bash
!c
```
//run cat filename again


##### Extract .xf
    
    1.unxz filename.tar.xz  
    2.tar -xf filename.tar

##### Install python package
    
```bash
pip install packagename
```

##### Delete current bash command
    
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


##### Add something to history (e.g. "addmetohistory")
    
```bash
#addmetodistory
```
//just add a "#" before~~


##### Sleep awhile or wait for a moment or schedule a job
    
```bash
sleep 5;echo hi
```

##### Count the time for executing a command
    
```bash
time echo hi
```

##### Backup with rsync
    
```bash
rsync -av filename filename.bak
rsync -av directory directory.bak
rsync -av --ignore_existing directory/ directory.bak
rsync -av --update directory directory.bak
```
//skip files that are newer on receiver (i prefer this one!)


##### Make all directories at one time!
    
```bash
mkdir -p project/{lib/ext,bin,src,doc/{html,info,pdf},demo/stat}
```
//-p: make parent directory  
//this will create project/doc/html/; project/doc/info; project/lib/ext ,etc


##### Run command only if another command returns zero exit status (well done)
    
```bash
cd tmp/ && tar xvf ~/a.tar
```

##### Run command only if another command returns non-zero exit status (not finish)
    
```bash
cd tmp/a/b/c ||mkdir -p tmp/a/b/c
```

##### Extract to a path
    
```bash
tar xvf -C /path/to/directory filename.gz
```

##### Use backslash "\" to break long command
    
```bash
cd tmp/a/b/c \
> || \
>mkdir -p tmp/a/b/c
```

##### Get pwd
    
```bash
VAR=$PWD; cd ~; tar xvf -C $VAR file.tar
```
//PWD need to be capital letter

##### List file type of file (e.g. /tmp/)
    
```bash
file /tmp/
```
//tmp/: directory


##### Bash script
    
```bash
#!/bin/bash
file=${1#*.}
```
//remove string before a "."

```bash
file=${1%.*}
```
//remove string after a "."

##### Search from history
    
```bash
Ctrl+r
```

##### Python simple HTTP Server
    
```bash
python -m SimpleHTTPServer
```

##### Variables
    
```bash
{i/a/,}
```
e.g. replace all
```bash
{i//a/,}
```
//for variable i, replace all 'a' with a comma

##### Read user input
    
```bash
read input
echo $input
```

##### Generate sequence 1-10
    
```bash
seq 10
```

##### Sum up input list (e.g. seq 10)
    
```bash
seq 10|paste -sd+|bc
```

##### Find average of input list/file
    
```bash
i=`wc -l filename|cut -d ' ' -f1`; cat filename| echo "scale=2;(`paste -sd+`)/"$i|bc
```

##### Generate all combination (e.g. 1,2)
    
```bash
echo {1,2}{1,2}
```
//1 1, 1 2, 2 1, 2 2

##### Generate all combination (e.g. A,T,C,G)
    
```bash
set = {A,T,C,G}
group= 5
for ((i=0; i<$group; i++));do
    repetition=$set$repetition;done
    bash -c "echo "$repetition""
```

##### Read file content to variable
```bash
foo=$(<test1)
```

##### Echo size of variable

```bash
echo ${#foo}
```

##### Echo tab

```bash
echo -e ' \t '
```

##### Array
```bash
declare -A array=()
```

##### Send a directory

```bash
scp -r directoryname user@ip:/path/to/send
```

##### Split file into lines (e.g. 1000 lines/smallfile)
```bash
$ split -d -l 1000 bigfilename
```

##### Rename all files (e.g. remove ABC from all .gz files)
```bash
rename 's/ABC//' *.gz
```

##### Remove extention (e.g remove .gz from filename.gz)
```bash
basename filename.gz .gz

zcat filename.gz> $(basename filename.gz .gz).unpacked
```

##### Use the squeeze repeat option (e.g. /t/t --> /t)
```bash
tr -s "/t" < filename
```

##### Do not print nextline with echo
```bash
echo -e 'text here \c'
```

##### Use the last argument
```bash
!$
```

##### Check last exit code
```bash
echo $?
```
##### View first 50 characters of file
```bash
head -c 50 file
```
 
##### Group/combine rows into one row 

e.g.  
AAAA  
BBBB  
CCCC  
DDDD  
```bash
cat filename|paste - -
-->
AAAABBBB
CCCCDDDD
cat filename|paste - - - -
-->
AAAABBBBCCCCDDDD
```

##### Fastq to fasta 
```bash
cat file.fastq | paste - - - - | sed 's/^@/>/g'| cut -f1-2 | tr '\t' '\n' >file.fa
```
##### Cut and get last column
```bash
cat file|rev | cut -d/ -f1 | rev
```

##### Add one to variable/increment a numeric variable (e.g. $var)
```bash
((var++))
```

##### Some handy environment variables
$0   :name of shell or shell script.  
$1, $2, $3, ... :positional parameters.  
$#   :number of positional parameters.  
$?   :most recent foreground pipeline exit status.  
$-   :current options set for the shell.  
$$   :pid of the current shell (not subshell).  
$!   :is the PID of the most recent background command.  

##### Clear the contents of a file (e.g. filename)
```bash
>filename
```
##### Unzip tar.bz2 file (e.g. file.tar.bz2)
```bash
tar xvfj file.tar.bz2
```
##### Output a y/n repeatedly until killed 
'y':
```bash
yes
```
or 'n':
```bash
yes n
```
or 'anything':
```bash
yes anything
```

For example: 
```bash
yes | rm -r large_directory
``` 

##### Create dummy file of certain size instantly (e.g. 200mb)
```bash
dd if=/dev/zero of=//dev/shm/200m bs=1024k count=200
``` 

Standard output:
200+0 records in 
200+0 records out 
209715200 bytes (210 MB) copied, 0.0955679 s, 2.2 GB/s 


## System
[[back to top](#handy-bash-oneliner-commands-for-tsv-file-editing)]

##### Snapshot of the current processes

```bash
ps 
```

##### Check graphics card

```bash
lspci
```

##### Show IP address
    
```bash
$ip add show
```
or
    
```bash
ifconfig
```

##### Check system version
    
```bash
cat /etc/*-release
```

##### Linux Programmer's Manuel: hier- description of the filesystem hierarchy
    
```bash
man hier
```

##### List job
    
```bash
jobs -l
```

##### Export PATH
    
```bash
export PATH=$PATH:~/path/you/want
```

##### Make file execuable
    
```bash
chmod +x filename
```
//you can now ./filename to execute it

##### List screen
    
```bash
screen -d -r
```

##### Echo screen name
    
```bash
screen -ls
```

##### Check system (x86-64)
    
```bash
uname -i
```

##### Surf the net

```bash
links www.google.com
```

##### Add user, set passwd
    
```bash
useradd username
passwd username
```

##### Edit variable for bash, (e.g. displaying the whole path)
    
```bash
1. joe ~/.bash_profile 
2. export PS1='\u@\h:\w\$' 
```
//$PS1 is a variable that defines the makeup and style of the command prompt 
```bash
3. source ~/.bash_profile
```

##### Edit environment setting (e.g. alias)
    
```bash
1. joe ~/.bash_profile
2. alias pd="pwd" //no more need to type that 'w'!
3. source ~/.bash_profile
```

##### List environment variables (e.g. PATH)
    
```bash
$echo $PATH
```
//list of directories separated by a colon

##### List all environment variables for current user
    
```bash
$env
```

##### Show partition format
    
```bash
lsblk
```

##### Soft link program to bin
    
```bash
ln -s /path/to/program /home/usr/bin
```
//must be the whole path to the program

##### Show hexadecimal view of data
    
```bash
hexdump -C filename.class
```

##### Jump to different node
    
```bash
rsh node_name
```

##### Check port (active internet connection)
    
```bash
netstat -tulpn
```

##### Find whick link to a file
    
```bash
readlink filename
```

##### Check where a command link to (e.g. python)
    
```bash
which python
```

##### List total size of a directory
    
```bash
du -hs .
```
or
    
```bash
du -sb
```

##### Copy directory with permission setting
    
```bash
cp -rp /path/to/directory
```

##### Store current directory
    
```bash
pushd . $popd ;dirs -l 
```

##### Show disk usage
    
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

##### Show current runlevel
    
```bash
runlevel
```

##### Switch runlevel
    
```bash
init 3 
```
or
```bash
telinit 3 
```
##### Permanently modify runlevel
    
```bash
1. edit /etc/init/rc-sysinit.conf 
2. env DEFAULT_RUNLEVEL=2 
```

##### Become root
    
```bash
su
```

##### Become somebody
    
```bash
su somebody
```

##### Report user quotes on device
    
```bash
requota -auvs
```

##### Get entries in a number of important databases
    
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

##### Change owner of file
    
```bash
chown user_name filename
chown -R user_name /path/to/directory/
```
//chown user:group filename

##### List current mount detail
    
```bash
df
```

##### List current usernames and user-numbers
    
```bash
cat /etc/passwd
```
##### Get all username
    
```bash
getent passwd| awk '{FS="[:]"; print $1}'
```

##### Show all users
    
```bash
compgen -u
```

##### Show all groups
    
```bash
compgen -g
```

##### Show group of user
    
```bash
group username
```

##### Show uid, gid, group of user
    
```bash
id username
```

##### Check if it's root
    
```bash
if [$(id -u) -ne 0];then
    echo "You are not root!"
    exit;
fi
```
//'id -u' output 0 if it's not root

##### Find out CPU information
    
```bash
more /proc/cpuinfo
```
or
    
```bash
lscpu
```

##### Set quota for user (e.g. disk soft limit: 120586240; hard limit: 125829120)
    
```bash
setquota username 120586240 125829120 0 0 /home
```

##### Show quota for user
    
```bash
quota -v username
```

##### Fork bomb
    
```bash
:(){:|:&};:
```
//dont try this at home

##### Check user login
    
```bash
lastlog
```

##### Edit path for all users
    
```bash
joe /etc/environment
```
//edit this file

##### Show running processes
    
```bash
ps aux
```

##### Find maximum number of processes
    
```bash
cat /proc/sys/kernal/pid_max
```

##### Show and set user limit
    
```bash
ulimit -u
```
##### Which ports are listening for TCP connections from the network

```bash
nmap -sT -O localhost
```

##### Print out number of cores/ processors

```bash
nproc --all
```
##### Check status of each core
1. top  
2. press '1'

##### Show jobs and PID

```bash
jobs -l
```

##### List all running services

```bash
service --status-all
```

##### Schedule shutdown server
```bash
shutdown -r +5 "Server will restart in 5 minutes. Please save your work."
```
##### Cancel scheduled shutdown
```bash
shutdown -c
```

##### Boardcast to all users
```bash
wall -n hihi
```
##### Kill all process of a user
```bash
pkill -U user_name
```
##### Set gedit preference on server

-->you might have to install the following:

apt-get install libglib2.0-bin;  

yum install dconf dconf-editor;  
yum install dbus dbus-x11;  

-->Check list  
```bash
gsettings list-recursively
```
-->Change setting  
e.g.
```bash
gsettings set org.gnome.gedit.preferences.editor highlight-current-line true
gsettings set org.gnome.gedit.preferences.editor scheme 'cobalt'
gsettings set org.gnome.gedit.preferences.editor use-default-font false
gsettings set org.gnome.gedit.preferences.editor editor-font 'Cantarell Regular 12'
```
##### Find out who has logged in on your system
--> [Quick] Printing out only the names:
```bash
users
```

--> [Detail] Printing out login time, load average, etc
```bash
w
```
##### Add user to a group (e.g add user 'nice' to the group 'docker', so that he can run docker without sudo) 
```bash
sudo gpasswd -a nice docker
```

##### pip install python package without root 
```bash
1. pip install --user package_name
2. You might need to export ~/.local/bin/ to PATH: export PATH=$PATH:~/.local/bin/
```

##### Removing old linux kernels (when /boot almost full...)
```bash
1. uname -a  #check current kernel, which should NOT be removed
2. sudo apt-get purge linux-image-X.X.X-X-generic  #replace old version
```


##### Change hostname
```bash
sudo hostname your-new-name
```

##### List installed packages
```bash
apt list --installed
```
or Red Hat: 
```bash
yum list installed
```

=-=-=-=-=-A lot more coming!! =-=-=-=-=-=-=-=-=-=waitwait-=-=-=-=-=-=-=-=-=-
