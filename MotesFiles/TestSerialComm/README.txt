
Description
-----------------------------------
This program involves reading and sending from the serial port. The program
is event-driven by the reception of a packet through the serial port.

When we receive a packet inot the serial port, an event is generated, UartReceive.receive, 
In this function if the packet length is equal to the expected, we blink the LEDs
according to the counter value that we have received. Then we increase the 
counter by adding 1 unit, and we send the packet back to the PC.