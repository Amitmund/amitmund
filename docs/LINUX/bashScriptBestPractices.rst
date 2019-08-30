Bash Script Best Practices
=====

Must have a check argument section

Example:

::

  # To check if the argument must be equal to 1 and there should be gap between [[ in ]] if block.
  # In this following example: "$# -ne 1"
  if [[ "$*" =~ "--help" || "$*" =~ "-h" || $# -ne 1 ]]; then
    usage
  fi

Must have a Usage section

Example:

::

  function usage(){
    echo ""
    echo "USAGE: $0 [ -h, --help, arg1 ]" 1>&2;
    echo "Example: $0 arg1"
    echo "Some more details over here."
    echo ""
    exit 1;
  }


..NOTE::
  # In variable there should not be spaces.
  agr1=$1



::

vi session-script
#!/bin/bash
ssh-add /path/to/key
bash -i # or other session starter

ssh-agent session-script