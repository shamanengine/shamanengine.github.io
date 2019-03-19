# How to move your Python project from one device to another.

Let's assume you have created and developed Python project on device_1 and you want to make it work somewhere else device_2. In my case I have:
- created a project in my warm tube PyCharm on a laptop 
- made it run on Raspberry Pi
The routine is the same for all other cases. 

## Device 1:
During the creation of the proect in PyCharm you can set up a virtual env through GUI or add it in Project settings menu. If you are using something less user-friendly, e.x. text editors (or maybe even Vim and you do know how to exit it) for your development you can create virtual environment on your own from scratch:
```bash
# 1) Check that you have pip, it should have been installed with Python. 
pip --version # alternatively you can run pip3 everywhere instead of pip

# 2) Install virtualenv, either it will install venv or notify that it is already installed
pip install virtualenv

# 3) Go to your project folder and create a venv instance
cd projectfolder
pip -m venv venv # alternatively you can use >>> virtualenv venv
tree -L 3 # just to check the structure

# 4) Activate your venv, make a snapshot of dependencies, deactivate the env
source venv/bin/activate # or . venv/bin/activate
pip freeze > requirements.txt
deactivate
```
Now you should see your requirements.txt file in project folder with all the dependencies. That's all for device_1

## device_2
Just follow the steps 1-3 from device_1 if you don't have venv already setup, then run below
```bash
# Go to project folder, activate venv, fetch the dependencies, deactivate venv
cd projectfolder
source venv/bin/activate
pip install -r requirements.txt
deactivate
```

That should do the trick.
___

## P.S. If your life is not pathetic enough
Step nuber 2 may be a tricky part. If you invoke "virtualenv --version" and see command not found it doesn't necessary mean that you haven't installed virtualenv, it may be installed for your user, not the root user or there is no alias for "virtualenv" command. Thus "virtualenv --version" doesn't return anything. If that bugs you...
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

# 2.4) If do you want to contribute to your brain cancer development even more, welcome to the party
# https://stackoverflow.com/questions/31133050/virtualenv-command-not-found
```
