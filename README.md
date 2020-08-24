Concept behind Seeker is simple, just like we host phishing pages to get credentials why not host a fake page that requests your location like many popular location based websites.IPTRACK Hosts a fake website on **In Built PHP Server** and uses **Serveo** to generate a link which we will forward to the target, website asks for Location Permission and if the target allows it, we can get :

* Longitude
* Latitude
* Accuracy
* Altitude - Not always available
* Direction - Only available if user is moving
* Speed - Only available if user is moving

Along with Location Information we also get **Device Information** without any permissions :

* Operating System
* Platform
* Number of CPU Cores
* Amount of RAM - Approximate Results
* Screen Resolution
* GPU information
* Browser Name and Version
* Public IP Address
* IP Address Reconnaissance

**This tool is a Proof of Concept and is for Educational Purposes Only, IPTRACK shows what data a malicious website can gather about you and your devices and why you should not click on random links and allow critical permissions such as Location etc.**

## How is this Different from IP GeoLocation

* Other tools and services offer IP Geolocation which is NOT accurate at all and does not give location of the target instead it is the approximate location of the ISP.

* IPTRACK uses HTML API and gets Location Permission and then grabs Longitude and Latitude using GPS Hardware which is present in the device, so IPTRACK works best with Smartphones, if the GPS Hardware is not present, such as on a Laptop, Seeker fallbacks to IP Geolocation or it will look for Cached Coordinates.  

* Generally if a user accepts location permsission, Accuracy of the information recieved is **accurate to approximately 30 meters**, Accuracy Depends on the Device.

**Note** : On iPhone due to some reason location accuracy is approximately 65 meters.

## Templates

You can choose a template which will be used by seeker from these : 

* NearYou
* Google Drive (Suggested by @Akaal_no_one)
* WhatsApp (Suggested by @Dazmed707)
* Telegram

## Tested On :

* Kali Linux
* Termux


## Installation

### Kali Linux / Ubuntu / Parrot OS

```bash
Sudo apt-get install python3
sudo apt-get install php
sudo apt-get install ssh
git clone https://github.com/Mr-XxX01/IP-TRACK.git
cd IP-TRACK
chmod 777 install.sh
./install.sh
```
### Termux

```bash
pkg install python3
pkg install php
pkg install ssh
git clone https://github.com/Mr-XxX01/IP-TRACK.git
cd IP-TRACK
chmod 777 termux_install.sh
./termux_install.sh
```

## Usage

```bash
python3 IPTRACK.py -h

usage: IPTRACK.py [-h] [-s SUBDOMAIN]

optional arguments:
  -h, --help                              show this help message and exit
  -s SUBDOMAIN, --subdomain Subdomain 	  Provide Subdomain for Serveo URL ( Optional )
  -k KML, --kml KML                       Provide KML Filename ( Optional )
  -t TUNNEL, --tunnel TUNNEL              Specify Tunnel Mode [manual]

# Example

# SERVEO 
########
python3 IPTRACK.py

# NGROK ETC.
############

# In First Terminal Start IP-TRACK in Manual mode like this
python3 IPTRACK.py -t manual

# In Second Terminal Start Ngrok or any other tunnel service on port 8080
./ngrok http 8080

#-----------------------------------#

# Subdomain
########### 
python3 seeker.py --subdomain google
python3 seeker.py --tunnel manual --subdomain zomato

#-----------------------------------#

# Docker Usage
##############

# SERVEO
########
docker run -t --rm thewhiteh4t/seeker

# NGROK
#######

# Step 1
docker network create ngroknet

# Step 2
docker run --rm -t --net ngroknet --name seeker thewhiteh4t/seeker python3 seeker.py -t manual

# Step 3
docker run --rm -t --net ngroknet --name ngrok wernight/ngrok ngrok http seeker:8080
```

## Known Problems

* Services like Serveo and Ngrok are banned in some countries such as Russia etc., so if it's banned in your country you may not get a URL, if not then first READ CLOSED ISSUES, if your problem is not listed, create a new issue.

## Tutorial

| Tutorial | Link |
|-|-|
| Channel Youtube | https://youtu.be/wyQxy5cOIl8|

