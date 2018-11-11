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

