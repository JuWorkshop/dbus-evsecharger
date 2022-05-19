# dbus-open-evse
Integrate Open_EVSE charger into Victron Energies Venus OS

## Purpose
This script supports reading EV charger values from openEVSE base charger. Writing values is supported for "Enable charging"and  "Charging current" 

### Pictures
![Remote Console - Overview](img/1-DeviceList.png) 
![](img/2-EVSE.png)
![](img/3-Device.png)
![](img/4-VRM_Portal.png)
![](img/5-VRM_Devices.png)
![](img/6-VRM_Graph.png)

## Install & Configuration
### Get the code
Just grap a copy of the main branche and copy them to a folder under `/data/` e.g. `/data/dbus-evsecharger`.
After that call the install.sh script.

The following script should do everything for you:
```
wget https://github.com/JuWorkshop/dbus-evsecharger/archive/refs/heads/main.zip
unzip main.zip "dbus-evsecharger-main/*" -d /data
mv /data/dbus-evsecharger-main /data/dbus-evsecharger
chmod a+x /data/dbus-evsecharger/install.sh
/data/dbus-evsecharger/install.sh
rm main.zip
```
⚠️ Check configuration after that - because service is already installed an running and with wrong connection data (host) you will spam the log-file

### Change config.ini
Within the project there is a file `/data/dbus-evsecharger/config.ini` - just change the values - most important is the deviceinstance under "DEFAULT" and host in section "ONPREMISE". More details below:

| Section  | Config vlaue | Explanation |
| ------------- | ------------- | ------------- |
| DEFAULT  | AccessType | Fixed value 'OnPremise' |
| DEFAULT  | SignOfLifeLog  | Time in minutes how often a status is added to the log-file `current.log` with log-level INFO |
| DEFAULT  | Deviceinstance | Unique ID identifying the shelly 1pm in Venus OS |
| ONPREMISE  | Host | IP or hostname of on-premise Shelly 3EM web-interface |


## Usefull links
Many thanks. @vikt0rm, @fabian-lauer and @trixing project:
- https://github.com/trixing/venus.dbus-twc3
- https://github.com/fabian-lauer/dbus-shelly-3em-smartmeter
- https://github.com/vikt0rm/dbus-goecharger
