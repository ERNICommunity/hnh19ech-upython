# hnh19ech-upython

Session about Python on microcontrollers specifically for the ESP8266 microcontroller.

We'll be creating a virtual environment on our pc in order to work with Mycropython.

## Setting up the environment

### Install Python.

Most of the software tools used are developt in Python so we need to install it. So head over to the
 [Python](https://www.python.org/downloads/) download page.
 
Take into account that depending on the version of Python you've installed on your system `pip` should
be installed as well, if not, please make sure you also install it.
 
### Install Basic dependencies.

In order to create the virtual environment we need to install a library called `virtualenv`, so 
go to the command line and execute the following command.

```console
python -m pip install virtualenv
```

### Create the virtual environment.

As we mentioned before, we'll be using a virtual environment so for this we need to created on a 
specific directory, in this case we created the `hnh2019ech` directory.

After heading over the directory we need to execute the following command in order to create the
virtual environment which in this case will be called `venv`:

```console
python -m virtualenv venv
```

After executing this command a folder will be created within the folder `hnh2019ech`, so, you'll get
a structure like this:

```
hnh2019ech
    └──venv
```

### Activate the virtual environment.

In order to start working we need to activate the virtual environment, to do so, execute the following 
command:

- Linux 
  ```console
  source ./venv/bin/activate  
  ```

- Windows
  ```console
  .\venv\Scripts\activate
  ```
  
  **Note:** If you're using Windows powershell please add the `.ps1` extension on the command.
  
### Getting the tools on our environment.

Now let's install the libraries needed for flashing the firmware onto the microcontroller.

```console
pip install esptool
pip install adafruit-ampy
```

## Getting the board to run python.

In order to have python on the microcontroller we'll need to download latest firmware version from 
the [Micropython](http://micropython.org/download#esp8266) and let's flash the firmware.

The first step will be erasing the flash of the microcontroller.

  - Linux:
  ```console
  esptool.py --port /dev/ttyUSB0 erase_flash
  ```
  
  - Windows:
  ```console
  esptool.py --port COMX erase_flash
  ```
  

Now let's actually flash the firmware:

  - Linux:
  ```console
  esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect 0 esp8266-20190529-v1.11.bin
  ```
  
  - Windows:
  ```console
  esptool.py --port COMX --baud 460800 write_flash --flash_size=detect 0 esp8266-20170108-v1.8.7.bin
  ```
  
**Note:** 
- The `/dev/ttyUSB0` or the `COMX` are the actual port where the microcontroller is connected to
the pc.

- If you get a problem please, checkout the [troubleshooting](https://docs.micropython.org/en/latest/esp8266/tutorial/intro.html#troubleshooting-installation-problems)
 site from micropython.