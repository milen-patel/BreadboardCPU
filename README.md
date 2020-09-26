# 8-Bit Computer
In my computer organization class, we learned about an incredibly basic computer model: SAP (Simple as Possible). Ben Eater and others have successfully ventured out to build this computer on a breadboard, and I wanted to build it on my own too.

I am using Ben Eater's tutorial series online, with deviations to come as problems arise.

## Part 1: The Clock
The first part of the project was to build a clock that will eventually be used to synchronize the rest of the components. The clock has two modes. The first is a manual mode where clock cycles are driven by the use of a manual push-button, and the second mode is an automatic clock whose frequency can be controlled with a potentiometer.

Each of the two clock modes is implemented using a 555 timer chip. In the push button case, the 555 is used solely for debouncing the push button. 

Additionally, there is a switch that is used to toggle between the clock modes. Similarly, the toggle is implemented using yet another 555 for debouncing. Lastly, there are some logic chips on the right side of the breadboard that implement the selector between the two modes using the debounced switch as a selector. Additionally, we provide the ability to halt the clock by taking the final output of the clock, feeding it into an AND gate and using the (inverted) halt control as the other input. This will come to be useful in the future when we need the program to halt the clock. We will take the final output of that AND gate to be the value of the clock at any given time.

