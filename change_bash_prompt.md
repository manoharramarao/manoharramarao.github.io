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
    MAGENTA="\[\033[0;31m\]"
    ORANGE="\[\033[0;33m\]"
    PURPLE="\[\033[0;35m\]"
    WHITE="\[\033[0;37m\]"
    BOLD=""
    RESET="\[\033[m\]"
    
    #PS1="$GREEN\u@\h$NO_COLOR:\w$YELLOW\$(parse_git_branch)$NO_COLOR\$ "
    PS1="$PURPLE\D{%G %m %d} $WHITE| $MAGENTA\t $WHITE| $YELLOW\W $WHITE|$GREEN\$(parse_git_branch)$RESET \n$RED=> $RESET"
    {% endraw %}
    ```
2. source ~/.bashrc
3. with the above changes, prompt would look like this
    ```bash
    dell13 | 2021 05 15 | 15:07:13 | nextjs-blog | (feature-api-routes) 
    =>
    ```
    
    ![image](https://user-images.githubusercontent.com/2945080/118355778-8f0ee180-b58f-11eb-88f2-93f59dcae848.png)




