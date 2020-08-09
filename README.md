Construction of hardware:

This project uses two different hardware combined to form metal detector namely Colpitts Oscillator and Speaker.
To create Colpitts oscillator we require one resistor of value between 100 ohms to 1000 ohms, two capacitors C1 in range 1nF to 10nF and C2 in range 10nF to 100nF, one inductor coil, and two MOSFETS one of p-type and other n-type.
Colpitts oscillator requires a NOT gate which is created by using one n-type and one p-type MOSFET. The source of the p-type MOSFET is connected to the 5V whereas the source of n-type MOSFET is connected to the ground and the drain and gate of two MOSFETS are connected to each other. 
The input to the NOT gate is applied at the gate of the MOSFETS and the output of the NOT gate is given at the drain of the MOSFET.
The input of NOT gate is connected to 1000 ohms resistor whose other end is connected to one end of the inductor coil and capacitor C1 which is grounded. The output of the NOT gate is connected to the other end of inductor coil and capacitor C2 which is grounded.
To create sound module we use CEM-1302 speaker, one 330 ohms resistor, one PNP transistor (2N3906), and one 1N4148 diode.
The diode is connected to speaker whose one end is connected to 5V supply and other end is connected to emmiter of the transistor whose collector is grounded and base is connected to 330 ohms resistor which goes to pin 0.1 of EFM8 board.
                                                                                   
Construction/Compilation of Software:

The purpose of the software in metal detector is to detect the change in frequecy of the circuit when the coin is brought near it and produce the PWM to drive the speaker.
We enable pin 0.0 on EFM8 to take as an input of frequency and using timer 0 we detect the frequency. The next step is to detect the natural frequency of the circuit wich is done by detecting frequency in absence of any metal near the circuit and reading it from putty.
Once we get the natural frequency we use if else statement to identify presence of any metal near it because if any metal is present then the frequency of the inductor will change, when this change is detected a PWM is produce using timer 2 at the pin 0.1 of EFM8 which causes speaker to beep. 

Operation:
 
The Colpitts oscillator works by comparing change in frequency produce when the metal is placed close to it. To do so we first measure the natural frequency of the oscillator.
Once we get the natural frequency we bring the metal close to the inductor which changes the magnetic field and hence magnetic flux around the coil which is reflected by slight change in the inductance of coil which results in change in frequency. 
Since we are require to detect the coin from about 1cm so when the frequency crosses certain frequency mark a rectangular pulse is generated at pin 0.1 of EFM8 board which makes speaker beep. 

Bonus:
Bonus feature of this project is that it detects which coin it is that means it identifies whether the coin is 1 dollar, 2 dollar, 50 cents, etc.
Since every particular value coin has different size, shape or material it produces change in magnetic fied of inductor to different extent and hence the change in frequency will be unique to each coin given other parameters remains constant.
So to do this we first measure the frequency produce by each coin when it is very close to the inductor (this is important because 1 cm distance from inductor without any measurement has error and deviation in freuency can be more but if the coin is closer to inductor it gives stable readings) then we use if else structure in our program to identify the value of coin. 
