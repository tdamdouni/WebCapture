# Command line fun: Insult the user when typing wrong bash command

_Captured: 2017-12-02 at 23:19 from [www.cyberciti.biz](https://www.cyberciti.biz/howto/insult-linux-unix-bash-user-when-typing-wrong-command/)_

You can configure sudo command to insult user when they type the wrong password. Now, it is possible to abuse insult the user when they enter the wrong command at the shell prompt.

[Want to watch TV on Linux?](https://www.cyberciti.biz/aclk?sa=l&ai=CupWQ5SYjWsr4EpPMpgOVi5uwAcH3nrRN_6ai2osGiZW8tIwJEAEgocuPAmDJBqAB6v3V5gPIAQaoAwHIAwKqBM0BT9BJ44KIHQvuzE8mpgyvq5epsMcRKcjEs2eGVE_8Hd297reXa5QWEcXg6qSO1R0OMi9Zw8_gTTz4O2uCQ003bK4KCJwpRk5DwG36uNsehQAA5-_41x5ZlsLOLTmgbcnLso7RR58pA0s_6ZAJl0tqzxwLjBTII45ytyJpz9BTieVTpPhPD5dNDFAM_LtmKXeNxwUDIJRgH6wOl3QqqLWbIWRPS-ewWgQXQoZunWClzZxTghHl9KsIkhMZy7eLCUyQTB3NzDeZGdhC3YA0P6AGN4AH_oGqGagHpr4b2AcB0ggHCIBhEAEYArEJbAykrlNCaPiACgHYEwM&num=1&sig=AOD64_0yponkAgY51u83saT34i5ykkZGMQ&client=ca-pub-7825705102693166&adurl=http://www.hauppauge.com/linux&nb=0)

Ad

[Watch over-the-air HD TV with a   
Hauppauge TV tuner ](https://www.cyberciti.biz/aclk?sa=l&ai=CupWQ5SYjWsr4EpPMpgOVi5uwAcH3nrRN_6ai2osGiZW8tIwJEAEgocuPAmDJBqAB6v3V5gPIAQaoAwHIAwKqBM0BT9BJ44KIHQvuzE8mpgyvq5epsMcRKcjEs2eGVE_8Hd297reXa5QWEcXg6qSO1R0OMi9Zw8_gTTz4O2uCQ003bK4KCJwpRk5DwG36uNsehQAA5-_41x5ZlsLOLTmgbcnLso7RR58pA0s_6ZAJl0tqzxwLjBTII45ytyJpz9BTieVTpPhPD5dNDFAM_LtmKXeNxwUDIJRgH6wOl3QqqLWbIWRPS-ewWgQXQoZunWClzZxTghHl9KsIkhMZy7eLCUyQTB3NzDeZGdhC3YA0P6AGN4AH_oGqGagHpr4b2AcB0ggHCIBhEAEYArEJbAykrlNCaPiACgHYEwM&num=1&sig=AOD64_0yponkAgY51u83saT34i5ykkZGMQ&client=ca-pub-7825705102693166&adurl=http://www.hauppauge.com/linux)

[Hauppauge Inc.](https://www.cyberciti.biz/aclk?sa=l&ai=CupWQ5SYjWsr4EpPMpgOVi5uwAcH3nrRN_6ai2osGiZW8tIwJEAEgocuPAmDJBqAB6v3V5gPIAQaoAwHIAwKqBM0BT9BJ44KIHQvuzE8mpgyvq5epsMcRKcjEs2eGVE_8Hd297reXa5QWEcXg6qSO1R0OMi9Zw8_gTTz4O2uCQ003bK4KCJwpRk5DwG36uNsehQAA5-_41x5ZlsLOLTmgbcnLso7RR58pA0s_6ZAJl0tqzxwLjBTII45ytyJpz9BTieVTpPhPD5dNDFAM_LtmKXeNxwUDIJRgH6wOl3QqqLWbIWRPS-ewWgQXQoZunWClzZxTghHl9KsIkhMZy7eLCUyQTB3NzDeZGdhC3YA0P6AGN4AH_oGqGagHpr4b2AcB0ggHCIBhEAEYArEJbAykrlNCaPiACgHYEwM&num=1&sig=AOD64_0yponkAgY51u83saT34i5ykkZGMQ&client=ca-pub-7825705102693166&adurl=http://www.hauppauge.com/linux)

[Learn more](https://www.cyberciti.biz/aclk?sa=l&ai=CupWQ5SYjWsr4EpPMpgOVi5uwAcH3nrRN_6ai2osGiZW8tIwJEAEgocuPAmDJBqAB6v3V5gPIAQaoAwHIAwKqBM0BT9BJ44KIHQvuzE8mpgyvq5epsMcRKcjEs2eGVE_8Hd297reXa5QWEcXg6qSO1R0OMi9Zw8_gTTz4O2uCQ003bK4KCJwpRk5DwG36uNsehQAA5-_41x5ZlsLOLTmgbcnLso7RR58pA0s_6ZAJl0tqzxwLjBTII45ytyJpz9BTieVTpPhPD5dNDFAM_LtmKXeNxwUDIJRgH6wOl3QqqLWbIWRPS-ewWgQXQoZunWClzZxTghHl9KsIkhMZy7eLCUyQTB3NzDeZGdhC3YA0P6AGN4AH_oGqGagHpr4b2AcB0ggHCIBhEAEYArEJbAykrlNCaPiACgHYEwM&num=1&sig=AOD64_0yponkAgY51u83saT34i5ykkZGMQ&client=ca-pub-7825705102693166&adurl=http://www.hauppauge.com/linux)

## Say hello bash-insulter

From the Github page:

> Randomly insults the user when typing wrong command. It use a new builtin error-handling function named command_not_found_handle in bash 4.x.

## Installation

Type the following git command to clone repo:  
`git clone https://github.com/hkbakke/bash-insulter.git bash-insulter`  
Sample outputs:
    
    
    Cloning into 'bash-insulter'...
    remote: Counting objects: 52, done.
    remote: Compressing objects: 100% (49/49), done.
    remote: Total 52 (delta 12), reused 12 (delta 2), pack-reused 0
    Unpacking objects: 100% (52/52), done.
    

Edit your ~/.bashrc or /etc/bash.bashrc using a text editor such as vi command:  
`$ vi ~/.bashrc`  
Append the following lines (see [if..else..fi statement](https://bash.cyberciti.biz/guide/If..else..fi) and [source command](https://bash.cyberciti.biz/guide/Source_command)):
    
    
    if [ -f $HOME/bash-insulter/src/bash.command-not-found ]; then
        source $HOME/bash-insulter/src/bash.command-not-found
    fi

Save and close the file. Login again or just run it manually if you do not want to logout:  
`$ . $HOME/bash-insulter/src/bash.command-not-found`

## How do I use it?

Just type some invalid commands:  
`$ ifconfigs  
$ dates`  
Sample outputs:

![An interesting bash hook feature to insult you when you type an invalid command. ](https://www.cyberciti.biz/media/new/cms/2017/11/bash-insulter-Insults-the-user-when-typing-wrong-command.jpg)

> _An interesting bash hook feature to insult you when you type an invalid command._

## Customization

You need to edit $HOME/bash-insulter/src/bash.command-not-found:  
`$ vi $HOME/bash-insulter/src/bash.command-not-found`  
Sample code:
    
    
    command_not_found_handle () {
        local INSULTS=(
            "Boooo!"
            "Don't you know anything?"
            "RTFM!"
            "Hahaha, n00b!"
            "Wow! That was impressively wrong!"
            "What are you doing??"
            "Pathetic"
            "...and this is the best you can do??"
            "The worst one today!"
            "n00b alert!"
            "Your application for reduced salary has been sent!"
            "lol"
            "u suk"
            "lol... plz"
            "plz uninstall"
            "And the Darwin Award goes to.... ${USER}!"
            "ERROR_INCOMPETENT_USER"
            "Incompetence is also competence"
            "Bad."
            "Fake it till you make it!"
            "What is this...? Amateur hour!?"
            "Come on! You can do it!"
            "Nice try."
            "What if... you type an actual command the next time!"
            "What if I told you... it is possible to type valid commands."
            "Y u no speak computer???"
            "This is not Windows"
            "Perhaps you should leave the command line alone..."
            "Please step away from the keyboard!"
            "error code: 1D10T"
            "ACHTUNG! ALLES TURISTEN UND NONTEKNISCHEN LOOKENPEEPERS! DAS KOMPUTERMASCHINE IST NICHT FÜR DER GEFINGERPOKEN UND MITTENGRABEN! ODERWISE IST EASY TO SCHNAPPEN DER SPRINGENWERK, BLOWENFUSEN UND POPPENCORKEN MIT SPITZENSPARKEN. IST NICHT FÜR GEWERKEN BEI DUMMKOPFEN. DER RUBBERNECKEN SIGHTSEEREN KEEPEN DAS COTTONPICKEN HÄNDER IN DAS POCKETS MUSS. ZO RELAXEN UND WATSCHEN DER BLINKENLICHTEN."
            "Pro tip: type a valid command!"
        )
     
        # Seed "random" generator
        RANDOM=$(date +%s%N)
        VALUE=$((${RANDOM}%2))
     
        if [[ ${VALUE} -lt 1 ]]; then
            printf "\n  $(tput bold)$(tput setaf 1)$(shuf -n 1 -e "${INSULTS[@]}")$(tput sgr0)\n\n"
        fi
     
        echo "-bash: $1: command not found"
     
        # Return the exit code normally returned on invalid command
        return 127
    }

## sudo insults

Edit the sudoers file:  
`$ sudo visudo`  
Append the following line:  
`Defaults insults`  
Or update as follows i.e. add insults at the end of line:  
`Defaults !lecture,tty_tickets,!fqdn,insults`  
Here is my file:
    
    
    Defaults	env_reset
    Defaults	mail_badpass
    Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
    ## If set, sudo will insult users when they enter an incorrect password. ##
    Defaults	insults
     
    # Host alias specification
     
    # User alias specification
     
    # Cmnd alias specification
     
    # User privilege specification
    root	ALL=(ALL:ALL) ALL
     
    # Members of the admin group may gain root privileges
    %admin ALL=(ALL) ALL
     
    # Allow members of group sudo to execute any command
    %sudo	ALL=(ALL:ALL) ALL
     
    # See sudoers(5) for more information on "#include" directives:
     
    #includedir /etc/sudoers.d

Try it out:  
`$ sudo -k # clear old stuff so that we get a fresh prompt  
$ sudo ls /root/  
$ sudo -i`  
Sample session:

![An interesting sudo feature to insult you when you type an invalid password.](https://www.cyberciti.biz/media/new/cms/2017/11/sudo-insults.jpg)

> _An interesting sudo feature to insult you when you type an invalid password._

## Say hello to sl

[sl is a joke software or classic UNIX](https://www.cyberciti.biz/tips/displays-animations-when-accidentally-you-type-sl-instead-of-ls.html) game. It is a steam locomotive runs across your screen if you type "sl" (Steam Locomotive) instead of "ls" by mistake.  
`$ sl`

![Linux / UNIX Desktop Fun: Steam Locomotive](https://www.cyberciti.biz/media/new/tips/2011/05/sl_command_steam_locomotive.png)

> _Linux / UNIX Desktop Fun: Steam Locomotive_

And, there you have it various ways to insult your users in your shell for fun. If you enjoyed this desktop/cli fun app, you may also like to use the following apps on Linux:
