# nmap3_automated

Thank you to nmmapper on Github for the python3-nmap Python library! https://github.com/nmmapper/python3-nmap

Using this library, I was able to create a script that takes a variable specified in the command line, which is then used to declare an ip or web address to target in an nmap scan.

The python script runs two separate nmap scans on the target, a dns brute script and top 10 ports scan. 

Ideally, this script can be automated, and scheduled to run at hourly or daily intervals.

The script outputs JSON data from scans to a logs folder.

For my next steps in this project, I plan to create a json visualizer, and identify trends in the data from the nmap scans.

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

Example: ```C:/Python310/python.exe c:/Users/uciuser/python3-nmap/automated.py```

You also need to use -t after the script name to add the argument

Example: ```C:/Python310/python.exe c:/Users/uciuser/python3-nmap/nmap3_automated.py -t www.megacorpone.com```

```
#import argparse to take target address from command line
import argparse

#use -h for help
#use -t to declare target address
argParser = argparse.ArgumentParser()
argParser.add_argument("-t", "--target", help="target address")
args = argParser.parse_args()

#create variable to hold value from argument
target = args.target

#import nmap3 function to scan input from command line
import nmap3

#import json to help format data
import json

#use a variable called nmap to call upon the nmap3 library
nmap = nmap3.Nmap()

#we will perform 2 different nmap scans and create seperate logs and JSON files
#the brute_script and top_ports variables in this loop are used to store the raw json data from the nmap scans

brute_script = nmap.nmap_dns_brute_script(target)
   
top_ports = nmap.scan_top_ports(target)

#import time to help create string to name file
import time
timestr = time.strftime("%Y%m%d-%H%M%S")

#CREATE A DIRECTORY TO EXPORT LOGS TO BEFORE RUNNING THE SCRIPT. POINT TO THEM USING THIS VARIABLE.

#FOR LINUX (use sudo to run the script)
#path = (r'/splunk/var/log/json_logs/') 

#FOR Windows (add your directory path) (use double slashes or an error message will pop up)
path = (r'C:\\Users\\uciuser\\python3-nmap\\json_logs\\')

#import os to help with creating path to your logs directory
import os

# the json file where the output must be stored
#uses os.path.join to add our path and date/time together to create the file
bs_file = open(os.path.join(str(path) + str(timestr) + "_dns_brute_script.json"), 'w')

#json.dump dns_brute_script data
json.dump(brute_script, bs_file, indent = 6)

bs_file.close()

# the json file where the output must be stored
#uses os.path.join to add our path and date/time together to create the file
tp_file = open(os.path.join(str(path) + str(timestr) + "_top_ports.json"), 'w')

#json.dump top_ports data
json.dump(top_ports, tp_file, indent = 6)

tp_file.close()
```