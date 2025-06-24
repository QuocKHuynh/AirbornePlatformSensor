# AirbornePlatformSensor
Capstone project sponsored by Boeing
This is my own implmentation of an airborne platform sensor using a OPS243-C Doppler radar. 
I used an Arduino due to control operations of the OPS243-C, servo motor, bluetooth module, and SD card module. The circuit also utilizes a 12 V external battery source, step down voltage regulator to 5 V, and an LED for visual indication. The 12 V powers the sensor, then gets converted to 5 V to control the other components. 
In an infinite loop, the Arduino checks for bluetooth input, parses data from the sensor, then continues the algorithm decided by the bluetooth input to set the angle of the servo and radar. 
This code has 3 different algorithms:
1) Tracking algorithm: When an object is detected, mark that angle, then check +changeAngle, then check -checkAngle, then check + 2*changeAngle, then check - 2 * changeAngle. When an object is detected, the Arduino turns on the external LED to indicate that the algorithm is executing. 
2) Detection algorithm: When an object is detected, pause at the angle for some number of cycles and turn on the LED.
3) Sweeping algorithm: Continuously sweep for objects for some cycles at each angle. The number of cycles and degrees of change for each sweep is configurable by the user in the code. Report the number of detected objects at the end of each 180 to 0 or 0 to 180 sweep. Blink the LED each time an object is detected.
The actions and data is saved on an SD card for analysis post-flight.
This code utilizes UART and SPI communication protocols. 
