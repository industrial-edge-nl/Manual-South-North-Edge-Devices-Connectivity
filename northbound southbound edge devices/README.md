# Northbound southbound edge devices
Connecting edge devices to connect to a cloud service or do centralized dashboarding.
[Official documentation](https://github.com/industrial-edge/Shopfloor-to-Cloud-Connectivity#network-architecture)

## Overview
![Overview](files/northBoundSouthbound.jpg)


### Setup

- Cloud
  - Connected to PORT 2 on edge device.

- Northbound edge device
  - Uses Port 1 for Southbound connection
  - Uses Port 2 for cloud connection
  - Applications
    - Dataservice - Saves data from southbound device in database      
    - Flow creator - Checks if data is flowing - for debugging      
    - IE Databus - Is used as data channel - MQTT broker      
    - IE MQTT Connector - Connects to the IE Cloud Connector of southbound device
      

- Southbound edge device
  - Uses Port 1 For Northbound connection
  - Uses Port 2 for OT level Connection
  - Applications    
    - IE Cloud Connector - Sends incoming data to another channel for northbound device to listen to    
    - Simatic s7 Connector - Connects to the PLC and publishes data over the databus
    - IE Databus  - Is used as data channel - MQTT broker      
    - Flow Creator - Checks if data is flowing - for debugging
      
- OT Level PLC
  - [Uses Tia Tank sample application](https://github.com/industrial-edge/miscellaneous#tank-application)

# Get started

## Networks
  - OT-South network 192.168.0.x/24 range
  - South-North network 192.168.1.x/24 range
  - North-Cloud network 192.168.2.x/24 range

## OT - Level
  Run Tia tank project on PLC SIM Advanced, or use a real PLC - Use a 1500 plc [Link Tia Portal Project](https://github.com/industrial-edge/miscellaneous#tank-application)  Or use your own project.  
  Give this PLC ip adress in range of the OT-South network, for example 192.168.0.10.

## Southbound - Level
  install the required apps:
- IE Cloud Connector 
- Simatic s7 Connector 
- IE Databus 
- Flow Creator 

- Give the Southbound-Device Port 2 ip adress in range of the OT-South network, for example 192.168.0.11
- Give the Southbound-Device Port 1 ip adress in range of the South-North network, for example 192.168.1.10



