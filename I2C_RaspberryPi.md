```
import smbus
import time


# setup

bus = smbus.SMBus(1)

argon_address = 0x05	


# Function

def SendNumber(input):
	bus.write_i2c_block_data(argon_address, 0 , input)
    return -1
    

def GetNumber():
    number = bus.read_byte(argon_address)
    return number
        
  
# Send the data to argon
# you can change the number, 1 for turning led on and 2 for turning it off
SendNumber([0,0,0,0,1])
print("Data sent!")

time.sleep(2)

number = GetNumber()
print("Confirmed, data from argon: ", number)
```
