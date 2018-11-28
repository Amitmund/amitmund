About Microsoft Visualstudio Code Editor
=====

How to run perl files
-----

Code have task.json, where we can configure how you would like to execute a code. 
By default most of the new language are supported, but I found perl is not there and was trying to execute the perl code using this editor.

.. Note:: Make sure you have your perl directory as a top workspace.

1. Create a top level directory where all your perl scripts are there. # This is must. (AFAIK for now :) )
2. Select "Terminal" then click "Run Build Task..." And you will see "No build task to run found. Configure Build Task..." 
3. Select this "No build task to run found. Configure Build Task..."
4. Then it will give you, "Create tasks.json file from template", select the same.
5. You will get multiple options, Select "Others Example to run an arbitrary external command"
6. It will open tasks.json, and over there you have to update the details.

For running the perl code, following details I have added in my tasks.json.
More details you can check at: 
https://code.visualstudio.com/docs/editor/tasks
https://code.visualstudio.com/docs/editor/variables-reference

::

  {
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
      {
        "label": "Run with Perl",
        "type": "shell",
        "command": "perl ${file}",
        "group": {
          "kind": "build",
          "isDefault": true
        }
      }
    ]
  }


You can also define more then one command.
Example:

But I have not tested anything on the same much yet.

::

  {
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
      {
        "label": "Run bash script",
        "type": "shell",
        "command": "bash ${file}",
        "group": {
          "kind": "build",
          "isDefault": true
        }
      }
      {
        "label": "Run perl script",
        "type": "shell",
        "command": "perl ${file}",
        "group": {
          "kind": "build",
          "isDefault": true
        }
      }
    ]
  }