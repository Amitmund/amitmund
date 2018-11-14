
Perl
=====

perl oneliner
-----

::

  1. Decimal to binary:
  perl -wl -e '$num1 = sprintf("%b",15), print $num1;'

  2. Decimal to Hexa:
  perl -wl -e '$num1 = sprintf("%x",15), print $num1;'

  3. Decimal to Octal:
  perl -wl -e '$num1 = sprintf("%o",15), print $num1;' 

  * Further details: perldoc -f sprintf

  4. Finding duplicate line:
  perl -n -e 'print if $a{$_}++;' filename (or)
  perl -wnl -e 'print if $_{$_}++;' filename

  5. Removing blank line:
  perl -wnl -e 'print unless /^$/;' filename

  6. Numbering all the lines:
  perl -wnl -e 'print $_= "$. $_";' passwd


  7. Print the number of lines of file(s) that match a pattern:
  perl -wnl -e '$x++ if /amit/; END {print $x+0};' file1  file2

  7. example:
  perl -wnl -e '$x++ if /amit/; END {print $x+0};' test
  3
  $cat test
  amit amit
  amit amit
  mund mund
  amit mund

  8 . printing the total number of a match:
  perl -waln -e '$t += /amit/ for @F; END { print $t }' test
  5
  $cat test
  amit amit
  amit amit
  mund mund
  amit mund

  9. printing the unix time:
  perl -wl -e 'print time;'
  1405679195

  10. printing localtime:
  perl -wl -e 'print $curTime if $curTime=localtime;'
  Fri Jul 18 15:57:34 2014

  perl -wl -e 'print localtime;'
  41561518611451980

  l$ perl -le 'print scalar gmtime'
  Fri Jul 18 10:29:56 2014

  $ perl -le 'print scalar localtime'
  Fri Jul 18 16:00:14 2014

  11. Factorial of 6:
  perl -MMath::BigInt -le 'print Math::BigInt->new(6)->bfac()' 
  720

  12. print a..z:



  perl -le 'print join ",", ("a".."z");'

  13. print 1..1000:
  perl -le 'print join ",", ("1".."1000");'