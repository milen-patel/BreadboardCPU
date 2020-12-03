# 8-Bit Computer
In my computer organization class, we learned about an incredibly basic computer model: SAP-1 (Simple as Possible). Ben Eater and others have successfully ventured out to build this computer on a breadboard, and I wanted to build it on my own too. I began this project in September of 2020 by building the clock. However, the rest of the computer was mostly built during November. I would say that this build took me atleast 60 hours in total.

![](sap-counting-down.gif)


## The Build
The first part of the project was to build a clock that will eventually be used to synchronize the rest of the components. The clock has two modes. The first is a manual mode where clock cycles are driven by the use of a manual push-button, and the second mode is an automatic clock whose frequency can be controlled with a potentiometer.

Each of the two clock modes is implemented using a 555 timer chip. In the push button case, the 555 is used solely for debouncing the push button. 

Additionally, there is a switch that is used to toggle between the clock modes. Similarly, the toggle is implemented using yet another 555 for debouncing. Lastly, there are some logic chips on the right side of the breadboard that implement the selector between the two modes using the debounced switch as a selector. Additionally, we provide the ability to halt the clock by taking the final output of the clock, feeding it into an AND gate and using the (inverted) halt control as the other input. This will come to be useful in the future when we need the program to halt the clock. We will take the final output of that AND gate to be the value of the clock at any given time.

It goes without saying that this computer is very limited in its functionality. However, it does have the ability to add and subtract numbers, so the ALU (Arithmetic Logic Unit) is implemented to do just that! We start off building two 8-bit registers (A and B respectively) that serve as the two operands to the ALU. 

We chain together two 74LS283's to create an ALU that can add the values stored in the A and B registers. To implement subtraction, we use XOR gates for each of the B input bits with the subtraction flag. The ALU was the messiest part of the build as there were many connections involved in feeding inputs to the ALU, chaining together ICs, and supporting subtraction. After reading around online, it became clear that many people were having issues getting their ALUs to work, and it almost always boiled down to misplacing a wire. I was fortunate enough to not run into any of those issues, so I would reccomend building the ALU as slowly and carefully as possible since debugging can be quite difficult.

Once the ALU was done, the next step was building a RAM module. The SAP has a memory address register which used a 4 bit value used to store the address of the current location in memory. The value of the registers contents were directly wired into the RAM, so the only way to use memory was to change the value of the memory address register. By default, the memory address register reads in values from the bus; however, we created a second mode where we could manually select addresses using a DIP switch. This is essential for loading our programs into memory.

After the RAM was done, a 4-bit program counter was created that could incremenet, put its value onto the bus, or read in a value from the bus. The program counter was used to fetch the current instruction from memory.

The last new componenet of the build was the output module. The output module used an 8-bit register to store the current value to be displayed, and the value of the register is designed to always be displayed on the four 7-segment displays. To implement this, we used an EEPROM to translate our 8 bit values into the appropriate values to display on each 7-segment display. On my build, I added a switch that toggles whether the output module treats the 8-bit value as an unsigned integer or in two's complement.

The final part of the build was creating the control logic for link all of the components together. Two EEPROMs were used to implement the control logic, and this is the part where my build got a bit messy as wires had to be placed all across the computer to set the appropriate control lines.
