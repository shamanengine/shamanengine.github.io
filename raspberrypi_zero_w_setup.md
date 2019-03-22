# How to set up Raspberry Pi Zero W as a Web server
Raspberry Pi in general and Zero W don't have that much horsepower to run a heavy-weight web-server, so you may want to make your set up as optimal as possible

## Installing Raspbian Lite
Raspbian Lite is not much more than Debian core + drivers + pretty generic software for Raspberry to run. That's it. No GUI, no office suite, no browser. This is very useful when you want to spare resources, and just use log-console as output

1. Download [Raspbian Light image](https://www.raspberrypi.org/downloads/raspbian/)

2. Download [Etcher](https://www.balena.io/etcher/) and flash the image to SD card. Eatcher is an easy to use tool to write images to your flash. FYI, you can't just copy the .img file to the card, you do need to use a specific tool like Etcher to "burn" the image to an SD card.

3. Plug your SD and launch Raspberry. Upon prompt type default Raspberry credentials:
- Login: pi
- Password: raspberry

4. Make basic configurations of your Raspberry.
```bash
sudo raspi-config
```
This will launch raspi-config application. Although the user interface is text-based, it is rather user-friendly. With its help you can manage:
- Wi-Fi
- Locale
- Time
- Change default password!!! 

Changing the default password is a minimum security requirement. Do at least this as the first thing on new installations. A friend of mine got hacked in no time and all his system got butchered. If you are even less irresponsible person than I - you can check this [Securing your Raspberry Pi] (https://www.raspberrypi.org/documentation/configuration/security.md) - a very useful article on improving your Raspberry security.

5. Update your system's software book of record and apply the latest upgrades. I like doing it separately and having a quick look at the log
```bash
sudo apt-get update
sudo apt-get upgrade
```

## Kicking off the Server

1. Install git
```bash
sudo apt-get install git
git --version  # to check the installation
```

2. Create a folder where you want to keep your projects, go there and clone the code
```bash
mkdir code  # where "code" is your folder for projects
cd code
git clone https://github.com/github_user/github_repository.git
```

3. Go to the project folder, install and activate virtual environment, fetch the dependencies, deactivate the environment
```bash
cd project_folder
python3 -m venv venv # alternatively you can use >>> virtualenv venv
source venv/bin/activate # or . venv/bin/activate
pip install -r requirements.txt
deactivate
```

For more details on this step, you can follow this article [How to move Python project from one device to another](https://github.com/shamanengine/shamanengine.github.io/blob/master/venv.md#how-to-move-python-project-from-one-device-to-another)

4. Make your server run while the virtual environment is activated, usually, it's something like this:
```bash
cd project_directory
source venv/bin/activate
python3 kickstarter.py
```

**_Note:_** I got this exception while trying to run my Web server
```bash
libf77blas.so.3: cannot open shared object file: No such file or directory
```
Fixed it with the below
```bash
sudo apt-get install libatlas-base-dev
```

I wish you luck, Ladies and Gentlemen
