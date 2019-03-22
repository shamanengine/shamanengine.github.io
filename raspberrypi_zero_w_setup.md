# How to set up Raspberry Pi Zero W as a SOAP web-server
Raspberry Pi in general and Zero W don't have that much horsepower to run a heavy-weight web-server, so you may want to make your set up as optimal as possible.

## Installing Raspbian Lite
Raspbian Lite is as much as Debian core + drivers + pretty generic software for Raspberry to run. That's it. No GUI, no office suite, no browser. This is very useful when you want to run a web-server, and just use log-console.
1. ~~Go here and buy Raspberry https://botland.com.pl/pl/399-raspberry-pi~~ I am not getting payed by then, just like what folks do
2. Go here and Download Raspbian Light image https://www.raspberrypi.org/downloads/raspbian/
3. Go here and download Etcher - easy to use tool to write images to your flash https://www.balena.io/etcher/ FYI, you can't just copy the .img file to the flash, you do need to use specific tool like Etcher to "burn" image to flash.
4. Plug your flash and launch Raspberry. Upon prompt type defauld 
Login: pi
Password: raspberry
5. Make basic configurations of your Raspberry.
```sudo raspi-config```
This will launch raspi-config application. Although the user interface is text based, it is rather user-friendly. With it's help you can manage:
- Wi-Fi
- Locale
- Time
- Change default password!!! 

Changing default password is a minimal security requirement. Do at least this as a first thing on new instalations. A friend of mine got hacked in no time and all his system got butchered. If you are even less irrisponsible than you can go here https://www.raspberrypi.org/documentation/configuration/security.md - a very usefull article on improving your Raspberry security.

6. Update your system's software book of record and apply latest upgrades. I like doing it separately and having a quick look at the log
```
sudo apt-get update
sudo apt-get update
```
7. Install git
```
sudo apt-get install git
git --version  # to check the instalation
```

## Kicking off the Server
1. Most probbably without this library your app-server won't kick-start
```sudo apt-get install libatlas-base-dev```
2. 
```git clone https://github.com/shamanengine/shamanengine.github.io.git```

To check that everything is fine:
```
pi@raspberrypi:~ $ su - pi
Password:
pi@raspberrypi:~ $
```
https://www.raspberrypi.org/documentation/configuration/security.md


