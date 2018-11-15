
sed
=====

.. Note:: I will be having some quick note on sed.
          This is mostly used for the text processing.


would replace repeating occurrences of x, y, or z with a single _
::

  echo "$string" | sed -r 's/[xyz]+/_/g'


How to remove the header from a file? [ -i in sed will update the file ]
::

  sed -i '1 d' filename

How to remove the footer from a file? [ $ is for end of the file ]
::

  sed -i '$ d' filename

How to replace the n-th line in a file with a new line in Unix?
::

  sed -i'' '10 d' filename       # d stands for delete
  sed -i'' '10 i new inserted line' filename     # i stands for insert

How do you remove the first number on 10th line in file?
::

 sed '10 s/[0-9][0-9]*//' < filename

How to remove the first 10 lines from a file?
::

  sed '1,10 d' < filename

How to replace the word "Gun" with "Pen" in the first 100 lines of a file?
::

  sed '100 s/Gun/Pen/' < filename


How to replace the second occurrence of the word "bat" with "ball" in a file?
::

  sed 's/bat/ball/2' < filename


Write a command to replace the word "bad" with "good" in file?
::

  sed s/bad/good/ < filename

