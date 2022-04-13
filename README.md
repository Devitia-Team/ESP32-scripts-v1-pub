# Cloning the ESP32

## **1** - Environment Setup

Flashing and writing to the ESP32s requires the following softwares (versions in parentheses work at the time of writing this):

- Python (3.10) from https://www.python.org
- esptool (3.3) from pip: With python installed, open powershell as administrator. Run the command `pip install esptool`. Follow any prompts and wait for the install to complete.
- Node.js (17.9.0) from https://nodejs.org/en/
- Chocolatey (installed during Node.js install)
- CP210x USB to UART Driver from https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers
- VS Code (1.66.2) from https://code.visualstudio.com
- PyMakr (1.1.18) extension for VS Code, from the VS Code extension manager

Note: It is recommended that you install the softwares in the order listed.

Once the above softwares are installed make sure all project files are in the same directory.

## **2** - Flashing Micropython to the ESP 32

Flashing MicroPython to the ESP requires first-time setup, but once set up can be done by running the command `./flash_py.bat`.

In your project folder, open the file 'flash_py.bat'. Within this file is 2 commands, and in those commands are 2 terms which may need to change depending on your PC.

1. Replace 'C:/python310/site-packages/esptool.py' with the location of esptool. The base python folder will be different if your version of python is different.
2. Replace 'com3' with the ESP32's com number. Find this by opening Device Manager on your computer. Connect an ESP32 via USB and watch for the new device to appear. If the UART to USB Driver is installed properly, the ESP32 is assigned a COM number, shown at the end of the device name in. The port number will also change depending on which USB port it is connected to. Keep track of this number.

Save and close the file. It can now be used to flash micropython to the ESP32. In a command prompt, navigate to the folder containing 'flash_py.bat'.

## **3** - Writing to the ESP 32

Open the project in VS Code. PyMakr options will show on the bottom bar to the left. Change Pymakr's settings by clicking 'All Commands', which will reveal a menu from the top center. Select 'Pymakr > Global Setting'. This will open a json file. For now, we want to change 2 fields. Replace the "py_ignore" field with the following:

```
"py_ignore": [
  "pymakr.conf",
  ".vscode",
  ".gitignore",
  ".git",
  "project.pymakr",
  "env",
  "venv",
  ".idea",
  "flash_py.bat",
  "esp32-20220117-v1.18.bin"
],
```

And replace the "autoconnect_comport_manufacturers" field with the following:

```
"autoconnect_comport_manufacturers": [
  "Pycom",
  "Pycom Ltd.",
  "FTDI",
  "Microsoft",
  "Microchip Technology, Inc.",
  "1a86",
  "Silicon Labs"
]
```

Save this file and feel free to close it.

Set the ESP 32's Bot ID in 'config.txt'. In the bottom left, click 'Upload Project.' The ESP32 will auto run after uploading the project files.
