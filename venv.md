# How to move your Python project from one device to another.

Let's assume you have created the project in your warm tube PyCharm (Device 1) on a laptop and you need to make it work somewhere else. In my case it was Raspberry Pi(Device 2), but the routine is the same for all other cases. 

## Device 1:
During the creation of the proect in PyCharm you can set up a virtual env through GUI during project creation/ Project settings menu. If you are using something else instead of PyCharm, e.x. text editors or else for your development, you can create virtual environment on your own from scratch:
```bash
# 1) Check that you have pip, it should have been installed with Python. Alternatively you can run pip3 everywhere instead of pip
pip --version

# 2) Run this to install virtualenv, either it will install virtualenv or notify that it is already installed
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
After these activities, you should see your requirements.txt file in project folder with all the dependencies. That's all for Device 1

```bash
# == YOU DON'T NEED THIS, I WARNED YOU ==
# 2.0) Check that you have installed virtualenv
virtualenv --version

# Here comes the tricky part
# If command not found it doesn't necessary mean that you haven't installed it, it may be installed for your user, not the root user or there is no alias for "virtualenv" command. Thus "virtualenv --version" doesn't return anything
# 2.1) If you want to be a ruler of your system then instead of 2) run this
sudo pip install virtualenv

# 2.2) Or if you have already run 2), and do want to be like 2.1) run this
pip uninstall virtualenv
sudo pip install virtualenv

# 2.3) If previous step doesn't satisfy your needs, you can try this
pip uninstall virtualenv
sudo /usr/bin/easy_install virtualenv

# 2.4) If you want to contribute to your brain cancer development evn more, welcome to the party
# https://stackoverflow.com/questions/31133050/virtualenv-command-not-found
# == unless you are a perfectionist or freak, which are the same at the core ==
```

## Device 2
Just follow the steps 1-3 from Device 1 if you don't have venv already setup, than run below
```bash
# Go to project folder, activate venv, fetch the dependencies, deactivate venv
cd projectfolder
source venv/bin/activate
pip install -r requirements.txt
deactivate
```

That should do the trick.
