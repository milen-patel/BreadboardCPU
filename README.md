# 8-Bit Computer
In my computer organization class, we learned about an incredibly basic computer model: SAP (Simple as Possible). Ben Eater and others have successfully ventured out to build this computer on a breadboard, and I wanted to build it on my own too.

I am using Ben Eater's tutorial series online, with deviations to come as problems arise.

## Part 1: The Clock
The first part of the project was to build a clock that will eventually be used to synchronize the rest of the components. The clock has two modes. The first is a manual mode where clock cycles are driven by the use of a manual push-button, and the second mode is an automatic clock whose frequency can be controlled with a potentiometer.

Each of the two clock modes is implemented using a 555 timer chip. In the push button case, the 555 is used solely for debouncing the push button. 

Additionally, there is a switch that is used to toggle between the clock modes. Similarly, the toggle is implemented using yet another 555 for debouncing. Lastly, there are some logic chips on the right side of the breadboard that implement the selector between the two modes using the debounced switch as a selector. Additionally, we provide the ability to halt the clock by taking the final output of the clock, feeding it into an AND gate and using the (inverted) halt control as the other input. This will come to be useful in the future when we need the program to halt the clock. We will take the final output of that AND gate to be the value of the clock at any given time.

![](clock.gif)

## Part 2: The Arithmetic Logic Unit (ALU)
It goes without saying that this computer is very limited in its functionality. However, it does have the ability to add and subtract numbers, so the ALU is implemented to do just that! We start off building two 8-bit registers (A and B respectively) that serve as the two operands to the ALU. 

We chain together two 74LS283's to create an ALU that can add the values stored in the A and B registers. To implement subtraction, we use XOR gates for each of the B input bits with the subtraction flag. The ALU was the messiest part of the build as there were many connection involved in feeding inputs to the ALU, chaining together ICs, and supporting subtraction. After reading around online, it became clear that many people were having issues getting their ALUs to work, and it almost always boiled down to misplacing a wire. I was fortunate enough to not run into any of those issues, so I would reccomend building the ALU as slowly and carefully as possible since debugging can be quite difficult.

Below is a quick demonstration of the ALU repeatedly operating at a high clock speed.

![](alu.gif)

## Part 3A: Ram Setup
Now that we have a functioning ALU, the next step is to build a RAM module so we can load and store relevant IO from the ALU.
## Part 3B: Ram Memory Address Selector
## Part 3C: RAM Value Selector
## Part 4: Program Counter
![](program-counter.gif)
## Part 5: Making an EEPROM Programmer
## Part 6: Output Display
