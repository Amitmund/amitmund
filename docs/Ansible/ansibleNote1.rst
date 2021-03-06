Ansible Quick Start
=====

What is Ansible:

- `Ansible` is an agentless configuration management system.
- `Ansible` work over SSH.
- `Ansible` runs it's modules on remote systems in order to complete the tasks and all the heavy lifting is generally is done by the remote host.
- You don't need anything else, except the ansible binary to work with `ansible` and its mostly relay on the `ssh`.


Example Ad-hoc command:
::
    ansbile localhost -m setup

Example ansible-playbook command example:
::
    ansible-playbook playbook1.yml


Ansible installation:
::

    yum list epel-release
    sudo yum -y install ansible

Example of few of the ansible dependency:
::

    libtomcrypt
    libtommath
    python-cffi
    python-enum34
    python-httplib2
    python-idna
    python-keyczar
    python-paramiko
    python-ply
    python-pycparser
    python2-crypto
    python2-cryptography
    python2-jmespath
    sshpass

Also its a good to have git, as we can manage the version of our ansible playbook.:
::

    sudo yum -y install git


--------------


We have ``ansibe configuration`` file and ``ansible inventory`` file

Ansible configuration file:
Primary ansible configuration file: ``/etc/ansible/ansible.cfg``

- You can configure your ansible default setting on the above file.

.. note::
    /etc/ansible/ansible.cfg

Default ansible inventory file: ``/etc/ansible/hosts``

.. note::
    /etc/ansible/hosts

.. note::
    An ``inventory`` is a list of hosts that Ansible manages.


An inventory location can be provieded as following:

- Default location: `/etc/ansible/hosts`
- Can be set in `ansible.cfg`
- In CLI as `ansible -i <inventory_path>`

What is bootstraping vs orchestration. 

orchestration:
  Orchestration describes automated arrangement, coordination and management of complex computer systems and services.

Inventory file example:
::

    # This is a comments.
    green.example.com
    192.168.1.100

    # Grouping a list of servers.
    [webservers]
    webserver1.example.com
    webserver2.example.com
    192.168.1.110

    # range of hosts
    www.[001:006].example.com


---------

Ansible Documentations:

- docs.ansible.com
``ansible-doc -s lineinfile``

------

The following note is not formated, its just for udpate as of now.
=====


