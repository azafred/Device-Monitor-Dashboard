# Device-Monitor-Dashboard
Python script to generate material design html report of devices' online/offline status. A cheap/fun reporting solution.
This can be used for for servers, networking equipment, IOT devices, anything that's "pingable".  
Supports:
 - Linux
 - Windows
 - Raspberry Pi

Live Demo: https://circa10a.github.io/monitor/

## Changelog
 - (5/27/2017) - Please see https://github.com/shaggyloris/Device-Monitor-Dashboard for extended functionality.
   - Integrated SQLite DB, all controlled via web UI, API functionality to return JSON.
 - (5/6/17) Added validation of OS for script to run
 - (2/26/17) Update Easy Install to automatically install packages
 - (2/25/17) Added support for vertically scrolling table, adjusts circle size if on mobile device.
 - (2/24/17) Combined ping function to single file, added ability to check other ports. Also converted script to be more in line with python norms. Table rows now act as hyperlinks to address listed and will auto detect port if specified.
 - (2/20/17) Updated noty,jquery, notifications UI, mobile UI
 - (2/18/17) Added support to build custom docker container
 - (2/4/17) Easy Install script now supports Node.js, update wheel color
 - (2/3/17) Change status from online/offline text to colored orb indicators

## Easy Install
`bash -c "$(curl -sL https://raw.githubusercontent.com/circa10a/Device-Monitor-Dashboard/master/install.sh)"`
- Either Node.js or Apache and Python required for Easy Install
- Tested with Ubuntu 16.04 / Apache 2.4.18 / Node.js 4 / Python 2.7
- Follow the prompts!

## Usage
- Have a text file with hostnames or ip addresses (optional: if port is desired seperate by comma. example: www.google.com, 80)
- Update the python script (variable at the top) with the path/name of your file with hostnames and output file path.(default hostames= hostnames.txt   default output= index.html)
- Run `python report.py`
- Ensure that you place the output HTML file in the project directory so it can find its web dependencies

## Automation
- Setup a web server
- Install a new cron job to run the report periodically `cd $path/to/project_directory/ && python report.py &> /dev/null`
- Set output path in python script to write out html report to web serving directory such as `/var/www/html`
- The page will automatically refresh every 60 seconds to reflect the new report generated by cron

## Docker!
- `git clone https://github.com/circa10a/Device-Monitor-Dashboard.git` 
- `cd Device-Monitor-Dashboard`   
- Edit your hostnames.txt file add your website, servers, switches, devices, etc.  
- `docker build -t myrepo/monitor .`  
- `docker run --name device-monitor -d -p 80:80 myrepo/monitor` 
```diff
- Known issue: Docker for Mac pings any address and returns success giving false results.
```
##Screenshots
![alt text](http://i.imgur.com/8BjmGyO.png)
![alt text](http://i.imgur.com/iRNNMkV.png)
