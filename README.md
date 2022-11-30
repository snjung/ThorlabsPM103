# ThorlabsPM103
This repository provides code to interact with a Thorlabs PM103 interface box via USB.

## Introduction
Thorlabs introduced a new power meter driver (TLPM.dll) instead of the formerly used NI-VISA-based driver (PM100D.dll). When installing the software-package, the new driver will be installed by default. There is the option to revert to the old PM100D driver with a [tool](https://www.thorlabs.com/software/MUC/OPM/v3.0/TL_OPM_V3.0_web-secured.pdf#%5B%7B%22num%22%3A326%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C28%2C359%2C0%5D) provided by Thorlabs. However, the new driver model is claimed to be more robust and more efficient and is therefore recommended.

Using the new driver model, I could not connect to the device via pyvisa and use standard commands like *IDN?
With the installation comes a library (***TLPM_64.dll***) that enabled to connect to the interface box. There is also a python library (***TLPM.py***) that can be used as a wrapper to simplify the dll-requests.

## Installation
It is advised to copy both the dll-file and the python library to the folder containing your own python scripts for interacting with the device. The TLPM python library is object-oriented and can be imported via `from TLPM import TLPM`
In TLPM.py, the dll-file gets imported by `self.dll = cdll.LoadLibrary("TLPM_64.dll")]`. I encountered errors when running code - probably when calling the script from a different working directory. Python seems to look for the file in the active working directory instead of the folder where the script is stored.
The Problem can be resolved by explicitely providing the address like `self.dll = cdll.LoadLibrary("C:/Users/sebastian.jung/Documents/GitHub/ThorlabsPM103/TLPM_64.dll")]`