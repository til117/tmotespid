Description
-----------------------------------

This project contains some templates and tutorials showing how to communicate 
between the motes and the PC. For this purpose we present two methods that depending on the requirements is better to use one or another. In the documentation you can find a comparatives of the two methods.


Motes
-----------------------------------

I have created three basic applications where you could find the basis to communicate
a mote with the PC using the serial port.

I. TestWriteReadSerialComm

	This application sends periodically a packet to the serial port and increments the 
	counter each iteration. To check the correct behaviour is needed to check the results
	on the PC. You should get a ramp (y=x).
	If the writing is enabled on the PC, the Leds will blink and show the (received value
	in binary) % 8.
	
	To sum up:
		Periodically sends -> nothing (Read mode)
		Periodically sends ; When a pck is received the leds blink (Write mode)
	
	It includes:
	- Serial communication
	- Serial message definition + Java class

	See TestWriteReadSerialComm README for more information or the documentation

	
II. TestSerialComm

	Every time the application receives a packet from the Serial port, the leds are shown 
	the received value in binary % 8. Then they increment the counter and sends the packet
	back to the PC with the new counter value.
	If the writing is enabled on the PC, the Leds will blink and show the (received value
	in binary) % 8
	
	To sum up:
		Reception of a packet from PC -> Increment counter -> Send a packet to the PC
		
	It includes:
	- Serial communication
	- Serial message definition + Java class
	
	See TestSerialComm README for more information or the documentation
	
III. TestHIL

	For this example, we have tried to simulate a Hardware In Loop, where we have a
	sensor and actuator scenario. But we can see them as receiver (actuator, read from PC), and
	the sender (sensor, write to the PC).
	
	The sensor is sending random values periodically to the PC, the PC compute something with the
	value (increment + 5, for instance) and sends the value to the actuator mote.
	When the actuator mote receives a packet, it shows the value in the LEDS and transmit the value
	to the sensor node through radio using the IEEE 802.15.4 standard protocol.
	
	It includes:
	- Serial communication
	- Serial message definition + Java class
	- Use of IEEE 802.15.4 (TKN15.4)	
	
	See TestHIL README for more information or the documentation
	

PC
-----------------------------------
We have implemented the same applications for LabView and Matlab. They are templates 
useful to start using this utility and communicate the motes with LabView and Matlab.

* LabViewFiles -----------------------------------

For this case, we have develop some SubVi:

	1. OpenSF: open the TCP/IP connection
	2. CloseSF: close the TCP/IP conenction
	3. ReadSF: read a packet from the TCP/IP connection created
	4. WriteSF: write a packet to the TCP/IP connection
	5. BuildPacket: create a packet to send to the mote. It requires a special structure
	6. ParsePacket: get the payload data from a received message

I. TestReadFromMote: This application only reads packet from the specified port

II. TestWriteToMote: This application writes packets to the specified port with
					 a given sample time
					 
III. TestMoteComm: This application sends a packet to the mote and waits until the 
				   mote replies, sending another packet
				   
IV. TestHIL: This applications involves two motes. We consider one mote connected to 
			 to the PC just for sending packet to the PC (port 9002), an ANOTHER mote
			 connected to receive packets from the PC (port 9003).
			 
V. TestController: This application simulates a scenario where the controller is implemented
					in the computer, which has more computational capabilites than the
					mote itself. This scneario a unique mote connected to the PC, which could
					be considered as a bridge between the process and the PC.
		 
See the README of each application for more information.

* MatlabFiles -----------------------------------

The matlab applications is divided in two main tools.
	1. testSerialApp: this is the application where we have all the useful and 
					  functions for the correct and excepted behaviour.
					  For installation follow the document0 "Communication PC to mote".
					  
					  *Tips:* if you have problems to compile the tinyos.jar, replace the enclosed
					  tinyos.jar which already includes the matlab java libraries required.
					  
    2. testSerialApp_gui: for simplicity we have created a Graphical User Interface. 
    				  with this interface it will be easy to control and manage the
    				  different options of the testSerialApp. 
    				  
See the README of the MatlabFiles folder or documentation for more indications

Troubleshot
-----------------------------------


    	