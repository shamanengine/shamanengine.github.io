# How to set up Raspberry Pi Zero W as a SOAP web-server
Raspberry Pi in general and Zero W don't have that much horsepower to run a heavy-weight web-server, so you may want to make your set up as optimal as possible.

## Installing Raspbian Lite
Raspbian Lite is pretty much Debian core + drivers + pretty generic software for Raspberry to run. That's it. No GUI, no office suite, no browser. This is very useful when you want to run a web-server, and just use log-console.
~0) Go here and buy Raspberry https://botland.com.pl/pl/399-raspberry-pi I am not getting payed by then, just like what folks do~
1) Go here and Download Raspbian Light image https://www.raspberrypi.org/downloads/raspbian/
2) Go here and download Etcher - easy to use tool to write images to your flash https://www.balena.io/etcher/ FYI, you can't just copy the .img file to the flash, you do need to use specific tool like Etcher to "burn" image to flash.
3) Plug your flash and launch Raspberry. Upon prompt type defauld 
Login: pi
Password: raspberry

To check that everything is fine:
```
pi@raspberrypi:~ $ su - pi
Password:
pi@raspberrypi:~ $
```
https://www.raspberrypi.org/documentation/configuration/security.md

sudo apt-get install libatlas-base-dev
