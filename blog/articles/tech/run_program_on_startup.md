# Several ways to run your program upon startup
## Approach 1 - editing rc.local

```bash
# Edit rc.local file and put what you want to run there
sudo nano /etc/rc.local

sudo source /home/pi/code/4inarow/venv/bin/activate &
sudo python3 /home/pi/code/4inarow/kickstarte.py &
exit 0 # this should be already there, keep it at the end of the file always!
```
If your program runs continuously (runs an infinite loop) or is likely not to exit, you must be sure to fork the process by adding an ampersand (“&”) to the end of the command, like:

sudo python /home/pi/sample.py &

The Pi will run this program at bootup, and before other services are started.  If you don’t include the ampersand and if your program runs continuously, the Pi will not complete its boot process. The ampersand allows the command to run in a separate process and continue booting with the main process running.

Now reboot the Pi to test it:

sudo reboot

## Approach 2 - editing rc.local
