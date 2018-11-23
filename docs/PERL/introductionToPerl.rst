
Introduction to perl
=====

PERL: Practical Extraction and Reporting Language

- Text processing
- System Administration Tasks
- Network Programming
- CGI and Web Programming
- Database Interaction

# to know the installed version of perl.
perl -v

http://perldoc.perl.org


General Perl Syntax
-----

- Each statement must be terminated with a semicolon ";"
- Comments are preceded by '#' sign
- Program file mush be shaved with a .pl or .PL file extention
- Can use an underscore (_) in place of spaces\
- Must not contain a space.


#!/usr/bin/env perl
# This is a comment. Perl interpreter will ignore this.

print "Hello", " ", "World", "\n";
print "Hello world\n";

chmod +x helloWorld.pl
./helloWorld.pl


Data Types
-----

- Perl is a loosely typed programming language.
- No need to define a `data type` in your perl program.
- Perl identifies the type based on context of the data.

- Scalar
- Arrays
- Hashes (associative array)


# Perl treats the following as false
0
('0')
undef
'' # Empty scalar.
() # Empty list.

# Perl treats the following as true
1
-1
'00' # Multiple zeroes in string
("0\n") # zero followed by newline
('') # string with space


Perl veriables
-----
- Perl variable names are preceded by a punctuation mark. Indicating the type of data.
- $ => for the perl Scalars.
- @ => for perl Arrays.
- % => for perl Hashes.


Perl scalar
-----

# For Numeric we don't need quote.
$age = 27;
$floatVar = 0.27;
$expoVar = 1.2e5;

# String Scalar
single quotes: $firstName = 'Ram';
Double quotes: $fullName = "firstName Kumar";
# Note: double quotes for the interpolation of the variable.

Perl another way for single and double quotes.

my @fruit = ('apples','oranges','guavas','grapes','bananas');

print q(The price of $fruit[0] is 10 dollars);
OUTPUT - The price of $fruit[0] is 10 dollers

print qq(The price of $fruit[0] is 10 dollars);
OUTPUT - The price of apples is 10 dollars


