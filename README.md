# Oasis chiller
Python library to control the Solid State Oasis recirculating chillers for temperature control.

# Configuration and disclaimer
The Oasis is a recirculating chiller to control temperature and is made by the company Solid State Cooling Systems. The modern versions of this product are called [UC160-190](https://www.sscooling.com/product/uc160-190/). This code was made for the older Oasis 150 using the Oasis_150_Product_Manual_Rev_M27 manual but could work for the newer models as well, however, there are no guarantees, always check and compare the communication manual before use. Furthermore, this code was tested on an Oasis 150 that turned out to be broken. We could communicate with the device, but it did not change the temperature upon command. This was also not possible in manual mode. We presume that the code is functional and correct but lacks final proof. Our Oasis unit operates fully in Celcius, please check if your model is the same. 

# Get started
- Make sure [pyserial](https://pythonhosted.org/pyserial/) is installed.
- Connect the Oasis using a serial to USB cable.
- Make the Oasis ready for opperation according to the manufacturers instructions. 
- In a Python interpreter, import the module: `import Oasis`.
- Find the USB address of the Oasis: `Oasis_address = Oasis.find_address()` 
- The find_address() function returns the address in the format of `COMX` on Windows or `dev/ttyUSBX` on Linux. The address will also be printed. 
- If you use a serial to USB converter that has an FTDI chip inside, the find_address() function will also return the ID nubmer for the FTDI chip. This ID is unique to the chip and can be used to find the port quicker in the future by: `Oasis.find_address(identifier = ID)`
- Initiate the Oasis unit: `Oasis = Oasis.Oasis(Oasis_address, name='My_Oasis')`
- Now the Oasis is ready for operation.

# Operation
The Oais can be operated with 4 main functions:
- Set the temperature to a specified value in Celcius: `Oasis.set_temp(X)` 
- Read the set point in Celcius: `Oasis.read_set_point()`
- Read the actual temperature in Celcius: `Oasis.read_temp()`
- Check for errors on the Oasis and raise an error if the Oasis returns an error: `Oasis.check_error(verbose=True, raise_error=True)`
