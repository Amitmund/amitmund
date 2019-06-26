
API Programming with Python Flask
=====


What Flask Provides out of box:

- Reciving HTTP requests
- Routing the HTTP requests to the controller
- Dispatching controller
- Returning the HTTP response


example 1:

::

    # I am using 4 space for indent, and in few editor the tab don't looks good..
    from flask import Flask, jsonify, request, Response

    # jsonify class: For json.
    # request class:
    # Response class: to return proper status code. Its upper case.

    # Need to explane the following line.
    # 
    app = Flask(__name__)

    ### for route / ####

    # The route and the function defination need to be in the same indent.
    @app.route('/')
    def hello():
        return "Hello World!"

    # There should an indent after the if statement, to define the block of the if statement.
    # Over here we are binding the app to host ip and to the port 5000.
    if __name__ == '__main__':
        app.run(host='0.0.0.0',port=5000)

.. note::
    Above is a quick sample code.
    
    In this code the application will be listening to the host on port 5000.



example 2:

.. note:: In this example we have added another route called '/book'

::

    # I am using 4 space for indent, and in few editor the tab don't looks good..
    from flask import Flask, jsonify, request, Response

    # jsonify class: For json.
    # request class:
    # Response class: to return proper status code. Its upper case.

    # Need to explane the following line.
    # 
    app = Flask(__name__)

    ### for route / ####

    @app.route('/')
    def hello():
        return "Hello World!"

    ### for route /book ###

    @app.route('/books')
    def welcome_to_book():
        return 'Welcome to the book api.'


    if __name__ == '__main__':
        app.run(host='0.0.0.0',port=5000)

.. note:: 
    Above is a quick sample code. In this code the application will be listening to the host on port 5000.

