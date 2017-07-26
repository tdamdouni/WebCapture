# What is a virtualenv and hot to install it?

_Captured: 2016-12-03 at 22:34 from [tutorials.technology](https://tutorials.technology/tutorials/10-whats-is-a-virtualenv-and-how-to-install-it.html)_

# Introduction

Virtualenv is a tool that allows you to isolate your python application. It's very usefull when you have two application that conflicts on dependencies. Virtualenvs uses the PATH enviroment variable to switch python interpreter, so every time you need to know which virtualenv are you using try the command _which python_. When you have a default Ubuntu installation, _which python_ usually return the system python interpreter _/usr/bin/python_. Also virtualenvs solves the problems of the requirement of root privileges, since it will install all dependencies on your user home directory instead of system directories.

# Step 1: Requirements

Pip package manager is required:
    
    
    sudo apt-get install python-pip python-dev build-essential
    sudo pip install --upgrade pip
    

# Step 2: Installation

If you have sudo permissions, you can install it on the system with:
    
    
    sudo pip install virtualenv virtualenvwrapper
    

If you don't have permission try to install with _\--user_ option:
    
    
    pip --user install virtualenv virtualenvwrapper
    

Now if you are using bash, open the .bashrc of your home directory to add:
    
    
    export WORKON_HOME=$HOME/.virtualenvs
    export PROJECT_HOME=$HOME/Devel
    source /usr/local/bin/virtualenvwrapper.sh
    

If you are using zsh, add the exports to the .zshrc.

# Step 3: How to use it

Virtualenvwrapper helps to use and manage virtualenvs, it adds some helpful commands like:

  * mkvirtualenv project_name: it will create an empty virtualenv called _project_name_.
  * workon project_name: switch between or enters the _project_name_ virtualenv.
  * rmvirtualenv project_name: it will delete the virtualenv called _project_name_.
  * lsvirtualenv: lists all created virtualenvs.

Let's see an example:
    
    
    mkvirtual test_virtualenv_1
    workon test_virtualenv_1
    pip install requests
    pip freeze | grep requests
    

the output should be similar to:
    
    
    requests==2.11.1
    

Let's create another virtualenvs and check if requests was installed.
    
    
    mkvirtualenv test_virtualenv_2
    workon test_virtualenv_1
    pip freeze | grep requests
    

After execute _pip freeze | grep requests_ no output is expected. That's all, hope you learnt a new very usefull tool!
