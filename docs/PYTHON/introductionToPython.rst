Quick Python Note:
=====

All are for python3

To install some module for python3

    - python3 -m pip install paramiko
    - python3 -m pip install fabric


# An quick working example:
...

    from fabric import Connection
    result = Connection('your_remote_host').run('uptime', hide=True)
    msg = "Ran {0.command!r} on {0.connection.host}, got stdout:\n{0.stdout}"
    print(msg.format(result))