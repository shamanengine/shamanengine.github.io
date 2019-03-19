# How to move Python project from one device to another

Let's assume you have created and developed Python project on Device 1 and you want to make it work somewhere else Device 2. In my case I have:
- created a project in my cozy PyCharm IDE on a laptop 
- made it run on Raspberry Pi

But the routine is the same for all other cases. 

## Device 1:
During the creation of the project in PyCharm you can set up a virtual env through GUI or add it in the Project settings menu. If you are using something less user-friendly, e.x. text editors (or maybe even Vim and you know how to exit it) you can create a virtual environment on your own from scratch:
```bash
# 1) Check that you have pip, it should have been installed with Python. 
pip --version # alternatively you can run pip3 everywhere instead of pip

# 2) Install virtualenv, either it will install venv or notify that it is already installed
pip install virtualenv

# 3) Go to your project folder and create a venv instance
cd project_folder
python3 -m venv venv # alternatively you can use >>> virtualenv venv
tree -L 3 # just to check the structure

# 4) Activate your venv, make a snapshot of dependencies, deactivate the env
source venv/bin/activate # or . venv/bin/activate
pip freeze > requirements.txt
deactivate
```
Now you should see your requirements.txt file in project folder with all the dependencies. That's all for Device 1

## Device 2
Just follow the steps 1-3 from Device 1 if you don't have venv already set up, then run below:
```bash
# Go to the project folder, activate venv, fetch the dependencies, deactivate venv
cd project_folder
source venv/bin/activate
pip install -r requirements.txt
deactivate
```

That should do the trick.
___

## P.S. If your life is not pathetic enough
Step number 2 may be a tricky part. If you invoke "virtualenv --version" and see command not found it doesn't necessarily mean that you haven't installed virtualenv, it may be installed for your user, not the root user or there is no alias for "virtualenv" command. Thus "virtualenv --version" doesn't return anything. If that bugs you...
```bash
# You don't need this, unless you are a perfectionist or freak, which are the same at the core
# 2.0) Check that you have installed virtualenv
virtualenv --version

# 2.1) If you want to be a ruler of your system then instead of 2) run this
sudo pip install virtualenv

# 2.2) If you have already run 2), and do want to be like 2.1) run this
pip uninstall virtualenv
sudo pip install virtualenv

# 2.3) If previous step doesn't satisfy your needs, you can try this
pip uninstall virtualenv
sudo /usr/bin/easy_install virtualenv
```

There is a chance that while trying to execute 'python3 -m venv venv' you will run into something like this: 
*The virtual environment was not created successfully because ensurepip is not
available. On Debian/Ubuntu systems, you need to install the python3-venv package using the following command.

    apt-get install python3-venv*



*If do you want to contribute to your brain cancer development, even more, ~~welcome to the party~~*
https://stackoverflow.com/questions/31133050/virtualenv-command-not-found
