# ELN-Computercraft-multiple-power-supply-managment-software.
This is a program that uses a computercraft computer to dynamically switch loads from the Electrical age mod between multiple power sources (nodes) usefull for combining weaker power sources into one even more powerful one. especially if your power sources are already at the maximum tier. 


This program aims to monitor multiple power sources (nodes) and dynamically switch between them. This is to basically allow you to combine multiple weaker power sources in to one stronger one. 

It switches based off of a health and priority system. Each update tick, It will calculate the health of each node. And then figure out how much of an impact would each load would have on a particular node. It then uses this information the decide which node to place each load.

This program is designed to communicate with a switch completely through wireless transmitters and receivers. When setting up, make sure that all components are in range and that there is nothing causing interference. 

--priorities

There is also a priority system labeled 0-6.
 There are five priorities, 1-5 where the higher the value, the more aggressive the program will be on this load. Keeping it in the healthier node more often. If heath drops too low, then a lower priority load will be cut. 

0 will be default. This will be the value you assign loads you are indifferent towards. If a load is detected without any info, this will also be its first value

6 is custom. A load marked with this value will have its own set of weights unique to itself.

--weights

To decide what to do with each load, the current conditions are compared to the priority value. Each priority has three weights

Switch threshold-If a node’s health exceeds this threshold compared to the node it is currently attached to, then It will switch towards this node.

Cut threshold- If the health of the node drops below this point (and there is no reasonable node to switch towards) then the load is cut entirely.

Share threshold - This one may be split into multiple thresholds or cut entirely, It will be to decide whether to split a load across two or more nodes. I currently don’t know how to implement this yet.

Override threshold - This one will only be implemented if i decide to code the GUI. if something is set to stay on, and if this threshold is reached (health becomes too low to maintain manual settings) it will revoke the manual settings for that load





--settings

This program will use multiple files to configure how it behaves. You can use define and name both the nodes and loads. Naming is not necessary, it only exists to help with the GUI that may or may not be implemented. There is no reasonable limit to amount of nodes or loads that could be defined. That said, processing limitations may make you not want to go above a certain amount. All settings are given in the settings folder each different file carries a different type of settings.  

//wireless settings
Each type of data is given a name you define in the name of the transmitters/receivers. This is a surname shared by all transmitters of this type. The name should be followed by 1-2 numbers each separated by a space, this is info is used to go to a specific transmitter/receiver. 
Ex: 15KWSwitch 0 1

“15KWSwitch” is the sub name, while the first number is the number of the node that is is involved with, while the second number is the load the switch is involved with. This’ll be transmitted to a receiver that controls a relay in the switch. So turning this signal on will connect load 1 to node 0.

You don’t place the numbers in the settings, just the subname. You later define how many nodes/loads in another setting and they are given automatically. This is so you’ll name the wireless components correctly.

//switch settings
This’ll carry the custom names of the nodes and loads. It also carries the threshold values as well as the ones for the custom loads. 
