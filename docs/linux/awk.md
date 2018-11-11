#awk

Books:

Tempest	 Shakespears   	 15.75	 Penguin   
Christmas   	 Dickens	 3.50	 Academic
Iliad	 Homer	 10.25	 Random
Raven	 Poe	 2.50	 Penguin

```
$ gawk 'pattern action { } ' filename

$ gawk '/Penguin/ {print}' books
/Pattern/ {action} -> Beginning & ending slash.

$ gawk '/Poe/ {print}' books

$ gawk '/^Christmas/ {print}' books

$ gawk '/Random$/ {print}' books

$ gawk '/.en/ {print}' books

$ gawk '/[0-9]*\.50/ {print}' books

$ gawk '/Penguin | Academic/ {print}' books

$ gawk '/{pint $2, $4} ' books

$ gawk '/Dickens/ {print $4, $3, $2, $1; print $0 }' books

$ gawk '{print NR, $2, $4} ' books

FS => Input field delimiter. ( e.g. : )

$ gawk -F : '{print $1}' /etc/passwd

$ gawk 'FS=":" {print $1, $2}' /etc/passwd

$ gawk '{myfield = $2; print myfield }' books

$ gawk '(NR %2) ==0 {print NR, $0} ' books

$ gawk '{print; tot =tot + $3} END {print "Total=", tot}' books

$ gawk '{print; tot +=$3} END {print "Total= "' tot}' books

$ gawk '$3 > 10.00 {print}' books

$ gawk 'lenth($2) > 5 {print}' books

$ gawk '( $4 == "Penguin" ) && ( $3 > 10.00 ) {print}' books

$ gawk '( $4 == "Penguin" ) || ( $4 == "Academic" ) {print}' books

$ gawk '( $1 ~/mas/ ) {print}' books

$ gawk '($1 !~/mas/) {print}' books

$ gawk '( $4 ~ /[Pp]enguin/) {print} ' books
```

## SRE Interview Questions: awk

Unix Interview Questions on Awk Command
Awk is powerful tool in Unix. Awk is an excellent tool for processing the files which have data arranged in rows and columns format. It is a good filter and report writer. 

1. How to run awk command specified in a file?
awk -f filename

2. Write a command to print the squares of numbers from 1 to 10 using awk command
awk 'BEGIN { for(i=1;i<=10;i++) {print "square of",i,"is",i*i;}}'

3. Write a command to find the sum of bytes (size of file) of all files in a directory.
ls -l | awk 'BEGIN {sum=0} {sum = sum + $5} END {print sum}'

4. In the text file, some lines are delimited by colon and some are delimited by space. Write a command to print the third field of each line.

awk '{ if( $0 ~ /:/ ) { FS=":"; } else { FS =" "; } print $3 }' filename

5. Write a command to print the line number before each line?
awk '{print NR, $0}' filename

6. Write a command to print the second and third line of a file without using NR.
awk 'BEGIN {RS="";FS="\n"} {print $2,$3}' filename

7. Write a command to print zero byte size files?
ls -l | awk '/^-/ {if ($5 !=0 ) print $9 }'

8. Write a command to rename the files in a directory with "_new" as postfix?
ls -F | awk '{print "mv "$1" "$1".new"}' | sh

9. Write a command to print the fields in a text file in reverse order?
awk 'BEGIN {ORS=""} { for(i=NF;i>0;i--) print $i," "; print "\n"}' filename

10. Write a command to find the total number of lines in a file without using NR
awk 'BEGIN {sum=0} {sum=sum+1} END {print sum}' filename

Another way to print the number of lines is by using the NR. The command is
awk 'END{print NR}' filename
