
Description
-----------------------------------

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

Compile
-----------------------------------
	make tmote install,ID bsl, /dev/ttyUSBX