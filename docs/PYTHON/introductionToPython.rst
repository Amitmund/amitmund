Quick Python Note:
=====

All are for python3

#------------------------------------------------------------

To install some module for python3

    - python3 -m pip install paramiko
    - python3 -m pip install fabric

#------------------------------------------------------------

# An quick working example on ssh:
...

    from fabric import Connection
    result = Connection('your_remote_host').run('uptime', hide=True)
    msg = "Ran {0.command!r} on {0.connection.host}, got stdout:\n{0.stdout}"
    print(msg.format(result))


#------------------------------------------------------------

https://www.tutorialspoint.com/python/python_variable_types.htm


Python has five standard data types −

Numbers
    number = 1


String
    str = 'Hello World!'


List
    list = [ 'abcd', 786 , 2.23, 'john', 70.2  ]


Tuple
    tuple = ( 'abcd', 786 , 2.23, 'john', 70.2  )


Dictionary
tinydict = {'name': 'john','code':6734, 'dept': 'sales'}


# Note: The major difference between tuples and lists is that:
    List = ['mutable', 'list']
    Tuple = ('immutable','Tuple')

    This means that a list can be changed, but a tuple cannot.


# Data Type Conversion:

>>> number1 = 10
>>> type(number1)
<class 'int'>

>>> str=str(number1)
>>> type(str)
<class 'str'>


#------------------------------------------------------------

Python oracle connector:
    https://www.geeksforgeeks.org/oracle-database-connection-in-python/

#------------------------------------------------------------
  

