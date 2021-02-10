# A Domoticz plugin for Brel Home Hub

* [Key features](#key-features)
* [Supported Brel devices](#supported-brel-devices)
* [Compatible hardware](#compatible-hardware)
* [Software requirements](#software-requirements)
* [Installation](#installation)
* [Check installed version](#check-installed-version)
* [Updating plugin](#updating-plugin)
* [Known issues](#known-issues)
* [Usage](#usage)
  + [Blinds and curtains](#blinds-and-curtains)
  + [Venetian blinds](#venetian-blinds)
  

## Key features
- Creates devices in Domoticz for every device configured in your Brel Home Hub
- Creates seperate devices for Position and Tilt
- Creates an extra virtual device for controlling áll your devices at once
- Specify default Position and Angle for your devices' Open and Close buttons


## Supported Brel devices
The plugin supports and is able to controll the following devices:
- Bi-Directional devices

The plugin doesn't work with:
- Unknown

## Compatible hardware
Most systems capable of running domoticz and has a version of python3 available should be able to run the plugin.
- Tested on Linux [Synology NAS] only

## Software requirements:
1. Python version 3.5.3 or higher, 3.7.x recommended. 
2. Domoticz compiled with support for Python-Plugins. 
3. Upgraded pip.
4. You need the pycrypto Python-module.

## Installation:
### 1. Clone Brel plugin into domoticz plugins-directory:
```shell
  $ cd domoticz/plugins/
  $ git clone https://github.com/superjunky/Domoticz-Brel-Plugin.git Domoticz Brel Plugin
```

### 2. Update pip:
```shell
  $ pip3 install -U pip
```

### 3. Install pycrypto
The plugin uses the pycrypto python module ([`https://pypi.org/project/pycrypto/`](https://pypi.org/project/pycrypto/))

```shell
  $ pip3 install pycrypto
```

### 3.1 Let Domoticz know about the pycrypto module
Domoticz may not have the path to the pycrypto library in its python environment.
In this case you will observe something starting like that in the log:
* failed to load 'plugin.py', Python Path used was
* Module Import failed, exception: 'ImportError'

To find where pycrypto is installed, in a shell:
```shell
  $ pip3 show pycrypto
```
The Crypto directory should be present in the directory indicated with Location.

when you have it, just add a symbolic link to it in Domoticz-Tuya-Thermostat-Plugin directory with ```ln -s```.
Example:
```shell
  $ cd ~/domoticz/plugins/Domoticz-Tuya-Thermostat-Plugin
  $ ln -s /home/pi/.local/lib/python3.5/site-packages/Crypto Crypto
```

### 4. Restart domoticz and enable Brel Home Hub from the hardware page
Don't forget to enable "Allow new Hardware" in the Domoticz settings page.

## Check installed version
To find the current version of the plugin and modules:
```shell
  $ cd domoticz/plugins/Domoticz-Brel-Plugin
  $ python3 plugin.py version
```

## Updating plugin
To update the plugin to the newest version, stop domoticz, enter the plugin directory, pull the latest changes from git and restart domoticz:
```shell
  $ cd domoticz/plugins/Domoticz-Brel-Plugin
  $ git pull
```

## Known issues
None so far.

## Usage
Lights and devices have to be added to the gateway as per Brel's instructions, using the official Brel app.

### Blinds and curtains
Domoticz sets the position of a curtain as a percentage between 0 (fully open) to 100 (fully closed). You need to set the maximum posistion of the curtain before using Domoticz. Please refer to the instructions from Brel on how to set the maximum position of a curtain. 

### Venetian blinds
Besides the position, Domoticz sets the angle of a venetian blind in degrees. A percentage between 0 is converted by the plugin into degrees between 0 and 180. To open your blinds, set the angle to 50% (which translates to 90 degrees).
