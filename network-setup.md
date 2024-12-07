Network Setup:

Devices:

- Router0: 1941

- Switches:
  - Switch0: 2960-24TT
  - Switch1: 2960-24TT

- PCs: 
  - PC0: 168.90.0.4
  - PC1: 168.90.0.5
  - PC2: 210.3.14.3
  - PC3: 168.90.0.3
  - PC4: 210.3.14.2

- Laptop0: 168.90.0.3

- Servers: 
  - Server0: 168.90.0.6
  - Server1: 210.3.14.5
  - Server2: 210.3.14.4

DHCP Configuration:

To configure DHCP on the router, I followed these steps:

To access the router configuration, I selected the router, switched to its CLI, and used the "enable" command followed by the "configure terminal" command to access configuration mode.
I then created the DHCP pool for Switch0 by executing the following commands in sequence:
 - ip dhcp pool First
 - network 168.90.0.0 255.255.0.0
 - default-router 168.90.0.1
 - dns-server 8.8.8.8
 - exit

Following this, I created a second DHCP pool for Switch1 in the same way by executing the following commands after reentering configuration mode:
 - ip dhcp pool Second
 - network 210.3.14.0 255.255.255.0
 - default-router 210.3.14.1
 - dns-server 8.8.8.8
 - exit

To ensure the router did not assign its own IP addresses from the pool, I excluded the following addresses within configuration mode as well, using the commands:
 - ip dhcp excluded-address 168.90.0.1
 - ip dhcp excluded-address 210.3.14.1

I then executed a final "exit" command to return to normal mode.

Next, I switched all end devices (PCs, servers, and laptop) to DHCP mode by accessing each device's Desktop tab > IP Configuration and selecting DHCP. I confirmed that all devices received correct IP addresses within the respective pools by hovering over the devices in Cisco Packet Tracer and performing ping tests between the two outlined in Task 1.