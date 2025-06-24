# citron.systems
citron data systems is a super simple, cheap, realtime, remote, open source data logger for race cars.  

## Pieces

### [can-client](https://github.com/Citron-Data-Systems/can-client)
It runs a minimal embedded linux image which runs only an erlang VM and is responsible for collecting data on the CAN bus and rendering it to the screen and sending it to the server. The can client is an application built on top of [nerves](https://nerves-project.org/). 

The hardware involved is just a raspberry pi, a cheap [MCP2515 board](https://www.amazon.com/WWZMDiB-Converter%EF%BC%8C3PCS-MCP2515-Receiver-Controller/dp/B0BVH43P9L) and an (optional) screen. You can run it in headless mode if you already have a dashboard and you just want wireless telemetry. Or you can just run the dashboard and omit the network if you just want a dashboard. 

During our races we stick a hotspot in the car - either a dedicated one or an old phone with a data plan will work. For just sending CAN traffic, the throughput requirements are not high. 


### [citron.systems](https://citron.systems)
lives on the internet. It hosts a visualization app and the realtime pubsub system that handles signals from the car. 

You give it a dbc definition which describes the signals on your CAN bus that you want to collect. All those signals are then sent to the server to be visualized. It doesn't matter which ECU you have as long as you can [find or create a DBC file](https://www.csselectronics.com/pages/can-dbc-file-database-intro) that describes the traffic on your bus. 


## Roadmap
### Software
* Predictive Lap timer
* Better offline support + full fidelity logging on the can-client. 
* Live video 
  
### Hardware
* PI Hat with an MCP2515, power supply, and GPS. This would make everything foolproof.
