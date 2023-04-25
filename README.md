# MAKE SURE YOU HAVE A WORKING PI-STAR CONFIGURATION BEFORE PROCEEDING.

It's beyond the scope of this document to help you configure your pi-star machine.

---

### These files have been modified for use with pi-star

* systemd/logtailer.service should run logtailer.py as root (required to run properly)
* created the ipv[4|6].fw files to add the firewall rules needed to MMDVMDash to allow access
* modified the scripts/DMRIDUpdate.sh script to use a better server, run as mmdvm and save the output to the MMDVMDash directory
* modified the html/index.html file to show "F" instead of "C" on the sysinfo tab (see note 1)
  * note 1: If you want to view the CPU temp in celcius, then change "F" back to "C" in the html/index.html file (around line 265)
otherwise, you're going to have to do a little editing in one of the python libraries to convert celcius to farenheit
    1. Make the disk rw by typing (rpi-rw)
    2. Become root by typing (sudo su)
    3. Change to the /usr/lib/python3/dist-packages/psutil directory (cd /usr/lib/python3/dist-packages/psutil)
    4. Edit the _pslinux.py file (nano _pslinux.py)
        a. Scroll down 1200 lines or so until you reach a section that shows "# --- sensors"
        b. Look for the line that says "current = (float(cat(path)) / 1000.0"  This should be around line 1210 or so
        c. Change it to read "current1 = (float(cat(path)) / 1000.0" and press enter
        d. USE SPACES to move the cursor until it's under the "c" from the line above
        e. Add "current = float(current1 * 1.8 + 32)


#### DO NOT FORGET!!!!!

* Edit the data/TG_List.csv file to reflect the talkgroups that you have enabled on your pi-star
* Edit the html/js/config.js file as described in [README-original.md](README-original.md).

#### IN PROCESS

* Try to hack together a simple install script

#### CREDITS
* This repo is based on the work of [@dg9vh](https://github.com/dg9vh) from his [MMDVMDash-Websockets repo](https://github.com/dg9vh/MMDVMHost-Websocketboard).
* logtailer.py is based on the work of [http://shzhangji.com/blog/2017/07/15/log-tailer-with-websocket-and-python/](http://shzhangji.com/blog/2017/07/15/log-tailer-with-websocket-and-python/).

