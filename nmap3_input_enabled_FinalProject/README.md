# nmap3_input_enabled

An nmap python script using the python3-nmap library. 

Thank you to nmmapper on Github for the python3-nmap Python library! https://github.com/nmmapper/python3-nmap

Using this library, I was able to create a script that takes user input to decide which nmap function to use, as well as specify an ip or web address to target.

This is the final project for my UC Irvine Cybersecurity course. I hope you are able to use this script for your own projects, and continue adding more to it!

## SETUP

Paste into terminal

```git clone https://github.com/wangoloj/python3-nmap.git```

cd to python3-nmap directory

```cd ~/python3-nmap```

Install pip3 which manages packages in Python

```pip3 install -r requirements.txt```

Install nmap online

```apt-get install nmap (Linux)```

```choco install nmap (Windows, MUST BE ADMIN!!!)```

YOUR SCRIPTS NEED TO BE SAVED IN YOUR PYTHON3-NMAP DIRECTORY SO THAT THEY CAN CALL UPON THE NMAP3 FUNCTION

Example: ```C:\Users\uciuser\python3-nmap>```

Call upon your version of Python along with the script name to run it

Example: ```C:/Python310/python.exe c:/Users/uciuser/python3-nmap/nmap3_input_enabled.py```

```
#import nmap3 function to scan input from command line
import nmap3

#import json to help format data
import json

#Create variables to hold the values for the selected nmap function and target address
selection = input("Please select the nmap tool you would like to use: 1. dns_brute_script, 2. os_detection, 3. top10ports [Enter 1, 2, or 3]: ")
target = input("Please enter website address: ")

#use a variable called nmap to call upon the nmap3 library
nmap = nmap3.Nmap()

#create a while True loop to determine if a valid input was given, otherwise exit out of the program to avoid crashes and long loading times
#the results variable in this loop is used to store the raw json data from the nmap scan
while True:
    if selection == "1":
        results = nmap.nmap_dns_brute_script(target)
    elif selection == "2":
        results = nmap.nmap_os_detection(target)
    elif selection == "3":
        results = nmap.scan_top_ports(target)
    else:
        print("Please select 1, 2, or 3!")
        break
#use json.dumps to format the raw data stored in results, and use indent=4 to make it more legible
#store this formatted json into variable x
    x = json.dumps(results, indent=4)
    #use print to display the data
    print(x)
    break
```