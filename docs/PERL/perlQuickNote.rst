Perl quick note
=====


How to comment
-----

#

=begin
---
---
=cut

__DATA__

-- comment till end.
---
---


Data type
-----

$ -> Scalar
@ -> Array
% -> Hashed

.. Note::  Every statement must end with semicolon (;)


Example Data type
-----

$name='Amit'; # Scalar

$var=<<EOF;
This is a multi line
line code.
EOF

print $var;

@myArray=(1,2.25,2e5,'Amit');

print "First index of myArrary is $myArray[0]";


Memory Address of Scalar
-----

my $name='Amit';
my $memAddOfName=\$name;

print $memAddOfName;

Size of Array
-----

my @myArray=(1,2.25,2e5,'Amit');

my $size1=$#myArray+1;
my $size2=@myArrary;
my $size3=scalar @myArrary;


Array
------

@days=qw/mon tue wed thu fri sat sun/;
print "last day of week is $days[-1]";




