
API Programming with Python Flask
=====


What Flask Provides out of box:

- Reciving HTTP requests
- Routing the HTTP requests to the controller
- Dispatching controller
- Returning the HTTP response


One example:

::

    # I am using 4 space for indent, and in few editor the tab don't looks good..
    from flask import Flask, jsonify, request, Response

    # jsonify class: For json.
    # request class:
    # Response class: to return proper status code. Its upper case.

    ### for route / #####

    @app.route('/')
        def hello():
        return "Hello World!"

    @app.route(' /books')
        def welcome_to_book():
        return 'Welcome to the book api.'


    if __name__ == '__main__':
    app.run(host='0.0.0.0',port=5000)

.. note:: Above is a quick sample code.
