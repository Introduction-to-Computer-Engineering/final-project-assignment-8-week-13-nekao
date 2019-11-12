# CPE 1040 - Introduction to Computer Engineering

## Assignment: Final Project

## Part II (Week 13, Assignment #8)

#### Week 13 - Oscilloscopes and serial protocols

### Oscilloscope warmup:

   1. Watch the first 4 oscilloscope videos [referenced below](#oscilloscopes).
   2. Take a look at the Rigol 1000 Series oscilloscopes documentation site to see what resources you have in case you need mmore in-depth knowledge.
   3. The oscilloscope shows _continuous varying signals_ that it detects at the tips of its _probes_. The probe has a two wires: _signal_ (red or central probe), and _ground_ (black or outside wire). _Remember that voltage is a **relative** potential, so, unless you connect the ground, which serves as the **reference level**, you will get garbage._
   4. Connect a Rigol probe to Channel 1.

### Visualize simple continuous signals:

   1. Visualize the following signals, using the **Auto** regime and default settings (trigger on a rising edge on CH1). For each signal, take a **video** of the setup (the source wire and connection of the oscilloscope probe) and the display of the oscilloscope, while varying one of the signal properties (wave shape, frequency, amplitude) using the controls of the source. 
 
READ.ME- Write up one sentence in the [README](README.md), enough to be able to insert a link to the video.

### Signals:
1. Configure the **OUT** of the built-in function generator on the workstation with whatever function you want. _Remember that we used it to drive external LEDs._
2. Fire up the standalone Rigol function generator. It is right beneath the multimeter. Connect a probe. _Notice that the function generator probes also have two wires._ Connect it properly to the oscilloscope probe. Repeat the previous task with this new source.
 3. Write a one-line micro:bit program to set an analog pin to emit PWM pulses. Which pin function will you use? Capture the signal. _PWM stands for [Pulse Width Modulation](https://en.wikipedia.org/wiki/Pulse-width_modulation) and is a method to control servo motors. PWM is based on a square wave signal where the pulses (that is, the sections where the signal is *_*high**) vary in width. The servo motor decodes the signal (essentially comparing the width of the pulse to the period of the square wave) and rotates the shaft accordingly._
 4. To repeat the task from (1), you need a loop for your program in (3). Write a loop that varies the duty cycle, up and down, between 5% and 95%, in steps of 5%. _Note: Here, you need to read on the oscilloscope what the period of the base wave is, to calculate the duty cycles. Include the period and the pulse widths for the highest and lowest duty cycle in your short writeup._

READ.ME = Explore the _other_ servo function, using the oscilloscope. Once you figure it out, write a small program to demo the operation, and record the video. _You might or might not need to use the **Single** mode of the oscilloscope._
   
### I2C warmup:
 Read the SparkFun [I2C tutorial](https://learn.sparkfun.com/tutorials/i2c).
 
 READ.ME-  1. In a small writeup in the [README](README.md), answer the following questions:
 
  1. What are the disadvantages of the other two serial communication channels, UART and SPI, and how does I2C improve on them?
  2. I2C is a two-wire serial communication channel. What are the two wires, SDA and SCL?
  3. What distinguishes the _master_ and the _slaves_?
  4. How are the two types of protocol _frames_ different?
  5. What is the most appropriate _trigger_ for capturing an I2C frame on the oscilloscope?
  6. (Advanced) If the micro:bit is configured by default as a _master_, and two micro:bits, connected to each other via the SDA and SCL lines, communicate over I2C? (**Bonus** for a convincing argument, one way or another.)
 

### First steps with I2C:

  1. In a loop, configure the micro:bit to write a number to some arbitrary I2C address. The address can be arbitrary. Capture an I2C frame on the oscilloscope. _Note that I2C has 2 wires, so you will need 2 probes, and set the correct trigger on the correct channel._ Use the **Single** mode on the oscillocope. Take a picture of your setup and a picture of the oscilloscope display. 

Write a short program to read a number from the I2C devices on the micro:bit. For each device:
      1. Try all three addresses. (**Bonus** for a cogent argument about why there are three.)
      2. Try signed and unsigned single bype integers.
      3. Scroll the values on the LED matrix. 
      4. What values do you read?
      5. Can you get different values by moving the micro:bit around.
      
 READ.ME- In the writeup, analyze what you have captured:
      1. What frame did you capture?
      2. What does the I2C write function do when there is nothing connected?
      3. Is there a difference in what you capture if you write a number to one of the internal device addresses? _(The accelerometer and magentometer (compass) are connected to the I2C bus on the micro:bit PCB. Their addresses can be found [here]
      
  

   
### S5. (Advanced, optional, and bonus) Simple pulse-based protocol:
   1. Program one micro:bit to emit pulse-based patterns by driving a digital output pin. Use a 50% duty cycle. Start with the 11111 pattern.
   2. Program another micro:bit to detect the pattern by listening on an digital input pin. Play with the `bits.onPulsed()` and `bits.pulseDuration()` functions.
   3. Generate and capture all 5-bit patterns. _How will you deal with the patterns that start with the same value as your protocol line (that is, if your line is high by default, how will you deal with patterns that start with 1, and if you line is low by default, how will you deal with patterns that start with 0)?_ Devise a demo that shows this capability on a video. You may use the LED matrix to show the sent and received patterns, for comparison.
