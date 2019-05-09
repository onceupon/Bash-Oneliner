# Bash-Oneliner
I am glad that you are here! I started working on bioinformatics a few years ago (recently switched to cloud computing), and was amazed by those single-word bash commands which are much faster than my dull scripts, time saved through learning command-line shortcuts and scripting. Not all the code here is oneliner, but i put effort on making them brief and swift. I am mainly using Ubuntu, RedHat and Linux Mint and CentOS, sorry if the commands dont work on your system. 

This blog will focus on simple bash commands for parsing data and Linux system maintenance that i acquired from work and LPIC exam. I apologize that there are no detailed citation for all the commands, but they are probably from dear Google and Stackoverflow.

English and bash are not my first language, please correct me anytime, thank you.  
If you know other cool commands, please teach me!

Here's a more stylish version of [Bash-Oneliner](http://onceupon.github.io/Bash-Oneliner/)~

## Handy Bash oneliner commands

- [Terminal Tricks](#terminal-tricks)
- [Variable](#variable)
- [Grep](#grep)
- [Sed](#sed)
- [Awk](#awk)
- [Xargs](#xargs)
- [Find](#find)
- [Condition and Loop](#condition-and-loop)
- [Math](#math)
- [Time](#time)
- [Download](#download)
- [Random](#random)
- [Xwindow](#xwindow)
- [System](#system)
- [Hardware](#hardware)
- [Networking](#networking)
- [Others](#others)

## Terminal Tricks

#####  Ctrl
```bash
Ctrl + n : same as Down arrow.
Ctrl + p : same as Up arrow.
Ctrl + r : begins a backward search through cammand history.(keep pressing Ctrl + r to move backward)
Ctrl + l : Clear the terminal
Ctrl + s : to stop output to terminal.
Ctrl + q : to resume output to terminal after Ctrl + s.
Ctrl + a : move to the beginning of line.
Ctrl + e : move to the end of line.
Ctrl + d : if you've type something, Ctrl + d deletes the character under the cursor, else, it escapes the current shell.
Ctrl + k : delete all text from the cursor to the end of line.
Ctrl + x + backspace : delete all text from the beginning of line to the cursor.
Ctrl + t : transpose the character before the cursor with the one under the cursor, press Esc + t to transposes the two words before the cursor.
Ctrl + w : cut the word before the cursor; then Ctrl + y paste it
Ctrl + u : cut the line before the cursor; then Ctrl + y paste it
Ctrl + x + Ctrl + e : launch editor define by $EDITOR
```
##### Change case
```bash
Esc + u
# converts text from cursor to the end of the word to uppercase.  
Esc + l
# converts text from cursor to the end of the word to uppercase. 
Esc + c
# converts letter under the cursor to uppercase.
```
##### Run history number (e.g. 53)
    
```bash
!53
```

##### Run last command
    
```bash
!!
```
##### Run last command and change some parameter using caret substitution (e.g. last command: echo 'aaa' -> rerun as: echo 'bbb')
```bash
#last command: echo 'aaa'
^aaa^bbb

#echo 'bbb'
#bbb

#Notice that only the first aaa will be replaced, if you want to replace all 'aaa', use ':&' to repeat it:
^aaa^bbb^:&
or 
!!:gs/aaa/bbb/

```

##### Run past command that began with (e.g. cat filename)
    
```bash
!cat
```

or

```bash
!c
# run cat filename again
```

## Grep
[[back to top](#handy-bash-oneliner-commands)]

#####  Type of grep
```bash
grep = grep -G # Basic Regular Expression (BRE)
fgrep = grep -F # fixed text, ignoring meta-charachetrs
egrep = grep -E # Extended Regular Expression (ERE)
pgrep = grep -P # Perl Compatible Regular Expressions (PCRE)
rgrep = grep -r # recursive
```
#####  Grep and count number of empty lines
```bash
grep -c "^$"
```

#####  Grep and return only integer
```bash
grep -o '[0-9]*'
#or
grep -oP '\d'
```
#####  Grep integer with certain number of digits (e.g. 3)
```bash
grep ‘[0-9]\{3\}’
# or
grep -E ‘[0-9]{3}’
# or
grep -P ‘\d{3}’
```

#####  Grep only IP address
```bash
grep -Eo '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}'
# or
grep -Po '\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}'
```

#####  Grep whole word (e.g. 'target')
```bash
grep -w 'target'
 
#or using RE
grep '\btarget\b'
```
#####  Grep returning lines before and after match (e.g. 'bbo')
```bash
# return also 3 lines after match
grep -A 3 'bbo'
 
# return also 3 lines before match
grep -B 3 'bbo'

# return also 3 lines before and after match
grep -C 3 'bbo'
```

#####  Grep string starting with (e.g. 'S')
```bash
grep -o 'S.*'
```

#####  Extract text bewteen words (e.g. w1,w2)
    
```bash
grep -o -P '(?<=w1).*(?=w2)'
```


##### Grep lines without word (e.g. bbo)
     
```bash
grep -v bbo filename
```

##### Grep lines not begin with string (e.g. #)
     
```bash
grep -v '^#' file.txt
```

##### Grep variables with space within it (e.g. bbo="some strings")
     
```bash
grep "$boo" filename
```
#remember to quote the variable!  

##### Grep only one/first match (e.g. bbo)

```bash
grep -m 1 bbo filename
```

##### Grep and return number of matching line(e.g. bbo)
    
```bash
grep -c bbo filename
```

##### Count occurrence (e.g. three times a line count three times)
    
```bash
grep -o bbo filename |wc -l 
```

##### Case insensitive grep (e.g. bbo/BBO/Bbo)
    
```bash
grep -i "bbo" filename 
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

##### Search all files in directory, do not ouput the filenames (e.g. bbo)
```bash
grep -rh bbo /path/to/directory 
```

##### Search all files in directory, output ONLY the filenames with matches(e.g. bbo)
```bash
grep -rl bbo /path/to/directory
```


##### Grep OR (e.g. A or B or C or D)
    
```
grep 'A\|B\|C\|D' 
```

##### Grep AND (e.g. A and B)
    
```bash
grep 'A.*B' 
```
##### Regex any singer character (e.g. ACB or AEB)
    
```bash
grep 'A.B' 
```
##### Regex with or without a certain character (e.g. color or colour)
    
```bash
grep ‘colou?r’
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
#grep -q will output 0 if match found  
#remember to add space between []!
```

##### Grep strings between a bracket()
```bash
grep -oP '\(\K[^\)]+'
```

##### Grep number of characters with known strings in between(e.g. AAEL000001-RA)
```bash
grep -o -w "\w\{10\}\-R\w\{1\}"
# \w word character [0-9a-zA-Z_] \W not word character 
```  
##### Skip directory (e.g. bbo)
```bash
grep -d skip 'bbo' /path/to/files/*
```  



## Sed
[[back to top](#handy-bash-oneliner-commands)]
##### Remove the 1st line
```bash
sed 1d filename
```

##### Remove the first 100 lines (remove line 1-100)
```bash
sed 1,100d filename
```

##### Remove lines with string (e.g. bbo)
    
```bash
sed "/bbo/d" filename
- case insensitive:
sed "/bbo/Id" filename
```
##### Remove lines whose nth character not equal to a value (e.g. 5th character not equal to 2)
```bash
sed -E '/^.{5}[^2]/d'
#aaaa2aaa (you can stay)
#aaaa1aaa (delete!)
```

##### Edit infile (edit and save)
    
```bash
sed -i "/bbo/d" filename
```
##### When using variable (e.g. $i), use double quotes " "
e.g. add >$i to the first line (to make a bioinformatics FASTA file)  
    
```bash
sed "1i >$i"  
# notice the double quotes! in other examples, you can use a single quote, but here, no way!   
# '1i' means insert to first line
```

##### Using environment variable and end-of-line pattern at the same time.
```bash
# Use backslash for end-of-line $ pattern, and double quotes for expressing the variable
sed -e "\$s/\$/\n+--$3-----+/"
```

##### Delete/remove empty lines
    
```bash
sed '/^\s*$/d' 
```    
or
   
```bash
sed '/^$/d' 
```
##### Delete/remove last line
   
```bash
sed '$d' 
```

##### Delete/remove last character from end of file
```bash
sed -i '$ s/.$//' filename
```

##### Add string to beginning of file (e.g. "\[")
```bash
sed -i '1s/^/[/' file
```

##### Add string at certain line number (e.g. add 'something' to line 1 and line 3)
```bash
sed -e '1isomething -e '3isomething'
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

##### Substitution with wildcard (e.g. replace a line start with aaa= by aaa=/my/new/path)
```bash
sed "s/aaa=.*/aaa=\/my\/new\/path/g"
```

##### Select lines start with string (e.g. bbo)
    
```bash
sed -n '/^@S/p' 
```
##### Delete lines with string (e.g. bbo)
    
```bash
sed '/bbo/d' filename 
```

##### Print/get/trim a range of line (e.g. line 500-5000)
    
```bash
sed -n 500,5000p filename
```

##### Print every nth lines
    
```bash
sed -n '0~3p' filename

# catch 0: start; 3: step
```



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

# notice a whitespace before '*'!!
```
##### Remove ending commas
    
```bash
sed 's/,$//g' 
```
##### Add a column to the end
    
```bash
sed "s/$/\t$i/"

# $i is the valuable you want to add  
# e.g. add the filename to every last column of the file  
```

    
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

##### Print a particular line (e.g. 123th line)
```bash
sed -n -e '123p'
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
```bash
sed '$ s/.$//'
```

##### Insert character at specified position of file (e.g. AAAAAA --> AAA#AAA)
```bash
sed -r -e 's/^.{3}/&#/' file
```


## Awk
[[back to top](#handy-bash-oneliner-commands)]

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
awk -v a="$a" -v b="$b" "$1==a && $10=b" filename 
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
awk '{split($2, a,",");for (i in a) print $1"\t"a[i]}' filename 
```

##### Print all lines before nth occurence of a string (e.g stop print lines when bbo appears 7 times)
    
```bash
awk -v N=7 '{print}/bbo/&& --N<=0 {exit}'
```

##### Print filename and last line of all files in directory
```bash
ls|xargs -n1 -I file awk '{s=$0};END{print FILENAME,s}' file
```

##### Add string to the beginning of a column (e.g add "chr" to column $3)
    
```bash
awk 'BEGIN{OFS="\t"}$3="chr"$3' 
```

##### Remove lines with string (e.g. bbo)
    
```bash
awk '!/bbo/' file 
```

##### Remove last column    
```bash
awk 'NF{NF-=1};1' file
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
[[back to top](#handy-bash-oneliner-commands)]

##### Set tab as delimiter (default:space)

```bash
xargs -d\t
```

##### Display 3 items per line

```bash
echo 1 2 3 4 5 6| xargs -n 3
# 1 2 3  
# 4 5 6

```
##### Prompt before execution

```bash
echo a b c |xargs -p -n 3
```

##### Print command along with output

```bash
xargs -t abcd
# bin/echo abcd  
# abcd

```
##### With find and rm

```bash
find . -name "*.html"|xargs rm
 
# when using a backtick
rm `find . -name "*.html"`
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

# v: verbose|  
# p: keep detail (e.g. owner)

```

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

# "--" signals the end of options and display further option processing
```

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

##### Xargs and sed (replace all old ip address with new ip address under /etc directory)
```bash
grep -rl '192.168.1.111' /etc | xargs sed -i 's/192.168.1.111/192.168.2.111/g'
```


## Find 
[[back to top](#handy-bash-oneliner-commands)]
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
find . -name '*.php' -exec sed -i 's/www/w/g' {} \;
```
if no subdirectory
    
```bash
replace "www" "w" -- *
# a space before *
```
##### Find and output only filename (e.g. "mso")
    
```bash
find mso*/ -name M* -printf "%f\n"
```

##### Find and delete file with size less than (e.g. 74 byte)
    
```bash
find . -name "*.mso" -size -74c -delete

# M for MB, etc
```


## Condition and loop
[[back to top](#handy-bash-oneliner-commands)]

##### If statement
```bash
# if and else loop for string matching
if [[ "$c" == "read" ]]; then outputdir="seq"; else outputdir="write" ; fi  

# Test if myfile contains the string 'test':
if grep -q hello myfile; then …

# Test if mydir is a directory, change to it and do other stuff:
if cd mydir; then
  echo 'some content' >myfile
else
  echo >&2 "Fatal error. This script requires mydir."
fi

# if variable is null
if [ ! -s "myvariable" ]
#True of the length if "STRING" is zero.

# Test if file exist
if [ -e 'filename' ]
then
  echo -e "file exists!"
fi

# Test if file exist but also including symbolic links:
if [ -e myfile ] || [ -L myfile ]
then
  echo -e "file exists!"
fi

# Test if the value of x is greater or equal than 5
if [ "$x" -ge 5 ]; then …

# Test if the value of x is greater or equal than 5, in bash/ksh/zsh:
if ((x >= 5)); then …

# Use (( )) for arithmetic operation
if ((j==u+2))

# Use [[ ]] for comparison
if [[ $age -gt 21 ]]
```

[More if commands](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

##### For loop
    
```bash
for i in $(ls); do echo file $i;done
#or
for i in *; do echo file $i; done

# Press any key to continue each loop
for i in $(cat tpc_stats_0925.log |grep failed|grep -o '\query\w\{1,2\}');do cat ${i}.log; read -rsp $'Press any key to continue...\n' -n1 key;done

# Print a file line by line when a key is pressed, 
oifs="$IFS"; IFS=$'\n'; for line in $(cat myfile); do ...; done
while read -r line; do ...; done <myfile

#If only one word a line, simply
for line in $(cat myfile); do echo $line; read -n1; done

#Loop through an array
for i in "${arrayName[@]}"; do echo $i;done

```

##### While loop, 

```bash
# Column subtraction of a file (e.g. a 3 columns file)
while read a b c; do echo $(($c-$b));done < <(head filename)
#there is a space between the two '<'s

# Sum up column subtraction
i=0; while read a b c; do ((i+=$c-$b)); echo $i; done < <(head filename)

# Keep checking a running process (e.g. perl) and start another new process (e.g. python) immetiately after it. (BETTER use the wait command! Ctrl+F 'wait')
while [[ $(pidof perl) ]];do echo f;sleep 10;done && python timetorunpython.py
```

##### switch (case in bash)
```bash
read type;
case $type in
  '0')
    echo 'how'
    ;;
  '1')
    echo 'are'
    ;;
  '2')
    echo 'you'
    ;;
esac
```

## Variable
[[back to top](#handy-bash-oneliner-commands)]
##### variable substitution within quotes
```bash
# foo=bar
 echo "'$foo'"
#'bar'
# double/single quotes around single quotes make the inner single quotes expand variables
```
##### get the length of variable
```bash
var="some string"
echo ${#var}  
# 11
```
##### get the first character of the variable
```bash
var=string
echo "${var:0:1}"
#s 

#or
echo ${var%%"${var#?}"}

```
##### remove the first or last string from variable
```bash
var="some string"
echo ${var:2}
#me string
```

##### replacement (e.g. remove the first leading 0 )
```bash
var="0050"
echo ${var[@]#0}
#050
```

##### replacement (e.g. replace 'a' with ',')
```bash
{var/a/,}
```
##### replace all (e.g. replace all 'a' with ',')
```bash
{var//a/,}
```
```bash
#with grep
 test="god the father"
 grep ${test// /\\\|} file.txt
 # turning the space into 'or' (\|) in grep
```
##### To change the case of the string stored in the variable to lower case (Parameter Expansion)
```bash
var=HelloWorld
echo ${var,,}
helloworld
```



## Math
[[back to top](#handy-bash-oneliner-commands)]
##### Print out the prime factors of a number (e.g. 50)
```bash
factor 50
```
##### Sum up input list (e.g. seq 10)
    
```bash
seq 10|paste -sd+|bc
```

##### Sum up a file (each line in file contains only one number)

```bash
awk '{s+=$1} END {print s}' filename
```


##### Column subtraction
    
```bash
cat file| awk -F '\t' 'BEGIN {SUM=0}{SUM+=$3-$2}END{print SUM}'
```


##### Simple math with expr
```bash
expr 10+20 #30
expr 10\*20 #600
expr 30 \> 20 #1 (true)
```

##### More math with bc

- Number of decimal digit/ significant figure  
```bash
echo "scale=2;2/3" | bc  
#.66
```
- Exponent operator  
```bash
echo "10^2" | bc  
#100
```

- Using variables   
```bash
echo "var=5;--var"| bc  
#4
```

## Time
[[back to top](#handy-bash-oneliner-commands)]

##### Find out the time require for executing a command
```bash
time echo hi
```

##### Wait for some time (e.g 10s)
```bash
sleep 10
```

##### Log out your account after a certain period of time (e.g 10 seconds)
```bash
TMOUT=10
#once you set this variable, logout timer start running!
```

##### Set how long you want to run a command 
```bash
#This will run the commmand 'sleep 10' for only 1 second.
timeout 1 sleep 10
```

##### Set when you want to run a command (e.g 1 min from now)
```bash
at now + 1min  #time-units can be minutes, hours, days, or weeks
warning: commands will be executed using /bin/sh
at> echo hihigithub >~/itworks
at> <EOT>   # press Ctrl + D to exit
job 1 at Wed Apr 18 11:16:00 2018
```


## Download
[[back to top](#handy-bash-oneliner-commands)]

##### Download the content of this README.md (the one your are viewing now)
```bash
curl https://raw.githubusercontent.com/onceupon/Bash-Oneliner/master/README.md | pandoc -f markdown -t man | man -l -
 
# or w3m (a text based web browser and pager)
curl https://raw.githubusercontent.com/onceupon/Bash-Oneliner/master/README.md | pandoc | w3m -T text/html

# or using emacs (in emac text editor) 
emacs --eval '(org-mode)' --insert <(curl https://raw.githubusercontent.com/onceupon/Bash-Oneliner/master/README.md | pandoc -t org)

# or using emacs (on terminal, exit using Ctrl + x then Ctrl + c) 
emacs -nw --eval '(org-mode)' --insert <(curl https://raw.githubusercontent.com/onceupon/Bash-Oneliner/master/README.md | pandoc -t org)
```

##### Download all from a page
    
```bash
wget -r -l1 -H -t1 -nd -N -np -A mp3 -e robots=off http://example.com

# -r: recursive and download all links on page  
# -l1: only one level link  
# -H: span host, visit other hosts  
# -t1: numbers of retries  
# -nd: don't make new directories, download to here  
# -N: turn on timestamp  
# -nd: no parent  
# -A: type (seperate by ,)  
# -e robots=off: ignore the robots.txt file which stop wget from crashing the site, sorry example.com
```

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
if [ ! -s $data ];then
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
[[back to top](#handy-bash-oneliner-commands)]
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
[[back to top](#handy-bash-oneliner-commands)]  

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
xcowsay
```

##### Open pictures/images from ssh server
```bash
1. ssh -X user_name@ip_address
2. apt-get install eog
3. eog picture.png
```

##### Watch videos on server
```bash
1. ssh -X user_name@ip_address
2. sudo apt install mpv
3. mpv myvideo.mp4
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


## System
[[back to top](#handy-bash-oneliner-commands)]

# Check if it's root running
if [ "$EUID" -ne 0 ]; then
        echo "Please run this as root"
        exit 1
fi

##### Snapshot of the current processes

```bash
ps 
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
# you can now ./filename to execute it
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
# $PS1 is a variable that defines the makeup and style of the command prompt 
```

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
# list of directories separated by a colon
```
##### List all environment variables for current user
    
```bash
$env
```
##### Unset environment variable (e.g. unset variable 'MYVAR')
```bash
unset MYVAR
```

##### Show partition format
    
```bash
lsblk
```

##### Soft link program to bin
    
```bash
ln -s /path/to/program /home/usr/bin
# must be the whole path to the program
```

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

##### Find which link to a file
    
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
pushd . 
 
# then pop
popd
 
#or use dirs to display the list of currently remembered directories. 
dirs -l 
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
# list all user account (all local and LDAP)  
# (e.g. fetch list of grop accounts)
```
    
```bash
getent group
# store in database 'group'
```

##### Change owner of file
    
```bash
chown user_name filename
chown -R user_name /path/to/directory/
# chown user:group filename
```

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
if [ $(id -u) -ne 0 ];then
    echo "You are not root!"
    exit;
fi
# 'id -u' output 0 if it's not root
```
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
# dont try this at home    
```bash
:(){:|:&};:
```

##### Check user login
    
```bash
lastlog
```

##### Edit path for all users
    
```bash
joe /etc/environment
# edit this file
```
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
#notice that some commpanies might not like you using nmap
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

##### Kill all process of a program
```bash
kill -9 $(ps aux | grep 'program_name' | awk '{print $2}')
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
if not working, do also:  
```bash
hostnamectl set-hostname your-new-hostname
```
then run:  
hostnamectl

check /etc/hostname  

if still not working..., edit:  
/etc/sysconfig/network  
/etc/sysconfig/network-scripts/ifcfg-ensxxx  
add HOSTNAME="your-new-hostname"  
  

##### List installed packages
```bash
apt list --installed
```
or Red Hat: 
```bash
yum list installed
```

##### Check which file make the device busy on umount
```bash
lsof /mnt/dir
```


##### When sound not working
```bash
killall pulseaudio
```
then press Alt-F2 and type in pulseaudio  

##### When sound not working
```bash
killall pulseaudio
```
 ##### List information about SCSI devices
```bash
lsscsi
```
##### Tutorial for setting up your own DNS server
http://onceuponmine.blogspot.tw/2017/08/set-up-your-own-dns-server.html

##### Tutorial for creating a simple daemon
http://onceuponmine.blogspot.tw/2017/07/create-your-first-simple-daemon.html

##### Tutorial for using your gmail to send email
http://onceuponmine.blogspot.tw/2017/10/setting-up-msmtprc-and-use-your-gmail.html

 ##### Using telnet to test open ports, test if you can connect to a port (e.g 53) of a server (e.g 192.168.2.106)
```bash
telnet 192.168.2.106 53
```
##### change network maximum transmission unit (mtu) (e.g. change to 9000) 
```bash
ifconfig eth0 mtu 9000
```
##### get pid of a running process (e.g python) 
```bash
pidof python
```
or  
```bash
ps aux|grep python
```
##### ntp
start ntp:  
```bash
ntpd
```
check ntp:  
```bash
ntpq -p
```
##### remove unnecessary files to clean your server
```bash
sudo apt-get autoremove
sudo apt-get clean
sudo rm -rf ~/.cache/thumbnails/*
```
Remove old kernal:
```bash
sudo dpkg --list 'linux-image*'
sudo apt-get remove linux-image-OLDER_VERSION
```

##### Increase/ resize root partition (root partition is an LVM logical volume)
```bash
pvscan
lvextend -L +130G /dev/rhel/root -r
```
#Adding -r will grow filesystem after resizing the volume.  


##### Create a UEFI Bootable USB drive (e.g. /dev/sdc1)
```bash
sudo dd if=~/path/to/isofile.iso of=/dev/sdc1 oflag=direct bs=1048576
```
##### Locate and remove a package
```bash
sudo dpkg -l | grep <package_name>
sudo dpkg --purge <package_name>
```

##### Create a ssh tunnel
```bash
ssh -f -L 9000:targetservername:8088 root@192.168.14.72 -N
#-f: run in background; -L: Listen; -N: do nothing  
#the 9000 of your computer is now connected to the 8088 port of the targetservername through 192.168.14.72  
#so that you can see the content of targetservername:8088 by entering localhost:9000 from your browser.
```
##### Get process ID of a process (e.g. sublime_text)
```bash
#pidof
pidof sublime_text

#pgrep, you dont have to type the whole program name
pgrep sublim

#top, takes longer time
top|grep sublime_text

```

##### Some benchmarking tools for your server
[aio-stress](https://openbenchmarking.org/test/pts/aio-stress) - AIO benchmark.   
[bandwidth](https://zsmith.co/bandwidth.html) - memory bandwidth benchmark.  
[bonnie++](https://www.coker.com.au/bonnie++/) - hard drive and file system performance benchmark.   
[dbench](https://dbench.samba.org/) -  generate I/O workloads to either a filesystem or to a networked CIFS or NFS server.  
[dnsperf](https://www.dnsperf.com/) - authorative and recursing DNS servers.   
[filebench](https://github.com/filebench/filebench) - model based file system workload generator.  
[fio](https://linux.die.net/man/1/fio) - I/O  benchmark.  
[fs_mark](https://github.com/josefbacik/fs_mark) - synchronous/async file creation benchmark.  
[httperf](https://github.com/httperf/httperf) - measure web server performance.  
[interbench](https://github.com/ckolivas/interbench) - linux interactivity  benchmark.  
[ioblazer](https://labs.vmware.com/flings/ioblazer) - multi-platform storage stack micro-benchmark.  
[iozone](http://www.iozone.org/) - filesystem benchmark.  
[iperf3](https://iperf.fr/iperf-download.php) - measure TCP/UDP/SCTP performance.  
[kcbench](https://github.com/knurd/kcbench) - kernel compile benchmark, compiles a kernel and messures the time it takes.  
[lmbench](http://www.bitmover.com/lmbench/) - Suite of simple, portable benchmarks.  
[netperf](https://github.com/HewlettPackard/netperf) - measure network performance, test unidirectional throughput, and end-to-end latency.  
[netpipe](https://linux.die.net/man/1/netpipe) - network protocol independent performance evaluator.  
[nfsometer](http://wiki.linux-nfs.org/wiki/index.php/NFSometer) - NFS performance framework.  
[nuttcp](https://www.nuttcp.net/Welcome%20Page.html) - measure network performance.  
[phoronix-test-suite](https://www.phoronix-test-suite.com/) - comprehensive automated testing and benchmarking platform.    
[seeker](https://github.com/fidlej/seeker) - portable disk seek benchmark.  
[siege](https://github.com/JoeDog/siege) - http load tester and benchmark.  
[sockperf](https://github.com/Mellanox/sockperf) - network benchmarking utility over socket API.  
[spew](https://linux.die.net/man/1/spew) - measures I/O performance and/or generates I/O load.   
[stress](https://people.seas.harvard.edu/~apw/stress/) - workload generator for POSIX systems.  
[sysbench](https://github.com/akopytov/sysbench) - scriptable database and system performance benchmark.   
[tiobench](https://github.com/mkuoppal/tiobench) - threaded IO benchmark.  
[unixbench](https://github.com/kdlucas/byte-unixbench) - the original BYTE UNIX benchmark suite, provide a basic indicator of the performance of a Unix-like system.  
[wrk](https://github.com/wg/wrk) - HTTP benchmark.   


##### Show a listing of last logged in users.
```bash
lastb
```
##### Show a listing of current logged in users, print information of them
```bash
who
```
##### Show who is logged on and what they are doing
```bash
w
```

##### Print the user names of users currently logged in to the current host.
```bash
users
```
##### Stop tailing a file on program terminate
```bash
tail -f --pid=<PID> filename.txt
# replace <PID> with the process ID of the program.
```

##### List all enabled services
```bash
systemctl list-unit-files|grep enabled
```


## Hardware
[[back to top](#handy-bash-oneliner-commands)]

##### Collect and summarize all hardware info of your machine
```bash
lshw -json >report.json
# Other options are: [ -html ]  [ -short ]  [ -xml ]  [ -json ]  [ -businfo ]  [ -sanitize ] ,etc
```


##### Finding Out memory device detail
```bash
sudo dmidecode -t memory
```

##### Print detail of CPU hardware
```bash
dmidecode -t 4
#          Type   Information
#          0   BIOS
#          1   System
#          2   Base Board
#          3   Chassis
#          4   Processor
#          5   Memory Controller
#          6   Memory Module
#          7   Cache
#          8   Port Connector
#          9   System Slots
#         11   OEM Strings
#         13   BIOS Language
#         15   System Event Log
#         16   Physical Memory Array
#         17   Memory Device
#         18   32-bit Memory Error
#         19   Memory Array Mapped Address
#         20   Memory Device Mapped Address
#         21   Built-in Pointing Device
#         22   Portable Battery
#         23   System Reset
#         24   Hardware Security
#         25   System Power Controls
#         26   Voltage Probe
#         27   Cooling Device
#         28   Temperature Probe
#         29   Electrical Current Probe
#         30   Out-of-band Remote Access
#         31   Boot Integrity Services
#         32   System Boot
#         34   Management Device
#         35   Management Device Component
#         36   Management Device Threshold Data
#         37   Memory Channel
#         38   IPMI Device
#         39   Power Supply
```
##### Count the number of Segate hard disks
```bash
lsscsi|grep SEAGATE|wc -l
or
sg_map -i -x|grep SEAGATE|wc -l
```
##### Get UUID of a disk (e.g. sdb)
```bash
blkid /dev/sdb
```

##### Print detail of all hard disks
```bash
lsblk -io KNAME,TYPE,MODEL,VENDOR,SIZE,ROTA
#where ROTA means rotational device / spinning hard disks (1 if true, 0 if false)
```
##### List information about NIC
```bash
lspci | egrep -i --color 'network|ethernet'
```
##### Found out power status of the server
```bash
ipmitool -U your_bmc_username -P your_bmc_userpassword -I lanplus -H your_bmc_ip_address power status
```
##### Found out server sensor temperature
```bash
ipmitool sensors |grep -i Temp
```
## Networking
[[back to top](#handy-bash-oneliner-commands)]

##### Display IP address
```bash
ip a
```

##### Display route table
```bash
ip r
```

##### Display ARP cache (ARP cache displays the MAC addresses of deveice in the same network that you have connected to)
```bash
ip n
```

##### Add transient IP addres (reset after reboot) (e.g. add 192.168.140.3/24 to device eno16777736)
```bash
ip address add 192.168.140.3/24 dev eno16777736
```

##### Persisting network configuration changes
```bash
sudo vi /etc/sysconfig/network-scripts/ifcfg-enoxxx
# then edit the fields: BOOTPROT, DEVICE, IPADDR, NETMASK, GATEWAY, DNS1 etc
```
##### Refresh NetworkManager 
```bash
sudo nmcli c reload
```

##### Restart all interfaces
```bash
sudo systemctl restart network.service
```

##### To view hostname, OS, kernal, architecture at the same time!
```bash
hostnamectl
```

##### Set hostname (set all transient, static, pretty hostname at once)
```bash
hostnamectl set-hostname "mynode"
```


## Others
[[back to top](#handy-bash-oneliner-commands)]
##### Get parent directory of current directory
```bash
dirname `pwd`
```

##### Copy a file to multiple files (e.g copy fileA to file(B-D))
```bash
tee <fileA fileB fileC fileD >/dev/null
```

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
##### Translate a range of characters (e.g. substitute a-z into a)
     
```bash
echo 'something' |tr a-z a
# aaaaaaaaa
```

##### Compare two files (e.g. fileA, fileB)
    
```bash
diff fileA fileB
# a: added; d:delete; c:changed
```

or

```bash
sdiff fileA fileB
# side-to-side merge of file differences
```

##### Compare two files, strip trailing carriage return/ nextline (e.g. fileA, fileB)
    
```bash
 diff fileA fileB --strip-trailing-cr
```

##### Number a file (e.g. fileA)

```bash
nl fileA
```
or

```bash
nl -nrz fileA
# add leading zeros
```
or  
```bash
nl -w1 -s ' '
# making it simple, blank seperated
```

##### Join two files field by field with tab (default join by the first column of both file, and default separator is space)
```bash
# fileA and fileB should have the same ordering of lines.
join -t '\t' fileA fileB
 
# Join using specified field (e.g. column 3 of fileA and column 5 of fileB)
join -1 3 -2 5 fileA fileB
```

##### Combine/ paste two or more files into columns (e.g. fileA, fileB, fileC)
    
```bash
paste fileA fileB fileC
# default tab seperated
```

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
some_commands |& tee logfile
```

or

```bash
some_commands 2>&1 >>outfile
#0: standard input; 1: standard output; 2: standard error
```

##### Send mail
    
```bash
echo 'heres the content'| mail -a /path/to/attach_file.txt -s 'mail.subject' me@gmail.com
# use -a flag to set send from (-a "From: some@mail.tld")
```

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
# to make it to history
```

##### Add something to history (e.g. "addmetohistory")
    
```bash
#addmetodistory
#just add a "#" before~~
```

##### Sleep awhile or wait for a moment or schedule a job
    
```bash
sleep 5;echo hi
```

##### Backup with rsync
    
```bash
rsync -av filename filename.bak
rsync -av directory directory.bak
rsync -av --ignore_existing directory/ directory.bak
rsync -av --update directory directory.bak
rsync -av directory user@ip_address:/path/to/directory.bak
```
//skip files that are newer on receiver (i prefer this one!)


##### Make all directories at one time!
    
```bash
mkdir -p project/{lib/ext,bin,src,doc/{html,info,pdf},demo/stat}
# -p: make parent directory  
# this will create project/doc/html/; project/doc/info; project/lib/ext ,etc
```

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
# PWD need to be capital letter
```

##### List file type of file (e.g. /tmp/)
    
```bash
file /tmp/
# tmp/: directory
```



##### Bash script
    
```bash
#!/bin/bash
file=${1#*.}
# remove string before a "."
```

```bash
file=${1%.*}
# remove string after a "."
```

##### Search from history
    
```bash
Ctrl+r
```

##### Python simple HTTP Server
    
```bash
python -m SimpleHTTPServer
```

##### Read user input
    
```bash
read input
echo $input
```

##### Generate sequence 1-10
    
```bash
seq 10
```

##### Find average of input list/file
    
```bash
i=`wc -l filename|cut -d ' ' -f1`; cat filename| echo "scale=2;(`paste -sd+`)/"$i|bc
```

##### Generate all combination (e.g. 1,2)
    
```bash
echo {1,2}{1,2}
# 1 1, 1 2, 2 1, 2 2
```
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
declare -a array=()
 
#or
declare array=()
 
#or associative array 
declare -A array=()
```

##### Send a directory

```bash
scp -r directoryname user@ip:/path/to/send
```

##### Split file into smaller file
```bash
# Split by line (e.g. 1000 lines/smallfile)
split -d -l 1000 largefile.txt
 
# Split by byte without breaking lines across files
split -C 10 largefile.txt
```

##### Create a large amount of dummy files (e.g 100000 files, 10 bytes each):
```bash
#1. Create a big file
dd if=/dev/zero of=bigfile bs=1 count=1000000

#2. Split the big file to 100000 10-bytes files
 split -b 10 -a 10 bigfile
```

##### Rename all files (e.g. remove ABC from all .gz files)
```bash
rename 's/ABC//' *.gz
```

##### Remove file extension (e.g remove .gz from filename.gz)
```bash
basename filename.gz .gz

zcat filename.gz> $(basename filename.gz .gz).unpacked
```
##### Add file extension to all file(e.g add .txt)
```bash
rename s/$/.txt/ *
# You can use rename -n s/$/.txt/ * to check the result first, it will only print sth like this:
# rename(a, a.txt)
# rename(b, b.txt)
# rename(c, c.txt)
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

```bash
#e.g.  
#AAAA  
#BBBB  
#CCCC  
#DDDD  
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

##### Add one to variable/increment/ i++ a numeric variable (e.g. $var) 
```bash
((var++))
or
var=$((var+1))

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
##### Unzip tar.xz file (e.g. file.tar.xz)
```bash
unxz file.tar.xz
tar xopf file.tar
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
or
dd if=/dev/zero of=//dev/shm/200m bs=1M count=200
``` 

Standard output:  
200+0 records in  
200+0 records out  
209715200 bytes (210 MB) copied, 0.0955679 s, 2.2 GB/s  

##### Cat to a file
```bash
cat >myfile
let me add sth here
exit by control + c
^C
``` 

##### Keep /repeatedly executing the same command (e.g Repeat 'wc -l filename' every 1 second)
```bash
watch -n 1 wc -l filename
``` 

##### Print commands and their arguments when execute (e.g. echo `expr 10 + 20 `)
```bash
set -x; echo `expr 10 + 20 `
``` 

##### Print some meaningful sentences to you (install fortune first)
```bash
fortune
``` 
##### Colorful (and useful) version of top (install htop first)
```bash
htop
``` 
##### Press any key to continue
```bash
read -rsp $'Press any key to continue...\n' -n1 key
``` 

##### Run sql-like command on files from terminal
download:  
https://github.com/harelba/q  
example:
```bash
q -d "," "select c3,c4,c5 from /path/to/file.txt where c3='foo' and c5='boo'"
``` 

##### Sreen and tmux
create session and attach:
```bash
screen
or  
tmux
``` 

create detached session foo:  
```bash
screen -S foo -d -m	
or  
tmux new -s foo -d
``` 

detached session foo:  
```bash
screen: ^a^d
or  
tmux: ^bd
``` 


list sessions:  
```bash
screen -ls	
or  
tmux ls
``` 

attach:  
```bash
screen -r	
or  
tmux attach
``` 

attach to session foo:  
```bash
screen -r foo	
or 
tmux attach -t foo
``` 
kill session foo:
```bash
screen -r foo -X quit
or  
tmux kill-session -t foo
``` 
scroll:  
(screeen)  
Hit your screen prefix combination (C-a / control+A), then hit Escape.  
Move up/down with the arrow keys (↑ and ↓).  

Redirect output of an already running process in screen:  
 (C-a / control+A), then hit 'H'  

store screen output for screen:  
Ctrl+A, Shift+H  
You will then find a screen.log file under current directory.

(tmux)  
Ctrl-b then \[ then you can use your normal navigation keys to scroll around.  
Press q to quit scroll mode.  

Send command to all panes in tmux:
```bash
Ctrl-B
:setw synchronize-panes
``` 
Some tmux pane control commands:
```bash
Ctrl-B

#   Panes (splits), Press Ctrl+B, then input the following symbol:
#   %  horizontal split
#   "  vertical split
#   o  swap panes
#   q  show pane numbers
#   x  kill pane
#   space - toggle between layouts

#   Distribute Vertically (rows): 
select-layout even-vertical
#   or
Ctrl+b, Alt+2

#   Distribute horizontally (columns): 
select-layout even-horizontal
#   or
Ctrl+b, Alt+1

``` 
##### Cut the last column
```bash
cat filename|rev|cut -f1|rev
``` 
##### pass password to ssh
```bash
sshpass -p mypassword ssh root@10.102.14.88 "df -h"
```
##### wait for a pid (job) to complete
```bash
wait %1 
or 
wait $PID
wait ${!}
#wait ${!} to wait till the last background process ($! is the PID of the last background process)
```
##### pdf to txt
```bash
sudo apt-get install poppler-utils
pdftotext example.pdf example.txt
```
##### list only directory
```bash
ls -ld -- */
```

##### Capture/record/save terminal output (capture everything you type and output)
```bash
script output.txt
#start using terminal 
#to logout the screen session (stop saving the contents), type exit.
```
##### list contents of directories in a tree-like format.
```bash
tree
#go to the directory you want to list, and type tree (sudo apt-get install tree)
#output:
#one/
#└── two
#    ├── 1
#    ├── 2
#    ├── 3
#    ├── 4
#    └── 5
#
```
##### set up virtualenv(sandbox) for python
```bash
#1. install virtualenv.
sudo apt-get install virtualenv
#2. Creat a directory (name it .venv or whatever name your want) for your new shiny isolated environment.
virtualenv .venv
#3. source virtual bin
source .venv/bin/activate
#4. you can check check if you are now inside a sandbox.
type pip
#5. Now you can install your pip package, here requirements.txt is simply a txt file containing all the packages you want. (e.g tornado==4.5.3).
pip install -r requirements.txt

```
##### Working with json data
```bash
#install the useful jq package
#sudo apt-get install jq
#e.g. to get all the values of the 'url' key, simply pipe the json to the following jq command(you can use .[]. to select inner json, i.e jq '.[].url')
jq '.url'
```
##### Editing your history
```bash
history -w
vi ~/.bash_history
history -r
```
##### Decimal to Binary (e.g get binary of 5)
```bash
D2B=({0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1})
echo -e ${D2B[5]}
#00000101
echo -e ${D2B[255]}
#11111111
```

##### Wrap each input line to fit in specified width (e.g 4 integers per line)
```bash
echo "00110010101110001101" | fold -w4
#0011
#0010
#1011
#1000
#1101
```
##### Sort a file by column and keep the original order
```bash
sort -k3,3 -s
```

##### Right align a column (right align the 2nd column)
```bash
cat file.txt|rev|column -t|rev
```
##### To both view and store the output
```bash
echo 'hihihihi' | tee outputfile.txt
# use '-a' with tee to append to file.
```

##### Show non-printing (Ctrl) characters with cat
```bash
cat -v filenme
```
##### Convert tab to space
```bash
expand filenme
```
##### Convert space to tab 
```bash
unexpand filenme
```

##### Display file in octal ( you can also use od to display hexadecimal, decimal, etc)
```bash
od filenme
```

##### Reverse cat a file
```bash
tac filenme
```
##### Reverse the result from `uniq -c`
```bash
while read a b; do yes $b |head -n $a ;done <test.txt
```
> More coming!!
