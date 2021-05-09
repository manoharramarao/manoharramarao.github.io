Steps to change bash prompt in Linux/ubuntu/Kubuntu
====================================================

1. Copy the following to ~/.bashrc at the end of the file
    ```bash
    {% raw %}
    function parse_git_branch () {
        git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
    }

    RED="\[\033[0;31m\]"
    YELLOW="\[\033[0;33m\]"
    GREEN="\[\033[0;32m\]"
    NO_COLOR="\[\033[0m\]"
    MAGENTA="\[\033[1;31m\]"
    ORANGE="\[\033[1;33m\]"
    PURPLE="\[\033[1;35m\]"
    WHITE="\[\033[1;37m\]"
    BOLD=""
    RESET="\[\033[m\]"
    
    #PS1="$GREEN\u@\h$NO_COLOR:\w$YELLOW\$(parse_git_branch)$NO_COLOR\$ "
    PS1="$PURPLE\D{%G %m %d} $WHITE| $MAGENTA\t $WHITE| $YELLOW\W $WHITE|$GREEN\$(parse_git_branch)$NO_COLOR \n=> "
    {% endraw %}
    ```
2. source ~/.bashrc
3. with the above changes, prompt would look like this
    ```bash
    2018 01 14 01:14:23 data_related (master) =>
    ```



