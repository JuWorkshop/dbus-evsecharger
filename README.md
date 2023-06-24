# dbus-open-evse
Integrate Open EV charger with data from openWB into Victron Energy Venus OS

## Purpose
This script supports reading EV charger values from openWB. Writing values is supported for "Enable charging" and "Charging current" 

### Pictures
TODO

## Install & Configuration
### Get the code
Just grap a copy of the main branche and copy them to a folder under `/data/` e.g. `/data/dbus-evcharger-openwb`.
After that call the install.sh script.

The following script should do everything for you:
```
wget https://github.com/CommentSectionScientist/dbus-evcharger-openwb/archive/refs/heads/main.zip
unzip main.zip "dbus-evcharger-openwb-main/*" -d /data
mv /data/dbus-evcharger-openwb-main /data/dbus-evcharger-openwb
chmod a+x /data/dbus-evcharger-openwb/install.sh
/data/dbus-evcharger-openwb/install.sh
rm main.zip
```
⚠️ Check configuration after that - because service is already installed an running and with wrong connection data (host) you will spam the log-file

### Change config.ini
Within the project there is a file `/data/dbus-evcharger-openwb/config.ini` - just change the values - most important is the deviceinstance under "DEFAULT" and host in section "ONPREMISE". More details below:

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
- https://github.com/JuWorkshop/dbus-evsecharger
