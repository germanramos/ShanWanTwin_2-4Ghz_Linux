# ShanWanTwin_2-4Ghz_Linux
Userspace script to split controller input for the Shanwan Wireless Twin controllers (2563:0555)

## Requirements
- Python 3
- python-uinput module with one of the following methods:
  - `sudo apt install python3-uinput`
  - `sudo python3 -m pip install python-uinput`
- Supported controller. You can find it using `dmesg` and applying a grep pattern `'(?<=2563:0555\.\d{4}: input,)\w{6}\d'`
   - Example: `dmesg | grep -oP '(?<=2563:0555\.\d{4}: input,)\w{6}\d'`

## Usage

`sudo ./start_shanwan.sh`

or if you now your hidraw device. Example with 5:

`sudo python3 shanwan-joystick.py /dev/hidraw5`

## NOTE

When using this script, /dev/input/js1 and js2 will be created and they will be fully functional.
However, the original js0 will still be there.
When you press a button of any controller, an event will be throw for (js0 and js1) or (js0 and js2) 
This will be anoying when configuring MAME input. You can edit the cfg file to remove the js0 event.
I add the MAME default.cfg for your convenience
