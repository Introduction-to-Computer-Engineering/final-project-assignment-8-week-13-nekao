# CPE 1040 - Introduction to Computer Engineering

## Assignment: Final Project

## Part II (Week 13, Assignment #8)

#### Week 13 - Oscilloscopes and serial protocols

### I2C warmup:
1. What are the disadvantages of the other two serial communication channels, UART and SPI, and how does I2C improve on them?
 - SPI is only intended for short distances, the biggest problem is the pin connection and the number of pins required. Making connections from multiple devices only slaved to one master.  UART is difficult to implent into your software if intended to do so.  This task eats up alot of data and slows the system down.  Where I2C improves in these areas begins with using only 2 wires and being able to connect to 1008 slave devices, the speed isnt as fast as SPI but gets the job done more efficently.
2. I2C is a two-wire serial communication channel. What are the two wires, SDA and SCL? 
 - SCL is a Clock Sigal, & SDA is a Data Signal.
3. What distinguishes the master and the slaves? 
 - The Clock signal being located in the master is the difference between the two.
4. How are the two types of protocol frames different?
 - the first being the Adress Frame, is where the master lets the slave know where the message needs to be sent triggering one or multiple frames that are 8 bit. The second one being Data Frames, the data first is sent to the SDA which is chosen by the master or slave dependings of the R/W bit was written or read.
5. What is the most appropriate trigger for capturing an I2C frame on the oscilloscope?
 - the appropriate trigger to go with first is the SDA trigger becasue of its intial falling edge.

### First steps with I2C:
I2C Read & Write Files:
- [Read File](i2cRead.js)
- [Write File](i2cWrite.js)

## section 1: Capturing I2C frame on oscilloscope
- Location of [Capture](Capture.jpg) of I2C frame. 
- Location of [SetUp](SetUp.jpg)

## (once link is opened to file, hit the download button to view the correct resolution of picture)
1. What frame did you capture?
- address frame
2. What does the I2C write function do when there is nothing connected?
- gives a blank scl sample reading when it goes from low to high.
- [Capture](writeSignal.jpg)
3. Is there a difference in what you capture if you write a number to one of the internal device addresses?
- much larger amount of data after handshake
- [Capture](writeToInternal.jpg)
- [File](writeInternalNumber.js)

## Section 2: Writing to Read 
Call to varinat 1.3 accelerometer: we dont have first varinat micro-bit, showed no data. 
- [Capture](1.3.jpg)
- [File](variant1.3.js)

Call to varinat 1 accelerometer: seems to be communicating with accelerometer.
- [Capture](variant1.jpg)
- [File](variant1.js)

Call to variant 2 accelerometer: call to variant 2 address 0x1E, seems to be communicating with either variant 2s accelerormeter or variant 1 magnetometer.
- [Capture](variant2.jpg)
- [File](variant2.js)

Signed single byte integers: 
- [Capture](signed.jpg)
- [File](signed.js)

Unsigned single byte integers: 
- [Capture](unsigned.jpg)
- [File](unsigned.js)

Scroll the values on the LED matrix?
 - Reading:

Can you get different Values from moving thr micro-bit around?

### links for the Oscilliscope Assignment 8
  - This write up is for the connection of the built-in function generator.
    - [Demo](http://imgur.com/gallery/hEh2QPw)
    
  - This write up is for the connection of the ossiliscope.
    - [Demo](http://imgur.com/gallery/7WLgX39)
   
  - This write up is for the one line program for the LED and oscilliscope connection.
    - [Demo](http://imgur.com/gallery/IUjgB4M)
    - [File](pws.js)
  
  - This write up is for the loop in the program that varies the duty cycle of the LED.
    - [Demo](http://imgur.com/gallery/I8iRtUu)
    - [File](pwCycle.js)
  
  - This write up is the servo connection also with the duty cycle of the LED being controled by the movement of the servo.
    - [Demo](http://imgur.com/gallery/RdFtBsm)
    - [File](servoOscilloscope.js)
 
 
 

  
