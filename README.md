# Final-Presentation

# **Introduction**
For this project we chose to create a robot that can tell you how far an object is using a sensor. If the object is far away, it turns on a green light. If the object is closer, it turns on a yellow light. If the object is very close, it turns on a red light. We also added a buzzer. The buzzer makes slow beeps when the object is far. The beeps get faster when the object comes close. We used a Raspberry Pi, wires, and LEDs to build the robot. We also wrote code to make everything work.

To begin with, I am going to tell you about Raspberry Pi.

# **What is Raspberry Pi?**
The Raspberry Pi is a low-cost computer with a compact size, about the size of a credit card, that can be connected to a computer monitor or a TV, and used with a standard mouse and keyboard. It is a small computer that runs a Linux operating system capable of allowing people of all ages to explore computing and learn to program languages like Scratch and Python. It is capable of performing most typical tasks of a desktop computer, from browsing the internet, playing high-resolution videos, handling office documents, to playing games. Additionally, the Raspberry Pi has the ability to interact with the outside world, and it can be used in a wide variety of digital projects, from music and video players, parent detectors, weather stations to bird boxes with infrared cameras. We want you to see that the Raspberry Pi can be used by children and adults all over the world to learn programming and understand how computers work.

# **How is Raspberry Pi composed?**
![image](https://github.com/user-attachments/assets/2b5145bd-ae07-45bf-b485-39fde766e4a5)

**GPIO pins:** One of the most alien features of a Raspberry Pi are the 40 shiny metal pins found on the top edge of the board. These are called GPIO pins, which stands for General-Purpose Input/Output. You can program these pins to control a huge variety of electronics, components, and other parts including LEDs, sensors, and motors. 

**MicroSD card slot:** While most computers have some form of built-in storage your laptop often has a hard drive, for example a Raspberry Pi has no "onboard" storage.Instead, the software your computer runs on, known as the operating system (OS), and all of your files are stored on a microSD card, much like you might find in a digital camera. 

**USB ports:** There are four USB ports you can use to plug in USB keyboards, mice, USB sticks, and other devices. 

**USB-C Power Supply:** The USB-C power supply gives the device power. A USB-C cable can have a wall plug on the other end of it. Ensure that the output voltage of the charger is 5 volts and the input current is at least 2.5 volts.

 **HDMI port:** Stands for High-Definition Multimedia Interface, and this port is what you'll use to connect your Pi to a screen like a TV or a computer monitor. 

**Camera connector:** Is clip-like connector labeled camera. It's the input for the official Raspberry Pi Camera Module. 

**3.5mm Audio Jack:** Allows for connecting audio jack connectors for sound output. 

**Micro USB power jack:** This is where you'll plug in the 5 V of power that every Raspberry Pi requires to work; this is the same sort of power input as many mobile phones. It's also worth noting that there is no power button! Your Pi will be on for as long as you keep the power cable connected.

 **Ethernet network port:** This is for a wired internet connection. 

**Quad-Core 1.4GHz processor:** In the middle of your Pi you'll see the brain of your computer. You may be wondering just how powerful your new purchase is: is it as fast as a laptop or a desktop computer? The processor, coupled with the Pis 1GB of RAM, gives the Raspberry Pi power that's roughly equivalent to some smartphones. 

**RAM:** Random Access Memory (RAM) is temporary storage for the device. It holds active data so the computer can store and expel it.

# Physical Part
![734D7FBE-9BE4-48A6-B394-EC5ACC592B7C](https://github.com/user-attachments/assets/31a518be-89ff-4e87-8daf-3fc5ac0008b6)
![image](https://github.com/user-attachments/assets/84a3f2d7-0188-497a-a08d-fa9b46fec984)
![image](https://github.com/user-attachments/assets/f316fc9c-5f17-475e-ac2e-2f72477624fc)



# **Programming Part**
“Hey everyone! Today, I’ll walk you through this Python code written for a Raspberry Pi. It uses an ultrasonic sensor to measure distance, and based on how close something is, it lights up different LEDs and controls a buzzer for audio alerts. Let's break the code down step by step.”

# **Importing Libraries**
![image](https://github.com/user-attachments/assets/e664106e-dd1a-4ca1-814d-582243c74cbb)

“We start by importing two libraries. RPi.GPIO lets us control the Pi’s pins, and time is used for delays and timing how long the sound pulse takes to travel — which helps us calculate distance.”

# Pin Assignments
![image](https://github.com/user-attachments/assets/1a075955-7acc-49eb-ba52-dc9ffb5762a8)

“Next, we assign GPIO pins for each component.

TRIG and ECHO are for the ultrasonic sensor.

Then we have three LEDs: green, yellow, and red — for far, warning, and danger levels.

Finally, we assign the buzzer to a pin.”

# GPIO Setup
![image](https://github.com/user-attachments/assets/cc58528f-c972-4cfd-9784-477cf9385cf6)

“Here, we set the GPIO mode to BOARD, which means we refer to the physical pin numbers on the Pi. Then we configure each pin as either an input or output depending on whether it sends or receives signals.”

# Distance Measurement Function
![image](https://github.com/user-attachments/assets/18edcf21-94cd-43fb-96d9-60b571e248fa)

“This function is the heart of the program — it measures how far away an object is using sound.
Here’s what it does:
It sends a very short signal — just 10 microseconds — from the TRIG pin.

Then it waits for the echo to come back on the ECHO pin.

It measures how long the signal took to go out and return.

Using the speed of sound, it calculates the distance.

Let’s say the echo takes 0.002 seconds — that gives us a distance of about 34.3 cm.”

# Handling Errors in Measurement
![image](https://github.com/user-attachments/assets/e8404b94-e6d0-4f45-ac8c-069bea1314b0)

“We use a timeout to avoid getting stuck if no signal comes back — maybe there’s nothing in front of the sensor. If it takes too long, we return -1 to skip that reading.”

# Buzzer Function
![image](https://github.com/user-attachments/assets/e902b450-4462-4ffa-8efe-67a4f250af1d)

“This function controls the buzzer. It turns it on for a short beep — 0.05 seconds — then waits for a delay. The delay changes based on how close the object is. So the closer something is, the faster the beeps.”

# Main Loop Begins
![image](https://github.com/user-attachments/assets/a3fe8883-c1f3-4cd8-b2c5-87bdf998263b)

“Here’s where the program runs in a loop — forever checking how far an object is.”

# Reset All LEDs
![image](https://github.com/user-attachments/assets/37585b2c-c88e-4143-8047-4bb4118edbf8)

“Before checking the distance, it turns off all the LEDs to reset the state.”


# Distance Conditions and Actions
![image](https://github.com/user-attachments/assets/ae5655e4-3b9f-4c77-8689-4003d05f59d3)

“If something is more than 22 cm away, the green LED turns on and the buzzer beeps slowly, once every second.”

“If it’s between 12 and 22 cm — like a hand getting closer — the yellow LED lights up and the buzzer beeps faster.”

“If it’s under 12 cm — really close — the red LED lights up and the buzzer beeps rapidly to give a clear warning.”

# Skip if Measurement
![image](https://github.com/user-attachments/assets/eb12d94f-46aa-4504-932b-13ce598d1772)

“If the distance reading failed, maybe because of an object being too far or nothing in front, we skip that loop and try again.”

# Cleanup on Exit
![image](https://github.com/user-attachments/assets/f1a4fca4-ca94-4e50-9bdb-21bfd6fda7b3)

“Finally, if we stop the program by pressing Ctrl+C, the GPIO.cleanup() function turns everything off safely so we don’t leave pins active.”

# References

What is a Raspberry Pi? Raspberry Pi. (2025, March 18).[ [https://raspberrypi.cl/que-es-raspberry/](url)](url)

Timmons-Brown, M. (2019a). Learn robotics with Raspberry Pi: Build and code your own moving, sensing, thinking Robots. No Starch Press, Inc. 























