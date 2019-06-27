
How to write in rst
=====

Some links:

- http://openalea.gforge.inria.fr/doc/openalea/doc/_build/html/source/sphinx/rest_syntax.html


Level 2
------

Level 3
~~~~~~

Level 4
#####

.. attention:: This is by using attention

.. caution:: This is by using caution

.. danger:: This is by using danger

.. error:: This is by using error

.. hint:: This is by using hint

.. important:: This is by using important

.. note:: This is by using note

.. tip:: This is by using tip

.. warning:: This is by using warning


-----

- This is a bullet list.

1. This is an enumerated list.

Definition lists:

what
    Definition lists associate a term with a definition.

how
    The term is a one-line phrase, and the definition is one
    or more paragraphs or body elements, indented relative to
    the term.

Field lists:

:what: Field lists map field names to field bodies, like
   database records.  They are often part of an extension
   syntax.

:how: The field marker is a colon, the field name, and a
  colon.

  The field body may contain one or more body elements,
      indented relative to the field marker.


-----



Few links to reffer
#####

http://docutils.sourceforge.net/docs/user/rst/quickref.html

https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html

http://docutils.sourceforge.net/docs/ref/rst/directives.html

http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html

-----

*emphasis*	Normally rendered as italics.

**strong emphasis**	Normally rendered as boldface.

`interpreted text`

``inline literal``


This is a paragraph.

Paragraphs line up at their left
edges, and are normally separated
by blank lines.



Bullet lists:
- This is item 1
- This is item 2

- Bullets are "-", "*" or "+".
  Continuing text must be aligned
  after the bullet and whitespace.

Note that a blank line is required
before the first item and after the
last, but is optional between items.


Enumerated lists:
3. This is the first item
4. This is the second item
5. Enumerators are arabic numbers,
   single letters, or roman numerals
6. List items should be sequentially
   numbered, but need not start at 1
   (although not all formatters will
   honour the first index).
#. This item is auto-enumerated


Definition lists:

what
  Definition lists associate a term with
  a definition.

how
  The term is a one-line phrase, and the
  definition is one or more paragraphs or
  body elements, indented relative to the
  term. Blank lines are not allowed
  between term and definition.


:Authors:
    Amit Kumar Mund
    (Testing on these.)

:Version: 1.0 of Nov/2018
:Dedication: Knowledge


A paragraph containing only two colons
indicates that the following indented
or quoted text is a literal block.

::

  Whitespace, newlines, blank lines, and
  all kinds of markup (like *this* or
  \this) is preserved by literal blocks.

  The paragraph containing only '::'
  will be omitted from the result.


Per-line quoting can also be used on
unindented literal blocks::

> Useful for quotes from email and
> for Haskell literate programming.


Grid table:

+------------+------------+-----------+
| Header 1   | Header 2   | Header 3  |
+============+============+===========+
| body row 1 | column 2   | column 3  |
+------------+------------+-----------+
| body row 2 | Cells may span columns.|
+------------+------------+-----------+
| body row 3 | Cells may  | - Cells   |
+------------+ span rows. | - contain |
| body row 4 |            | - blocks. |
+------------+------------+-----------+



Simple table:

=====  =====  ======
   Inputs     Output
------------  ------
  A      B    A or B
=====  =====  ======
False  False  False
True   False  True
False  True   True
True   True   True
=====  =====  ======



A transition marker is a horizontal line
of 4 or more repeated punctuation
characters.

------------

A transition should not begin or end a
section or document, nor should two
transitions be immediately adjacent.


External hyperlinks, like Python_.
.. _Python: http://www.python.org/


External hyperlinks, like `Python
<http://www.python.org/>`_.


For instance:
.. image:: images/ball1.gif


The |biohazard| symbol must be used on containers used to dispose of medical waste.
.. |biohazard| image:: images/biohazard.png


.. This text will not be shown
   (but, for instance, in HTML might be
   rendered as an HTML comment)


------------
